---
layout: post
title: PicoCTF 2018 - Truly an Artist
categories: [PicoCTF, Forenscis]
tags: [Easy, Forensics, image]
---

## Information

| Points |Category  | Level|
|--|--|--|
| 200 | Forensics |Easy |

## Challenge

>Can you help us find the flag in this [Meta-Material](https://2018shell.picoctf.com/static/9b8863e30054675ce78328df28c601db/2018.png)? You can also find the file in /problems/truly-an-artist_4_cdd9e325cf9bacd265b98a7fe336e840.

### Hint

> -   Try looking beyond the image.
>-   Who created this?

## Solution

I tried to put the image in some online tools and etc and I didnt fount anything, later I tried to figure out what those numbers in the image says and again didn't found anything. So I read again the challenge and then it's hit me.
![Hit Me](https://i.imgur.com/KoCapGi.png)

The link to download the file called "**Meta**-Material", as you know each file as a metadata on him that save information like, date of creation, last modification and etc.
There is a nice tool to extract this data from a file called "exiftool"

    apt-get install exiftool

For installing the program.
Now go with the terminal for the file location and write

    exiftool 2018.png

There is some information about this file, and hi! here is the flag!
![The flag](https://i.imgur.com/jb2gg17.png)

## Flag
> `picoCTF{look_in_image_13509d38} `
