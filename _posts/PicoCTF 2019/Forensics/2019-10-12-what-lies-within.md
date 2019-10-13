---
layout: post
title: PicoCTF 2019 - What Lies Within
categories: [PicoCTF, Forensics]
tags: [Easy, Forensics, PNG]
---

# *What Lies Within*

## Information

| Points |Category  | Level|
|--|--|--|
| 150 | Forensics  |Easy |

## Challenge

> Theres something in the [building](https://2019shell1.picoctf.com/static/aec3861fc4d5bce4d39dc0db196426de/buildings.png). Can you retrieve the flag?
 
### Hint

> There is data encoded somewhere, there might be an online decoder

## Solution

So as the hint say, there must be decoder online, I search "image decoder online" of course....
And I found this [site](https://stylesuxx.github.io/steganography/).
Chose the decode tab and upload the image, and press "Decode".
![The flag!](https://i.imgur.com/0kABBuU.png)
And there is the flag!

## Flag
> `picoCTF{h1d1ng_1n_th3_b1t5}`
