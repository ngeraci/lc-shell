---
title: "Navigating the filesystem"
teaching: 20
exercises: 10
questions:
- "How do you move around the filesystem in the shell?"
objectives:
- "Use shell commands to list directories and files"
- "Use shell commands to move to a different directory"
keypoints:
- "Knowing where you are in your directory structure is key to working with the shell"
---
## Navigating the shell

We will begin with the basics of navigating the Unix shell.

Let's start by opening the shell. This likely results in seeing a black window with a cursor flashing next to a dollar sign.
This is our command line, and the `$` is the command **prompt** to show that the system is ready for our input.
The appearance of the prompt will vary from system to system, depending on how the set up has been configured,
but it usually ends with a `$`.

When working in the shell, you are always *somewhere* in the computer's
file system, in some folder (directory). We will therefore start by finding out
where we are by using the `pwd` command, which you can use whenever you are unsure
about where you are. It stands for "print working directory" and the result of the
command is printed to your standard output, which is the screen.

Let's type `pwd` and hit enter to execute the command:
(The `$` sign is used to indicate a command to be typed on the command prompt,
 but we never type the `$` sign itself, just what follows after it.)

~~~
$ pwd
~~~
{: .bash}
~~~
/Users/riley
~~~
{: .output}

The output will be a path to your home directory. Let's check if we recognize it
by listing the contents of the directory. To do that, we use the `ls` command:

~~~
$ ls
~~~
{: .bash}
~~~
Applications Documents    Library      Music        Public
Desktop      Downloads    Movies       Pictures
~~~
{: .output}

Now let's go somewhere else. We can do that through the `cd` or Change Directory command:
(Note: On Windows and Mac, by default, the case of the file/directory doesn't matter
On Linux it does.)

~~~
$ cd Desktop
~~~
{: .bash}

Notice that the command didn't output anything. This means that it was carried
out successfully. Let's check by using `pwd`:

~~~
$ pwd
~~~
{: .bash}
~~~
/Users/riley/Desktop
~~~
{: .output}

If something had gone wrong, however, the command would have told you. Let's
test that by trying to move into a non-existent directory:

~~~
$ cd "Folder full of perfect code"
~~~
{: .bash}
~~~
bash: cd: Folder full of perfect code: No such file or directory
~~~
{: .output}

Notice that we surrounded the name by quotation marks. This lets the shell know that we mean 'one single thing called "Folder full of perfect code"', not 'six different things', is to use (single or double) quotation marks.

We've now seen how we can go 'down' through our directory structure
(as in into more nested directories). If we want to go back, we can type `cd ..`.
This moves us 'up' one directory, putting us back where we started.
**If we ever get completely lost, the command `cd` without any arguments will bring
us right back to the home directory, the place where we started.**

> ## Previous Directory
> To switch back and forth between two directories use `cd -`.
{: .callout}

> ## Try exploring
>
> Move around the computer, get used to moving in and out of directories,
> see how different file types appear in the Unix shell. Be sure to use the `pwd` and
> `cd`, and `ls` commands you learned so far.
>
> If you're on Windows,
> also try typing `explorer .` to open Explorer for the current directory
> (the single dot means "current directory"). If you're on a Mac,
> try `open .` and for Linux try `xdg-open .`.
>
{: .challenge}


Being able to navigate the file system is very important for using the Unix shell effectively.
As we become more comfortable, we can get very quickly to the directory that we want.

> ## Getting help
>
> Use the `man` command to view the manual page (documentation) for a shell command.
> For example, `man ls` displays all the arguments available to you - which saves
> you remembering them all! Try this for each command you've learned so far.
> Use the `spacebar` to navigate the manual pages. Use `q` at any time to quit.
>
> ***Note*: this command only works on Mac and Linux**. It does not work directly on Windows.
> If you use Windows, you can search for a command on [http://man.he.net/](http://man.he.net/),
> and view the associated manual page. You can also often get more information about a command with the flag `--help`, such as `ls --help`.
>
> >## Answer
> >~~~
> >$ man ls
> >~~~
> >{: .bash}
> >~~~
> >LS(1)                     BSD General Commands Manual                    LS(1)
> >
> >NAME
> >     ls -- list directory contents
> >
> >SYNOPSIS
> >     ls [-ABCFGHLOPRSTUW@abcdefghiklmnopqrstuwx1] [file ...]
> >
> >DESCRIPTION
> >     For each operand that names a file of a type other than directory, ls
> >     displays its name as well as any requested, associated information.  For
> >     each operand that names a file of type directory, ls displays the names
> >     of files contained within that directory, as well as any requested, asso-
> >     ciated information.
> >
> >     If no operands are given, the contents of the current directory are dis-
> >     played.  If more than one operand is given, non-directory operands are
> >     displayed first; directory and non-directory operands are sorted sepa-
> >     rately and in lexicographical order.
> >
> >     The following options are available:
> >
> >     -@      Display extended attribute keys and sizes in long (-l) output.
> >
> >     -1      (The numeric digit ``one''.)  Force output to be one entry per
> >             line.  This is the default when output is not to a terminal.
> >
> >     -A      List all entries except for . and ...  Always set for the super-
> >             user.
> >
> >...several more pages...
> >
> >BUGS
> >     To maintain backward compatibility, the relationships between the many
> >     options are quite complex.
> >
> >BSD                              May 19, 2002                              BSD
> >
> >~~~
> >{: .output}
> {: .solution}
{: .challenge}
