---
title: "Organizing files"
teaching: 20
exercises: 10
questions:
- "How do we combine what we've learned so far to organize and rename a group of files?"
objectives:
- "Understand how the basic concepts we've learned so far can be combined and applied."
- "Use shell commands to move to a different directory"
keypoints:
- "There are many ways shell commands can be combined to automate common file management tasks."
---
## Organizing files

Now that we've gone over some fundamental shell concepts, let's walk through one way we could combine them to tackle a common file-organization task.

First, let's move into the directory `shell-lesson/images`:
~~~
cd Desktop/shell-lesson/images
~~~
{: .bash}

In this directory, we have 30 TIFF files and 30 JPEG files. The TIFF files are our master copies of the images, and the JPEG files are access derivatives. Instead of having them mixed together in one place, we want to organize them into two folders called `master` and `access`.

(In real life, of course, they would be a collection of different images. For the purposes of this workshop, they're all copies of this cool cat from the [National Library of Medicine](https://collections.nlm.nih.gov/catalog/nlm:nlmuid-101611398-img)):

![Black and white photo of a cat dressed as a nurse](https://ngeraci.github.io/lc-shell/assets/img/nlm_nlmuid-101611398-img.jpg){:height="50%" width="50%"}

Let's create our new directories:
~~~
mkdir master
mkdir access
~~~
{: .bash}

Now, let's write a loop that will move all files ending in `.tif` from our current directory to the directory `master`. We'll run it once with `echo` to make sure it will do what we want it to do:
~~~
for file in *.tif; do echo mv $file master; done
~~~
{: .bash}

~~~
mv nlm_nlmuid-101611398-img_001.tif master
mv nlm_nlmuid-101611398-img_002.tif master
mv nlm_nlmuid-101611398-img_003.tif master
mv nlm_nlmuid-101611398-img_004.tif master
mv nlm_nlmuid-101611398-img_005.tif master
mv nlm_nlmuid-101611398-img_006.tif master
mv nlm_nlmuid-101611398-img_007.tif master
mv nlm_nlmuid-101611398-img_008.tif master
mv nlm_nlmuid-101611398-img_009.tif master
mv nlm_nlmuid-101611398-img_010.tif master
mv nlm_nlmuid-101611398-img_011.tif master
mv nlm_nlmuid-101611398-img_012.tif master
mv nlm_nlmuid-101611398-img_013.tif master
mv nlm_nlmuid-101611398-img_014.tif master
mv nlm_nlmuid-101611398-img_015.tif master
mv nlm_nlmuid-101611398-img_016.tif master
mv nlm_nlmuid-101611398-img_017.tif master
mv nlm_nlmuid-101611398-img_018.tif master
mv nlm_nlmuid-101611398-img_019.tif master
mv nlm_nlmuid-101611398-img_020.tif master
mv nlm_nlmuid-101611398-img_021.tif master
mv nlm_nlmuid-101611398-img_022.tif master
mv nlm_nlmuid-101611398-img_023.tif master
mv nlm_nlmuid-101611398-img_024.tif master
mv nlm_nlmuid-101611398-img_025.tif master
mv nlm_nlmuid-101611398-img_026.tif master
mv nlm_nlmuid-101611398-img_027.tif master
mv nlm_nlmuid-101611398-img_028.tif master
mv nlm_nlmuid-101611398-img_029.tif master
mv nlm_nlmuid-101611398-img_030.tif master
~~~
{: .output}

Looks good. Now let's remove `echo` from our loop, and use it to actually move the files.
~~~
$ for file in *.tif; do mv $file master; done
~~~
{: .bash}

By default, we don't get output from the `mv` command if it's run successfully. But we can use `ls` to see that the files have moved:
~~~
ls master
~~~
{: .bash}

~~~
nlm_nlmuid-101611398-img_001.tif  nlm_nlmuid-101611398-img_016.tif
nlm_nlmuid-101611398-img_002.tif  nlm_nlmuid-101611398-img_017.tif
nlm_nlmuid-101611398-img_003.tif  nlm_nlmuid-101611398-img_018.tif
nlm_nlmuid-101611398-img_004.tif  nlm_nlmuid-101611398-img_019.tif
nlm_nlmuid-101611398-img_005.tif  nlm_nlmuid-101611398-img_020.tif
nlm_nlmuid-101611398-img_006.tif  nlm_nlmuid-101611398-img_021.tif
nlm_nlmuid-101611398-img_007.tif  nlm_nlmuid-101611398-img_022.tif
nlm_nlmuid-101611398-img_008.tif  nlm_nlmuid-101611398-img_023.tif
nlm_nlmuid-101611398-img_009.tif  nlm_nlmuid-101611398-img_024.tif
nlm_nlmuid-101611398-img_010.tif  nlm_nlmuid-101611398-img_025.tif
nlm_nlmuid-101611398-img_011.tif  nlm_nlmuid-101611398-img_026.tif
nlm_nlmuid-101611398-img_012.tif  nlm_nlmuid-101611398-img_027.tif
nlm_nlmuid-101611398-img_013.tif  nlm_nlmuid-101611398-img_028.tif
nlm_nlmuid-101611398-img_014.tif  nlm_nlmuid-101611398-img_029.tif
nlm_nlmuid-101611398-img_015.tif  nlm_nlmuid-101611398-img_030.tif
~~~
{: .output}

Now let's repeat the same pattern with to move our JPEG files to `access`:

~~~
for file in *.jpg; do mv $file access; done
~~~
{: .bash}

Again, we won't see any output from our successful `mv` command, but we can double-check with `ls` that the files are where we want them to be:

~~~
ls
~~~
{: .bash}

~~~
access/  master/
~~~
{: .output}

~~~
ls access
~~~
{: .bash}

~~~
nlm_nlmuid-101611398-img_001.jpg  nlm_nlmuid-101611398-img_016.jpg
nlm_nlmuid-101611398-img_002.jpg  nlm_nlmuid-101611398-img_017.jpg
nlm_nlmuid-101611398-img_003.jpg  nlm_nlmuid-101611398-img_018.jpg
nlm_nlmuid-101611398-img_004.jpg  nlm_nlmuid-101611398-img_019.jpg
nlm_nlmuid-101611398-img_005.jpg  nlm_nlmuid-101611398-img_020.jpg
nlm_nlmuid-101611398-img_006.jpg  nlm_nlmuid-101611398-img_021.jpg
nlm_nlmuid-101611398-img_007.jpg  nlm_nlmuid-101611398-img_022.jpg
nlm_nlmuid-101611398-img_008.jpg  nlm_nlmuid-101611398-img_023.jpg
nlm_nlmuid-101611398-img_009.jpg  nlm_nlmuid-101611398-img_024.jpg
nlm_nlmuid-101611398-img_010.jpg  nlm_nlmuid-101611398-img_025.jpg
nlm_nlmuid-101611398-img_011.jpg  nlm_nlmuid-101611398-img_026.jpg
nlm_nlmuid-101611398-img_012.jpg  nlm_nlmuid-101611398-img_027.jpg
nlm_nlmuid-101611398-img_013.jpg  nlm_nlmuid-101611398-img_028.jpg
nlm_nlmuid-101611398-img_014.jpg  nlm_nlmuid-101611398-img_029.jpg
nlm_nlmuid-101611398-img_015.jpg  nlm_nlmuid-101611398-img_030.jpg
~~~
{: .output}

There's also a way we can combine commands to verify that we have the correct number of files in each folder. By using the pipe character (`|`), we can pass the output of `ls`, which lists files, to `wc -l`, which gets the word count (`wc`) of textual data in lines (`-l`).

~~~
ls access|wc -l
~~~
{: .bash}

~~~
30
~~~
{: .output}

~~~
ls master|wc -l
~~~
{: .bash}
~~~
30
~~~
{: .output}

Cool, each directory has 30 files in it, like it should.  `ls|wc -l` is a useful combination to remember for counting the number of files in a directory.
