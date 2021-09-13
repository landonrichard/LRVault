# Scanning
#NCL
---
## Port Scans with Nmap
#KaliTools 

To scan ports you can use a tool called Nmap. With Nmap you will need to be familiar with certain command line flags to specify the scan.

| Flags      | Action |
| ----------- | ----------- |
| -p      | Specify port       |
| -Pn      | Disable host discovery       |
| -sL      | List scan       |
| -sS      | TCP SYN scan       |
| -sT      | TCP connect scan       |
| -sU      | UDP scan       |
| -sV      | Determine software version       |
| -sY      | SCTP INIT scan       |
| -sN      | TCP NULL       |

>Screenshot of Nmap
>![Aircrack-ng Summary Screenshot](nmap.png)

**Further Reading**
- [Nmap](https://nmap.org/)
- [Nmap Guide](https://www.varonis.com/blog/nmap-commands/)

---
## Directory Scanning on an HTTP Server
#KaliTools 

To brute force directories and filenames on a web server you can use a tool called DirBuster. You will need to know the target URL and have a wordlist. There are several DirBuster wordlists you can use. Several wordlists come with DirBuster but if you need them they can be found here [DirBuster Lists](https://github.com/daviddias/node-dirbuster/tree/master/lists).

>Open DirBuster
>
>In Target URL field enter the URL you want to crawl
>
>Check the Go Faster toggle
>
>Select List based brute force and browse for the wordlist
>
>Select Brute Force Dirs and Brute Force Files
>
>Toggle Be Recursive to check within found folder

>Dirbuster Screenshot
>![Dirbuster Screenshot](dirbuster.png)

**Further Reading**
- [DirBuster](https://tools.kali.org/web-applications/dirbuster)
- [DirBuster Manual](https://null-byte.wonderhowto.com/how-to/hack-like-pro-find-directories-websites-using-dirbuster-0157593/)
- [DirBuster Quick Video](https://www.youtube.com/watch?v=--nu9Jq07gA)