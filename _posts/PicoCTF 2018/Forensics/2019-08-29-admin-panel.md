---
layout: post
title: PicoCTF 2018 - admin panel
categories: [PicoCTF, Forenscis]
tags: [Easy, Forensics, HTTP, WireShark, Packet Sniff]
---

## Information

| Points |Category  | Level|
|--|--|--|
| 150 | Forensics |Medium |

## Challenge

>We captured some [traffic](https://2018shell.picoctf.com/static/4b72ffeae766b0102106eabfe6be90b1/data.pcap) logging into the admin panel, can you find the password?

### Hint

>Tools like wireshark are pretty good for analyzing pcap files.

## Solution

Immediately when you see a pcap file you need to think about Wireshark.
> pcap files contains packets data of a network.

So let's open Wireshark and open the file:
![Wireshark](https://i.imgur.com/QLZrfkc.png)

But there are many packets what are we gonna do?
![meme](https://i.imgur.com/qvogqZe.png)

The power of Wireshark came from his filter options, the name of the challenge is admin panel, it's says that someone use an admin panel, probably from his browser, so let's filter for HTTP packets only, write in the filter box http and press enter.
![filter http](https://i.imgur.com/46ryx4j.png)

So now we have a few packets to search in, we can see that there are 2 requests for "login" page, remember in the challenge we asked to find the password, so it's our way, let's check each one of them, double click on packet to open it in a new window.
![First packet](https://i.imgur.com/CLqlEt8.png)

open the HyperText Transfer Protocol (HTTP) to check the information in this level.
We can see that it's a POST request, so there will be a data that sent to the server in this request, scroll down and we can see that the that is not encoded and we can read it, so the user is "jimmy" and the password is  "p4ssw0rd", so is it the flag? tried to enter this and got incorrect answer.
Let's check the other login request:
![Second packet](https://i.imgur.com/eMtiFsV.png)

We can see it's again a POST request and now the user is admin, and there is no password.. why?
we can see that there is a warring right there says:

> [Packet size limited during capture:  URL Encoded Form Data truncated]

What?!?! so the password just truncated?!
Don't worry it's just truncated from the wireshark interface, we can still the raw data right down the screen, and what a beautiful look, here is the flag!
## Flag
> `picoCTF{n0ts3cur3_9feedfbc}`
