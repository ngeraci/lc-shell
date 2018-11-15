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
$ cd Desktop/shell-lesson/images
~~~
{: .bash}

In this directory, we have 30 TIFF files and 30 JPEG files. The TIFF files are our master copies of the images, and the JPEG files are access derivatives. Instead of having them mixed together in one place, we want to organize them into two folders called `master` and `access`.

(In real life, of course, they would be a collection of different images. For the purposes of this workshop, they're all copies of this cool cat from the [National Library of Medicine](https://collections.nlm.nih.gov/catalog/nlm:nlmuid-101611398-img)):

![Black and white photo of a cat dressed as a nurse](assets/img/nlm_nlmuid-101611398-img_001.jpg)
