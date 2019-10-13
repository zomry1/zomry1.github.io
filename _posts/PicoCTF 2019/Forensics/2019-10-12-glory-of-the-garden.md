---
layout: post
title: PicoCTF 2019 - Glory of the Garden
categories: [PicoCTF, Forensics]
tags: [Easy, Forensics, PNG, Hex]
---

# *Glory of the Garden*

## Information

| Points |Category  | Level|
|--|--|--|
| 50 | Forensics  |Easy |

## Challenge

> This [garden](https://2019shell1.picoctf.com/static/064eaf1591900ad250736459aa2448a0/garden.jpg) contains more than it seems. You can also find the file in /problems/glory-of-the-garden_6_0d6d3ea97757b84c7a51a38daa7dca8d on the shell server.

### Hint

> What is a hex editor?

## Solution
So I download the file and it's just a photo of a garden...
the hint talks about hex editor so I open [one](https://hexed.it/) in the browser, and load the image to it.
![Hex editor online](https://i.imgur.com/TQ7fpN9.png)
So I load the image to it thought the "Open file" button and now I can see a lot of dump...
Let's use the search to see if we can find the flag format and press Enter
![Search flag format](https://i.imgur.com/J9Unp08.png)
Press on what the editor found, and we found the flag!
![The flag!](https://i.imgur.com/MM2Ag01.png)
## Flag
> `picoCTF{more_than_m33ts_the_3y3f20F5be9}`

