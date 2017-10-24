---
layout: page
title: Setup
permalink: /setup/
---

[![Yale Spinup]({{ page.root }}/assets/img/spinup_logo_word.png)](https://spinup.internal.yale.edu/)

We'll be connecting to virtual computers hosted in the cloud for you for the purposes of this course.
After we finish today, feel free to request an account for yourself at [spinup.internal.yale.edu](https://spinup.internal.yale.edu/).

### Find your Host!
If you want to follow along today, you'll need to connect to a remote computer.
This will be accomplished with a cryptographic network protocol called ssh.
You should should each receive a slip of paper with the host name of your virtual machine.

### Mac OSX / macOS
If you are on a mac, you already have ssh. All you need to do is open up your terminal app.
To open the terminal app, you can navigate to your apps then utilities directory and double click on its icon, or use spotlight to find it.

It should look something like this:

![Terminal App]({{ page.root }}/assets/img/macterm.png)

In order to connect to your virtual machine, you'll want to type something like

~~~
$ ssh student@spinup-######.spinup.yale.edu
~~~
{: .bash}

You'll be asked for your password, which is also on your slip of paper.

### Windows
The simplest way to use ssh on windows is with [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty). You can download an installer
by [clicking here](https://the.earth.li/~sgtatham/putty/latest/w32/putty-0.70-installer.msi).

When you open putty.exe, you should see a window like this:

![Putty window]({{ page.root }}/assets/img/putty.png)

Type your host name from your slip of paper (`spinup-######.spinup.yale.edu`) into the "Host Name
(or IP address)" box and click open. You will be prompted for your
username and password, which is also on your slip.

### Sample Files

Feel free to download a copy of the sample files on the computer in front
of you, but in order to follow along, you need to download the files
on the remote computer.

Copy the lines below and paste them into your terminal window. To paste in
Windows PuTTY, right click the mouse in the window. In macOS Terminal
use <kbd>⌘</kbd> + <kbd>v</kbd>

~~~
wget https://ycrc.github.io/PIL/data/PIL-data.zip
unzip PIL-data.zip
~~~
{: .bash}

>## `output`
> <asciinema-player font-size="medium" poster="npt:0:1" rows="16" src="{{ page.root }}/assets/asciinema/00-01-getdata.json">
> </asciinema-player>
>
{: .asciinema}

In the lesson, you will find out how to access and manipulate the data in this folder.  
