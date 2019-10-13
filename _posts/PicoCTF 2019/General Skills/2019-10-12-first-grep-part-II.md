---
layout: post
title: PicoCTF 2019 - First Grep Part II
categories: [PicoCTF, General Skills]
tags: [Easy, General Skills]
---

# *First Grep: Part II*

## Information

| Points |Category  | Level|
|--|--|--|
| 200 |General Skills  |Easy |

## Challenge

> Can you find the flag in /problems/first-grep--part-ii_0_b68f6a4e9cb3a7aad4090dea9dd80ce1/files on the shell server? Remember to use grep.

Submit!

### Hint

> grep [tutorial](https://ryanstutorials.net/linuxtutorial/grep.php)
> 
## Solution

To get the file we need to use the shell of the site so open this [url](https://2019game.picoctf.com/shell)
In order to connect you need to enter your username and password.
No to get the problem folder we need to go back 2 folders and then enter the problem folder so write:

    cd ..
    cd ..
    cd /problems/first-grep--part-ii_0_b68f6a4e9cb3a7aad4090dea9dd80ce1/files

Now us ls to see what in the directory:

`ls`

So there are many directory in it, and many more in it's and on and on and on...
We really need to do grep in each folder?

There is an easy way to do grep search in recursive way (that way we will search in each inner folder).

The way to do that, it's only include the -r flag in the grep command so let's write:

    grep -r 'picoCTF{'
   
   And we got this:

>    files9/file26:picoCTF{grep_r_to_find_this_e4fa3ba7}

We found the flag and it's in the files26 that in the files9 folder

## Flag
> `picoCTF{grep_r_to_find_this_e4fa3ba7}`
