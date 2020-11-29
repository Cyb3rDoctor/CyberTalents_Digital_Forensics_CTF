# Bomp

## Challenge description:

```
Why dosen't my BOMP Explode!!
Format: Flag{}
```

## Solution:

The challenge file is named "b0mp" (without an extension), and **file** command didn't determine the file type:

![image](https://user-images.githubusercontent.com/70543460/100540475-43b58080-3246-11eb-8055-c02431f81f76.png)

<br/><br/>

So, I opened the file in a hex editor:

![image](https://user-images.githubusercontent.com/70543460/100540542-8b3c0c80-3246-11eb-91c0-d6fa50ec9b4d.png)

<br/><br/>

The most interesting thing in the decoded text is **BGRs**

![image](https://user-images.githubusercontent.com/70543460/100540614-f7b70b80-3246-11eb-88c8-4f390ae9b0b3.png)

<br/><br/>

I searched for the terms **BGRs** and **hex**, in order to find something related to what I was looking for (the file type).
And while checking the search results, I found that the file type is **BMP (bitmap image file)**

![image](https://user-images.githubusercontent.com/70543460/100540737-d4d92700-3247-11eb-8985-a9dbcc3a9ff5.png)

Note: The challenge name (**B**o**mp**) made me sure that it's a **BMP** image

<br/><br/>

Then I searched for the magic bytes of the **BMP** files:

![image](https://user-images.githubusercontent.com/70543460/100543759-ae70b700-325a-11eb-9485-8b03de80fb6d.png)

Then I fixed them in the challenge file:

![image](https://user-images.githubusercontent.com/70543460/100543800-f263bc00-325a-11eb-86d6-3e9b6087a98f.png)

<br/><br/>

After that, I tried to open the image but I couldn't...

<br/><br/>

So I tried **file** command again:

![Annotation 2020-11-29 155817](https://user-images.githubusercontent.com/70543460/100544399-0f4dbe80-325e-11eb-84f8-ced97d902093.png)

It's clear from the output of **file** command that the size of the image should be fixed...

<br/><br/>

Then I read about the BMP images header structure...

<br/><br/>

![image](https://user-images.githubusercontent.com/70543460/100547376-15986680-326f-11eb-86dd-c5587ad2a8f2.png)

<br/><br/>

According to the above table, and after analyzing the challenge image in a hex editor,
**the image width**, **the image height**, **the number of color planes**, and **the bit depth** need to be fixed in the challenge image!

<br/><br/>

![image](https://user-images.githubusercontent.com/70543460/100547426-58f2d500-326f-11eb-84ca-6f382f12421b.png)

<br/><br/>

I don't know the correct values that need to be fixed,
so I downloaded a random BMP image, then I copied **the image width**, **the image height**, **the number of color planes**, and **the bit depth** values from it
to the challenge image,
then I opened the challenge image with **GIMP**, and it looked like this:

![image](https://user-images.githubusercontent.com/70543460/100549563-44690980-327c-11eb-87a2-58d201290070.png)

<br/><br/>

After that, I renamed the challenge image to **b0mp.data**; because I wanted to open it in **GIMP** as a **raw image data**

And I adjusted the width and the offset until I saw the flag **(It was flipped vertically)** :

<br/><br/>

![image](https://user-images.githubusercontent.com/70543460/100549934-f86b9400-327e-11eb-967c-b1bd749bd56d.png)

<br/><br/>

![image](https://user-images.githubusercontent.com/70543460/100550006-75970900-327f-11eb-89ab-b7222bbdf9ff.png)

<br/><br/>

--------------------

# Note:

After creating the above writeup, I figured out that the challenge file can be opened directly in GIMP as a raw image data without fixing anything!

But no problem, at least I/you have learnt some information about BMP structure :)
