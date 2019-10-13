---
layout: post
title: PicoCTF 2019 - WhitePages
categories: [PicoCTF, Forensics]
tags: [Easy, Forensics, Files]
---

# *WhitePages*

## Information

| Points |Category  | Level|
|--|--|--|
| 250 | Forensics  |Medium|

## Challenge

> I stopped using YellowPages and moved onto WhitePages... but [the page they gave me](https://2019shell1.picoctf.com/static/0c6da182a2b6eb85c909014da28377d5/whitepages.txt) is all blank!
 
### Hint

> 

## Solution

I download the file, and opened it -
![The file](https://i.imgur.com/A8Yr1yT.png)
There is nothing I can see in it, but when i press Ctrl + A to mark all, I can see that there is something!
![There is something](https://i.imgur.com/0hRa270.png)
The name of the challenge make me think about [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character)
Those characters are invisible but still are in the file. So after some searching in the web I saw a interpreter for those white-spaces, but nothing came out.
So I go back to the file to check if all the chars are the same or there are different white-spaces in the file.
I copy the first char and Ctrl+F in the file - 

As you can see, there some holes so this is different white-spaces chars, I copy one of the "holes" and search too, I found that the file include only 2 diffrenet white-spaces.
So after some time I thought about binary, maybe those chars signal 1 and 0s.

So I wrote this python script:
*There is much to scroll because the text of the file is just one line*
```python
# coding=utf8

text = '                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                '

firstType = ' '
secondType =  ' '
binaryString = ''

for char in text: #Foreach char
	if char == firstType: #Check if it is the first type
		binaryString += '0' #Mark it as 0
	else:
		binaryString += '1' #Mark it as 1

print(binaryString) #Print result

```

So it's just move on each char and set it to 0 or 1.
I tried it when the first type is 0 and the second one is 1, and the opposite,
the opposite worked...
run the script - 
![the script](https://i.imgur.com/zPc0Syq.png)
So we got an binary number, used this [site](https://www.rapidtables.com/convert/number/binary-to-ascii.html) to convert it to a meaningful text -
![The flag](https://i.imgur.com/yeghTuu.png)
We got the flag!

## Flag
> `picoCTF{not_all_spaces_are_created_equal_c167040c738e8bcae2109ef4be5960b1}`
