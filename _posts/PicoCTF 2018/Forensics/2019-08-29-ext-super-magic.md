---
layout: post
title: PicoCTF 2018 - Ext Super Magic
categories: [PicoCTF, Forenscis]
tags: [Medium, Forensics, Disk Image]
---


## Information

| Points |Category  | Level|
|--|--|--|
| 250| Forensics |Medium|

## Challenge

>We salvaged a ruined Ext SuperMagic II-class mech recently and pulled the  [filesystem](https://2018shell.picoctf.com/static/b9ff30ec03a9007fb1b1cd6ae15fae84/ext-super-magic.img)  out of the black box. It looks a bit corrupted, but maybe there's something interesting in there. You can also find it in /problems/ext-super-magic_1_c544657e659accef770d3f2bc8384a8c on the shell server.

### Hint

>-   Are there any  [tools](https://en.wikipedia.org/wiki/Fsck)  for diagnosing corrupted filesystems? What do they say if you run them on this one?
>-   How does a linux machine know what  [type](https://www.garykessler.net/library/file_sigs.html)  of file a  [file](https://linux.die.net/man/1/file)  is?
>-   You might find this  [doc](http://www.nongnu.org/ext2-doc/ext2.html)  helpful.
>-   Be careful with  [endianness](https://en.wikipedia.org/wiki/Endianness)  when making edits.
>-   Once you've fixed the corruption, you can use /sbin/[debugfs](https://linux.die.net/man/8/debugfs)  to pull the flag file out.

## Solution

I tried to use the command file in order to check what file we have but it just return "data"... not very helpful...

By the name of the challenge I undertood that this image is of an ext filesystem, there is an a command in UNIX to check those images, so I wrote:

    debufs ext-super-magic.img

![Debugfs](https://i.imgur.com/jZ46GoS.png)

and its return an error because "Bad magic number in super-block". So i googled after magic number in suplerblock and found the answer [here](https://superuser.com/questions/239088/whats-a-file-systems-magic-number-in-a-super-block)
So basiclly it's just a sequence of numbers in spesific posiiton in each file that tell allow us to recognize the format of the file. (and this is how the file command works)
Also in the answer the user added 

> "For example, an ext2/ext3/ext4 filesystem always has the bytes `0x53 0xEF` at positions 1080–1081."

So in order to fix the image file we need to overwrite in those ofsets those values.
Let's write a little python script to fix this:
```python
with open("ext-super-magic.img", "r+b") as ext:
    ext.seek(0x438)  #Seek to the needed offset (0x438 in hex = 1080)
    ext.write(b"\x53\xef")  #Write the magic number
print("Magic numbers fixed")
```
Now let's run the script:

    python3 magic_numbers_fix.py

![Fix magic number](https://i.imgur.com/XNZHrUz.png)
In order to check if it's really worked, let's use the file command again (remmber last time it just return "data").

    file ext_super_magic.image

![File fixed file](https://i.imgur.com/hOIGWUW.png)
Now let's use again "debugfs" in order to access the files.

    debugfs ext-super-magic.img

![No error](https://i.imgur.com/zRVyeEU.png)
And now there is no error! use:

    ls

   To see all the files in the image, press Enter to scroll down.
   and found file named "flag.jpg"
![ls](https://i.imgur.com/YHhjZ31.png)
In order to save it, enter:

    dump flag.jpg flag.jpg
    
![Dump file](https://i.imgur.com/3dxfws5.png)
Now open the flag and here it is!
![The Flag!](https://i.imgur.com/PzAubXv.png)
## Flag
> `picoCTF{B3a388F85f93246B9DBA7Cc0fbBA5eE0}`
