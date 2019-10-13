---
layout: post
title: PicoCTF 2019 - extensions
categories: [PicoCTF, Forensics]
tags: [Easy, Forensics, Files]
---

# *extensions*

## Information

| Points |Category  | Level|
|--|--|--|
| 150 | Forensics  |Easy |

## Challenge

> This is a really weird text file [TXT](https://2019shell1.picoctf.com/static/45886ed4b6d5d1dc74c4944fcf4b4041/flag.txt)? Can you find the flag?
 
### Hint

> How do operating systems know what kind of file it is? (It's not just the ending!Make sure to submit the flag as picoCTF{XXXXX}

## Solution

I download the file, and opened it -
![The file](https://i.imgur.com/iNWM9v8.png)

There is nothing I can see in this junk, tried to Ctrl+F and search pico format flag but still nothing.
but as we can see, at the first line we can see PNG, so maybe it's just an image? (It's called the header of the file for [more reading](https://en.wikipedia.org/wiki/File_format#File_header))
In order to open the file as image, we need to rename the file extention, 
and now we can open the file as an image -
![The flag](https://i.imgur.com/xk0lCDd.png)


## Flag
> `picoCTF{now_you_know_about_extensions}`
