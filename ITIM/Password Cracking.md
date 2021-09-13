# Password Cracking
#NCL
---
## Cracking MD5 Password with a Wordlist
#KaliTools 

To crack an MD5 password with a wordlist you can use a program called Hashcat. You will be using a dictionary attack. There are different wordlists you can use. Default wordlists that come with Kali can be found at `/usr/share/wordlists/`. 

>Example of a dictionary attack against the RockYou wordlist
>`hashcat pass.txt -m 0 -a 0 pass.txt /usr/share/wordlists/rockyou.txt`

**Further Reading**
- [Hashcat](https://hashcat.net/wiki/doku.php?id=hashcat)
- [Wordlists 1](https://github.com/jeanphorn/wordlist)
- [Wordlists 2](https://www.darknet.org.uk/2008/02/password-cracking-wordlists-and-tools-for-brute-forcing/)

---
## Cracking MD5 Passwords with a Mask
#KaliTools 

To crack an MD5 password using a mask you can use a program called Hashcat. You will be using a brute force attack.

**Charsets**

| Syntax      | Characters |
| ----------- | ----------- |
| ?l      | abcdefghijklmnopqrstuvwxyz       |
| ?u      | ABCDEFGHIJKLMNOPQRSTUVWXYZ       |
| ?d      | 0123456789       |
| ?h      | 0123456789abcdef       |
| ?H      | 0123456789ABCDEF       |
| ?a      | ?l?u?d?s       |
| ?b      | 0x00 - 0xff       |

>Exmaple of mask attack using hashcat and 0-9 charset to find a flag matching FLAG-LKR-1998
>`hashcat -m 0 -a 3 pass.txt 'FLAG-LKR-?d?d?d?d'` (with initials)
> `hashcat -m 0 -a 3 pass.txt "FLAG-?u?u?u-?d?d?d?d"` (without initials)

**Further Reading**
-[Hashcat Mask Attacks](https://hashcat.net/wiki/doku.php?id=mask_attack)

---
## Cracking MD5 Passwords with a Wordlist and Mask
#KaliTools 

To crack an MD5 password using a wordlist and mask you can use a program called Hashcat. You will be using a hybrid attack. There are different wordlists you can use. Default wordlists that come with Kali can be found at `/usr/share/wordlists/`. 

**Charsets**

| Syntax      | Characters |
| ----------- | ----------- |
| ?l      | abcdefghijklmnopqrstuvwxyz       |
| ?u      | ABCDEFGHIJKLMNOPQRSTUVWXYZ       |
| ?d      | 0123456789       |
| ?h      | 0123456789abcdef       |
| ?H      | 0123456789ABCDEF       |
| ?a      | ?l?u?d?s       |
| ?b      | 0x00 - 0xff       |

>Exmaple of a hybrid wordlist and mask attack using hashcat and 0-9 charset to find a flag with a password from the list plus 3 digits afterwords.
>`hashcat -m 0 -a 6 hash.txt wordlist.txt ?d?d`

**Further Reading**
-[Hashcat Mask Attacks](https://hashcat.net/wiki/doku.php?id=mask_attack)

---

## Cracking NTLM Passwords with Ophcrack
#KaliTools 

You can crack Windows XP, Windows Vista, and Windows 7 passwords with Ophcrack using rainbow tables. Make a PWDUMP file with all of the hashes or load each hash one by one into Ophcrack. 

>Screenshot of Ophcrack
>![Ophcrack Screenshot](OphcrackSS.png)

>**Example of an NTLM password**
>21259dd63b980471aad3b435b51404ee:1e43e37b818ab5edb066eb58ccdc1823

**Downloads**
-[Ophcrack](https://ophcrack.sourceforge.io/download.php?type=ophcrack)
-[Rainbow Tables](https://ophcrack.sourceforge.io/tables.php)
