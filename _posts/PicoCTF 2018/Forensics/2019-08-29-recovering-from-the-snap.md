---
layout: post
title: PicoCTF 2018 - Recovering From the Snap
categories: [PicoCTF, Forenscis]
tags: [Easy, Forensics, Disk Image]
---

## Information

| Points |Category  | Level|
|--|--|--|
| 150 | Forensics |Medium |

## Challenge

>There used to be a bunch of [animals](https://2018shell.picoctf.com/static/1603334c6d1519a49283974d0d480ffe/animals.dd) here, what did Dr. Xernon do to them?

### Hint

>Some files have been deleted from the disk image, but are they really gone?

## Solution

So we have a dd file, this extension  tell as that this file is a raw image format, so basically it's a replica of a hard drive disk.

So we have an amazing tool for this stuff (disk images) named 

"[TestDisk](https://www.cgsecurity.org/wiki/TestDisk)"

So let's use it, in open the terminal in the folder of the dd file, and enter

    testdisk animals.dd

![start testDisk](https://i.imgur.com/kZpDAfI.png)

the program will load up, and show you the media in this image, press Enter to proceed.
Now we can see the "hint" says that no partition table were found in the image, so probably there isn't one in the image, so let's press Enter to continue without partition (None).

![No partition](https://i.imgur.com/x0155il.png)

Now we need to chose which partition we want to boot but there is only one so press Enter to boot it.

![Choose boot partition](https://i.imgur.com/NMf3MUE.png)

Now in order to see all the directories and files we need to choose "List" so use the right arrow to move from "Rebuild BS" to "List" and press Enter.

![List](https://i.imgur.com/bnMSGsL.png)

Now we can see all the files that are in the image of the disk, and we can see file named "theflag.jpg", in order to copy it, select it and press "C".

![enter image description here](https://i.imgur.com/Z0gSNce.png)

And now browse where you want to copy the file, and press "C" again, now press "q" few times to exit from the program.

![destination folder](https://i.imgur.com/3i4Ai1A.png)

Go to your destination folder and enjoy from the flag!

![the flag!](https://i.imgur.com/WAsRz4t.png)

## Flag
> `picoCTF{th3_5n4p_happ3n3d}`
