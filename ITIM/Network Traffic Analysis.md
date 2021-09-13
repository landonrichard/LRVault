# Network Traffic Analysis
#NCL
---
## Capturing and Understanding Basic Packets
#KaliTools 

To capture and analyze packets you can use a program called wireshark. To get more details on specific packets follow the stream.

>Screenshot of Wireshark
>![Wireshark Screenshot](wireshark.jpg)

**Further Reading**
- [Wireshark](https://www.wireshark.org/)
- [Wireshark Help](https://www.wireshark.org/docs/wsug_html_chunked/)
- [Wireshark Crash Course](https://www.youtube.com/watch?v=lb1Dw0elw0Q)

---
## Understanding Network Traffic using Non-Standard Protocols (Pandora)
#KaliTools 

To capture and analyze packets you can use a program called wireshark. To get more details on specific packets follow the stream.

>Cyber Skyline Overview
>The communication between the client and server will contain three types of messages: Initialization, Hash Request, and Hash Response. A connection is started with the client sending an Initialization message, which contains the number of Hash Requests that the client wishes to make. Then, the server will send the length of its response. Then, the client sends their Hash Requests to the server. After all of the Hash Requests have been received, the server will finish sending a single Hash Response which contains hashes of all of the data that was sent by the client.
>Initialization (Client -> Server) 
>1.N - A 4-byte integer in network byte order that represents the number of Hash Requests that will be sent. 
>
>Hash Request (Client -> Server) 
>1.Check - A fixed 2-byte integer in network byte order that verifies the integrity of the message.
> 2.Len - A 4-byte integer in network byte order that represents the length of the data in bytes. 
> 3.Data - The data that will be hashed. 
> 
>Hash Response (Server -> Client) 
>1.Count - The length of the data, in bytes, that follows. 
>2.Hashes - The hashes requested by the client. Each hash is in the form of a fixed-length chunk. These hashes are in the same order that the requests were made.

You can filter packet capture to just the custom protocols. If the packet capture contains both SSH and HTTP traffic you could remove the noise by filtering by `tcp && !(tcp.port == 22) && !(tcp.port == 80)`. Now the first packet should show the client establishing a connection with the server.

You can find the magic 2-byte id by following the TCP stream for the first filtered packet and exporting it as a **hex dump**. The first 4 bytes represents the number of requests and the next 2 bytes are the 2-byte magic number check.

To find out how many encrypt requests were made by the client we have to assume some values for the sake of this example. If the first request has a length of 0x58 (88 in decimal) and the second request has a length of 0x48 (72 in decimal). (You should be able to find the second request by the second instance of 0x0417.) 

The hash length can be found by taking the number of requests and dividing it by the length of the response of the server (0xa0 or 160 decimal). 

The result of this is 32 bytes with the given values. This means the first 32 bytes are the first hash and the second 32 bytes being the second hash.

Any of the hash requests can be decoded using **base64**.