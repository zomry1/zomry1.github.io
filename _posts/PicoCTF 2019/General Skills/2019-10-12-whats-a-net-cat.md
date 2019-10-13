---
layout: post
title: PicoCTF 2019 - what's a net cat?
categories: [PicoCTF, General Skills]
tags: [Easy, General Skills]
---

# *what's a net cat?*

## Information

| Points |Category  | Level|
|--|--|--|
| 100 |General Skills  |Easy |

## Challenge

> Using netcat (nc) is going to be pretty important. Can you connect to `2019shell1.picoctf.com` at port `49816` to get the flag?

### Hint

> nc [tutorial](https://linux.die.net/man/1/nc)

## Solution

> **netcat -** computer networking utility for reading from and writing to network
> connections using [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol") or [UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol).

Let's connect thought netcat -

> Open terminal -> nc 2019shell1.picoctf.com 49816

* nc - stands for netcat 
	* command syntax:
		>   nc ADDRESS PORT
		
## Flag
> `picoCTF{nEtCat_Mast3ry_a752a0d3}`