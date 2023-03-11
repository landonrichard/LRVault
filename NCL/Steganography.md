# Steganography
#NCL
---
## Data Hidden in Raw Binary
#KaliTools 
#WebTools 

An image can be altered to embed small hidden flags in the raw binary of a file.

To search through the file and find the flag you can use the "strings" command and grep for known characters in the flag.

>Example
> `strings FileName.jpg | grep FLAG`


**Further Reading**
- [GREP](https://man7.org/linux/man-pages/man1/grep.1.html)
- [Strings](https://linux.die.net/man/1/strings)

---
## Files Hidden in the Image
#KaliTools 

Files of any type can be hidden in an image. [^1]

To try and find these files within the image you can use a tool called DIIT (Digital Invisible Ink Toolkit). You can choose different algorithms to use if the first one doesn't work.

[^1]: Given the file is small enough and fits within the colorspace of the image.

>Screenshot
>![D.I.I.T.](DIITScreenshot.png)

**Tools**
-[DIIT](http://diit.sourceforge.net/)
-[Binwalk](https://github.com/ReFirmLabs/binwalk)

## Finding MD5 Sum of a File
#KaliTools 

**MD5 Sum**
': a commonly used function for validating data integrity.'

To check the MD5 Sum of a file, you can use the "md5sum" command.

>Example
>`md5sum FileName.png`