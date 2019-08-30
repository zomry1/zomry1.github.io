---
layout: post
title: PicoCTF 2018 - hex editor
categories: [PicoCTF, Forenscis]
tags: [Easy, Forensics, Hex Editor, image]
---

## Information

| Points |Category  | Level|
|--|--|--|
| 150 | Forensics |Easy |

## Challenge

>This [cat](https://2018shell.picoctf.com/static/8bf13e0b1ce613af3b79223abb8f8d6d/hex_editor.jpg) has a secret to teach you. You can also find the file in /problems/hex-editor_2_c1a99aee8d919f6e42697662d798f0ff on the shell server.

### Hint

>-   What is a hex editor?
>-   Maybe google knows.
>-   [xxd](http://linuxcommand.org/man_pages/xxd1.html)
>-   [hexedit](http://linuxcommand.org/man_pages/hexedit1.html)
>-   [bvi](http://manpages.ubuntu.com/manpages/natty/man1/bvi.1.html)

## Solution

We have a image file, but the name of the challenge is hex editor, so it's obvious that we need to open the file with hex editor and find the flag. One nice option is use the "strings" command that search for printable text in a file and print it.

    strings hex_editor.jpg

![Strings](https://i.imgur.com/CNdpt4A.png)
But it will output a lot of junk that there is in the image so let's add a filter with grep, pipe the output of the strings to grep that search for some part of the flag that always in the flag like "picoCTF"

    strings hex_editor.jpg | grep picoCTF 

And we found the flag!
![The flag](https://i.imgur.com/0ncbVEF.png)

## Flag
> `picoCTF{and_thats_how_u_edit_hex_kittos_22C1d865}`
