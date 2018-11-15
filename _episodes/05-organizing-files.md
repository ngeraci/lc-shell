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

In this directory, we have 10 TIFF files and 10 JPEG files. The TIFF files are our master copies of the images, and the JPEG files are access derivatives. Instead of having them mixed together in one place, we want to organize them into two folders called `master` and `access`.

(In real life, of course, they would be a collection of different images. For the purposes of this workshop, they're all copies of this cat nurse from the [National Library of Medicine](https://collections.nlm.nih.gov/catalog/nlm:nlmuid-101611398-img)):

![Black and white photo of a cat dressed as a nurse](https://ngeraci.github.io/lc-shell/assets/img/nlm_nlmuid-101611398-img.jpg)

### Make directories

Let's create our new directories:
~~~
mkdir master
mkdir access
~~~
{: .bash}

### Move TIFF files

Now, let's use a wildcard to will move all files ending in `.tif` from our current directory to the directory `master`. We'll run it once with `echo` to make sure it will do what we want it to do:
~~~
echo mv *.tif master
~~~
{: .bash}

~~~
mv nlm_nlmuid-101611398-img_001.tif nlm_nlmuid-101611398-img_002.tif nlm_nlmuid-101611398-img_003.tif nlm_nlmuid-101611398-img_004.tif nlm_nlmuid-101611398-img_005.tif nlm_nlmuid-101611398-img_006.tif nlm_nlmuid-101611398-img_007.tif nlm_nlmuid-101611398-img_008.tif nlm_nlmuid-101611398-img_009.tif nlm_nlmuid-101611398-img_010.tif master/
~~~
{: .output}

Looks good. Now let's remove `echo` from our command, and use it to actually move the files.
~~~
mv *.tif master
~~~
{: .bash}

By default, we don't get output from the `mv` command if it's run successfully. But we can use `ls` to see that the files have moved:
~~~
ls master
~~~
{: .bash}

~~~
nlm_nlmuid-101611398-img_001.tif
nlm_nlmuid-101611398-img_002.tif
nlm_nlmuid-101611398-img_003.tif
nlm_nlmuid-101611398-img_004.tif
nlm_nlmuid-101611398-img_005.tif
nlm_nlmuid-101611398-img_006.tif
nlm_nlmuid-101611398-img_007.tif
nlm_nlmuid-101611398-img_008.tif
nlm_nlmuid-101611398-img_009.tif
nlm_nlmuid-101611398-img_010.tif
~~~
{: .output}

### Move JPEG files

Now let's repeat the same pattern with to move our JPEG files to `access`:

~~~
mv *.jpg access
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
nlm_nlmuid-101611398-img_001.jpg
nlm_nlmuid-101611398-img_002.jpg
nlm_nlmuid-101611398-img_003.jpg
nlm_nlmuid-101611398-img_004.jpg
nlm_nlmuid-101611398-img_005.jpg
nlm_nlmuid-101611398-img_006.jpg
nlm_nlmuid-101611398-img_007.jpg
nlm_nlmuid-101611398-img_008.jpg
nlm_nlmuid-101611398-img_009.jpg
nlm_nlmuid-101611398-img_010.jpg
~~~
{: .output}

### Count files

There's also a way we can combine commands to verify that we have the correct number of files in each folder. By using the pipe character (`|`), we can pass the output of `ls`, which lists files, to `wc -l`, which gets the word count (`wc`) of textual data in lines (`-l`).

~~~
ls access|wc -l
~~~
{: .bash}

~~~
10
~~~
{: .output}

~~~
ls master|wc -l
~~~
{: .bash}
~~~
10
~~~
{: .output}

Cool, each directory has 10 files in it, like it should.  `ls|wc -l` is a useful combination to remember for counting the number of files in a directory.


### Rename files
What if we also want to rename these files? You may have noticed that all of the image files contain the characters `-img` within the filenames, like `nlm_nlmuid-101611398-img_007.jpg`. Perhaps including `-img` in image filenames was part of our workplace's old filenaming convention, but that's since changed. So we want to remove `-img` from all the filenames, like turning `nlm_nlmuid-101611398-img_007.jpg` into `nlm_nlmuid-101611398_007.jpg`

Let's test the following loop:
~~~
for file in access/*.jpg master/*.tif; do echo mv $file ${file//-img/}; done
~~~
{: .bash}

~~~
mv access/nlm_nlmuid-101611398-img_001.jpg access/nlm_nlmuid-101611398_001.jpg
mv access/nlm_nlmuid-101611398-img_002.jpg access/nlm_nlmuid-101611398_002.jpg
mv access/nlm_nlmuid-101611398-img_003.jpg access/nlm_nlmuid-101611398_003.jpg
mv access/nlm_nlmuid-101611398-img_004.jpg access/nlm_nlmuid-101611398_004.jpg
...
~~~
{: .output}

How does this work? The first part of the loop, `for file in access/*.jpg master/*.tif`; says that we're going to select all of the files in `access` that end in `.jpg`, and all of the files in `master` that end in `.tif`. `mv $file` moves the file, and `${file//-img/}` sets the file's destination location as a version of the file's name where `-img` is substituted with nothing, a bit like a command-line version of find and replace. The substitution pattern it uses works like this: `{input//text to find/text to replace found text with}`.

To actually rename the files, let's now run the loop without `echo`:
~~~
for file in access/*.jpg master/*.tif; do mv $file ${file//-img/}; done
~~~
{: .bash}

Hooray! We've now updated all our file names. We've taken a directory of 20 files, and in just a few minutes, organized them into subdirectories by file type, and changed their names to reflect our current filenaming practice. And whether we had 20 or 2,000 files, we could approach the task pretty much the same way.

### Saving file paths to a text file

One last thing: we want a report listing all the files in our `access` and `master` directories. One way we can do this is by redirecting the output of `ls` to a text file.

~~~
ls access master > catnurse_paths.txt
~~~
{: .bash}

Now let's view our new file:
~~~
cat catnurse_paths.txt
~~~
{: .bash}

~~~
access:
nlm_nlmuid-101611398_001.jpg
nlm_nlmuid-101611398_002.jpg
nlm_nlmuid-101611398_003.jpg
nlm_nlmuid-101611398_004.jpg
nlm_nlmuid-101611398_005.jpg
nlm_nlmuid-101611398_006.jpg
nlm_nlmuid-101611398_007.jpg
nlm_nlmuid-101611398_008.jpg
nlm_nlmuid-101611398_009.jpg
nlm_nlmuid-101611398_010.jpg

master:
nlm_nlmuid-101611398_001.tif
nlm_nlmuid-101611398_002.tif
nlm_nlmuid-101611398_003.tif
nlm_nlmuid-101611398_004.tif
nlm_nlmuid-101611398_005.tif
nlm_nlmuid-101611398_006.tif
nlm_nlmuid-101611398_007.tif
nlm_nlmuid-101611398_008.tif
nlm_nlmuid-101611398_009.tif
nlm_nlmuid-101611398_010.tif
...
~~~
{: .output}

🎉
