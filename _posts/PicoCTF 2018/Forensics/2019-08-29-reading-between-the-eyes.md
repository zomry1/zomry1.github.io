---
layout: post
title: PicoCTF 2018 - Reading Between the Eyes
categories: [PicoCTF, Forenscis]
tags: [Easy, Forensics, Web tool, Stenography, Image]
---

## Information

| Points |Category  | Level|
|--|--|--|
| 150 | Forensics |Easy |

## Challenge

>Stego-Saurus hid a message for you in this [image](https://2018shell.picoctf.com/static/9129761dbc4bf494c47429f85ddf7434/husky.png), can you retreive it?

### Hint

>Maybe you can find an online decoder?

## Solution

First of all when you got an image, just try to use the online forensics tools for images, so just search for "stenography online decoder" and go to the first [result](https://stylesuxx.github.io/steganography/)
upload the image and press "decode" and here is the flag!

This encoder and decoder use the LSB stenography method, which in a few words, hide in each pixel at the LSB of each color (the pixel is an R,G,B byte for each one of them) a bit from the encrypted message, and the naked eye can't see any difference because it's the least significant bit.
For more information I recommend on this [article](https://www.boiteaklou.fr/Steganography-Least-Significant-Bit.html)



## Flag
> `picoCTF{r34d1ng_b37w33n_7h3_by73s}`
