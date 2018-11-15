---
title: "What is the shell?"
teaching: 20
exercises: 10
questions:
- "What is the shell?"
- "What is the command line?"
- "Why should I use it?"
objectives:
- "Explain the basics of the Unix shell"
- "Explain why and how to use the command line"
keypoints:
- "The shell is powerful"
- "The shell can be used to copy, move, and combine multiple files"
---

## Introduction: What is the shell, and why should I use it?

If you've ever had to deal with large amounts of data or large numbers of files scattered across your computer or a remote server, you know that copying, moving, renaming, counting, searching through, or otherwise processing those files manually can be immensely time-consuming and error-prone. Fortunately, there is an extraordinarily powerful and flexible tool designed for just that purpose.

The shell (sometimes referred to as the "Unix shell", for the operating system where it was first developed) is a program that allows you to interact with your computer using typed text commands. It is the primary interface used on Linux and Unix-based systems, such as MacOS, and can be installed optionally on other operating systems such as Windows.

It is an example of a "command line interface", where instructions are given to the computer by typing in commands, and the computer responds by performing a task or generating an output. This output is often directed to the screen, but can be directed to a file, or even to other commands, creating powerful chains of actions with very little effort.

Using a shell can feel more similar to programming than to using a mouse. Commands are terse (often only a couple of characters long), their names are frequently cryptic, and their output is lines of text rather than something visual like a graph. On the other hand, with only a few keystrokes, the shell allows you to combine existing tools into powerful pipelines and to handle large volumes of data automatically. This automation not only makes you more productive, but also improves the reproducibility of your workflows by allowing you to save and then repeat them with a few simple commands. Understanding the basics of the shell provides a useful foundation for learning to program, since some of the concepts you will learn here—such as loops, values, and variables—will translate to programming.

In addition to the basic commands we'll cover today, there are many more specialized tools, like [FFmpeg](https://ffmpeg.org/) for audiovisual media, [ImageMagick](https://www.imagemagick.org/script/index.php) for image files, and [ExifTool](https://www.sno.phy.queensu.ca/~phil/exiftool/) for working with embedded metadata, are operated through the shell. Familiarity with the shell will allow you to use programs like these to make more complex changes to files in bulk, like converting file types.


### Where is my shell?

The shell is a program that is usually launched on your computer much in the way you would start any other program. However, there are numerous kinds of shells with different names, and they may or may not be already installed. The shell is central to Linux-based computers, and MacOS machines ship with Terminal, a shell program. For Windows users, popular shells such as Cygwin or Git Bash provide a Unix-like interface, but may need to be installed separately.

For this lesson, we will use Git Bash for Windows users, Terminal for Mac OS, and the shell for Linux users.
