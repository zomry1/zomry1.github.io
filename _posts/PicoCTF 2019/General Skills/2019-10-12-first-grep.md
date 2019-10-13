---
layout: post
title: PicoCTF 2019 - First Grep
categories: [PicoCTF, General Skills]
tags: [Easy, General Skills]
---

# *First Grep*

## Information

| Points |Category  | Level|
|--|--|--|
| 100 |General Skills  |Easy |

## Challenge

> Can you find the flag in [file](https://2019shell1.picoctf.com/static/458ae91cb23746189bf490f0c8d9a919/file)? This would be really tedious to look through manually, something tells me there is a better way. You can also find the file in /problems/first-grep_2_04dbf496b78e6c37c0097cdfef734d88 on the shell server.

### Hint

> grep [tutorial](https://ryanstutorials.net/linuxtutorial/grep.php)

## Solution

Let's download the file, it's full in garbage.
The name of the challenge is grep so let's use it.
> open terminal -> move to the folder of the file (by cd) -*> grep "picoCTF" file

 
* grep - the grep command search a pattern in the text 
	* command syntax:
		>   grep "PATTERN" FILENAME

## Flag
> `picoCTF{61}`
