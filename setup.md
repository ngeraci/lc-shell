---
layout: page
title: Setup
root: .
---

## Terminal Setup

Bash is the default shell on most Linux distributions and Mac OS. 
Windows users will need to install Git Bash to provide a UNIX-like environment.

- **Linux:** The default shell is usually Bash, but if your machine is set up differently you can run it by opening a terminal and typing `bash`.  There is no need to install anything. Look for Terminal in your applications to start the Bash shell.
- **Mac OS:** Bash is the default shell in all versions of Mac OS, you do not need to install anything. Open Terminal from `/Applications/Utilities` or spotlight search to start the Bash shell.
- **Windows:** On Windows, CMD or PowerShell are normally available as the default shell environments. These use a syntax and set of applications unique to Windows systems and are incompatible with the more widely used UNIX utilities. However, a Bash shell can be installed on Windows to provide a UNIX-like environment. For this lesson we suggest using Git Bash, part of the [Git for Windows](https://git-for-windows.github.io/) package:
    - Download the latest Git for Windows [installer](https://git-for-windows.github.io/).
    - Double click the `.exe` to run the installer (for example, `Git-2.13.3-64-bit.exe`) using the default settings.
    - Once installed, open the shell by selecting Git Bash from the start menu (in the Git folder).
    
## Data Files

You need to download some files to follow this lesson:

1. Download [shell-lesson.zip](https://github.com/ngeraci/pca-shell/raw/gh-pages/data/shell-lesson.zip) and move the file to your Desktop.
2. Unzip/extract the file (ask if you need help with this step). You should end up with a new folder called `shell-lesson` on your Desktop.
3. Open a terminal and type:

~~~
$ cd
~~~
{: .bash}

In the lesson, you will find out how to access the data in this folder.

[template]: {{ site.workshop_repo }}
