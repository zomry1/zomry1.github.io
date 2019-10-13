---
layout: post
title: PicoCTF 2019 - strings it
categories: [PicoCTF, General Skills]
tags: [Easy, General Skills]
---

# *strings it*

## Information

| Points |Category  | Level|
|--|--|--|
| 100 |General Skills  |Easy |

## Challenge

> Can you find the flag in [file](https://2019shell1.picoctf.com/static/d97e691ff0842819be9dfcb767c074d9/strings) without running it? You can also find the file in /problems/strings-it_0_b76c77672f6285e3a39c188481cdff99 on the shell server.
> 
### Hint

> [strings](https://linux.die.net/man/1/strings)

## Solution

First of all, we want to make "strings" file readable, so let's use the strings command
> open terminal -> move to the folder of the file (by cd) -*> strings strings > output.txt

* **strings** - the strings command cast binary/executable file to human-readable string.
	* command syntax:
		>   strings FILENAME
		
added **> output.txt** to save the results of the command in output.txt file.
now, we can open the output.txt file and see a lot of garbage, let's do the same trick we did in
grep 1(add link).

    open terminal -> move to the folder of the file (by cd) -*> grep "picoCTF" file

## Flag
> `picoCTF{5tRIng5_1T_f1527258}`
