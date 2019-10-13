---
layout: post
title: PicoCTF 2019 - shark on wire 1
categories: [PicoCTF, Forensics]
tags: [Easy, Forensics, Wireshark, Pcap]
---

# *shark on wire 1*

## Information

| Points |Category  | Level|
|--|--|--|
| 150 | Forensics  |Easy |

## Challenge

> We found this [packet capture](https://2019shell1.picoctf.com/static/ae9ca8cff43ed638ed5d137f9ece7455/capture.pcap). Recover the flag. You can also find the file in /problems/shark-on-wire-1_0_13d709ec13952807e477ba1b5404e620.
 
### Hint

> Try using a tool like Wireshark
> What are streams?

## Solution

I download the file, and the file extension is pcap, So it's Wireshark file.
For those who don't know what it is, [Wireshark](https://en.wikipedia.org/wiki/Wireshark) is a sniffing and packet analyzer program.

So download the program, and open the file with it - 
![Wireshark](https://i.imgur.com/oDdBRAI.png)
Most of the time, the packters we are intrested in are UDP and TCP protocols, as I scroll down
I could see a lot of UDP packets.
I chose randomly one of those packets (just click on it), and opened the data tab - 
![Packet](https://i.imgur.com/tFcqcdN.png)
We can see that it's just a 'b', tried this on other packets but nothing came out.
I cant check each packet...So Wireshark has it own filtering system, So i wanted to search a udp packets that contains the picoCTF format, after some searching it the web I found this as the filter I wanted -

> udp contains "picoCTF"

(Dont forget to press enter to filter)
tried it in Wireshark but nothing came out again..
![Nothing](https://i.imgur.com/hGkPFeq.png)
So mabye the data is fragmented between many packets?
In order to check this there is something called [udp streams](https://www.wireshark.org/docs/wsug_html_chunked/ChAdvFollowStreamSection.html)
So in order to check those streams, I deleted the filter (and pressed Enter), chose random udp packet and press right click on it -> follow -> udp stream:
![UDP stream](https://i.imgur.com/93Awf6B.png)

A window open with the whole text of this stream, but it just junk...

Maybe this is not the correct stream, I tried to look at the others with change the stream id:
![Change stream](https://i.imgur.com/zT7oKd5.png)
I found the flag in the 5th stream!
![The flag](https://i.imgur.com/9105jay.png)

## Flag
> `picoCTF{StaT31355_636f6e6e}`
