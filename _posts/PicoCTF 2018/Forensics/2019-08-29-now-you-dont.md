---
layout: post
title: PicoCTF 2018 - now you don't
categories: [PicoCTF, Forenscis]
tags: [Easy, Forensics, image]
---

## Information

| Points |Category  | Level|
|--|--|--|
| 150 | Forensics |Easy |

## Challenge

>We heard that there is something hidden in this [picture](https://2018shell.picoctf.com/static/eee00c8559a93bfde1241d5e00c2df37/nowYouDont.png). Can you find it?

### Hint

> -   There is an old saying: if you want to hide the treasure, put it in plain sight. Then no one will see it.
>-   Is it really all one shade of red?

## Solution

Again I started with trying the basic online stuff and some programs (like binwalk and etc), but nothing came up.

We can see that this image is not only black and it's not some photo, it's only red background, so I thought that this challenge I really need to use tools on the image, and not on the data.
I read the hints and got it, like the LSB decoder we saw earlier [Add kink to Reading Between the Eyes] there is a chance that there is a little change in the red shade that the naked eye can't see, that probablly made by modifiction of the image, we can try to check those modifiction with error level analyzer like the one in this [site](https://29a.ch/photo-forensics/#forensic-magnifier)
![error level analyze](https://i.imgur.com/SqPLNER.png)

We imedaitlly can see that there is somthing in the image, let's set the jpeg quality to 100 and the error scale to 100, in order to clear the text.
![The Flag!](https://i.imgur.com/MkJNcUB.png)

And there is the flag!


## Flag
> `picoCTF{n0w_y0u_533_m3}`
