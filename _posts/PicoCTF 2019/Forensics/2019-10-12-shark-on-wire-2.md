---
layout: post
title: PicoCTF 2019 - shark on wire 2
categories: [PicoCTF, Forensics]
tags: [Easy, Forensics, Wireshark, Pcap]
---

# *shark on wire 2*

## Information

| Points |Category  | Level|
|--|--|--|
| 300 | Forensics  |Medium |

## Challenge

> We found this [packet capture](https://2019shell1.picoctf.com/static/dcd259894e0efe9d6e91da2af47e6369/capture.pcap). Recover the flag that was pilfered from the network. You can also find the file in /problems/shark-on-wire-2_0_3e92bfbdb2f6d0e25b8d019453fdbf07.
 
### Hint

> Try using a tool like Wireshark
> What are streams?

## Solution

I open the pcap file with Wireshark, start to filltering udp and tcp protocols,
look at the streams, and search in the content of the packets (like I did in "shark on wire 1" [Add link]).
But nothing came out, so I took a look at the piazza forum to get some hints, and the main conclusion from the posts was tha**t the flag is not in the body, and try to find a message that the
body look suspicious and look at the headers.** 
So again filtering and filtering again, till I found this:
![right filter](https://i.imgur.com/1Q3igVr.png)
The filter:

    udp.port == 22
 filter for only UDP protocols with the port 22, all the packets as the same data... but the first and the last packets that contain "start" and "end" - **this is suspicious**. So if it's not in the body of the packets but in the headers.
 Take a look at the UDP header:
 ![UDP header](https://i.imgur.com/yaqSO9B.png)
 The destination port is all the same (22), the length too, it's probably not the checksum because it's can't be modified easily so we left with the **source port**, as we can see each message has different source port! each one of them start with 5 and has 3 digits.
 It took some time but I came with the idea maybe the 3 digits are a ASCII code for chars.
 So i wrote each of the numbers in a line and put them in this [site](https://cryptii.com/pipes/decimal-text) But this was not in the format and had no meaning.. but I cloud see the letters C , T ,F and { , } So I realized i didn't wrong but just the order of the chars was wrong.
 So I back to Wireshark and notice to the "No." column:
 ![No. column](https://i.imgur.com/n3NNcuO.png)
 The order was wrong so I click on it, to order the list by the No. and tried again to enter the numbers:

> 112 105 99 111 67 84 70 123 112 49 76 76 102 51 114 51 100 95 100 97 116 97 95 118 49 97 95 115 116 51 103 48 125

![The flag](https://i.imgur.com/buunwKF.png)
And there is the flag!

## Flag
> `picoCTF{p1LLf3r3d_data_v1a_st3g0}`
