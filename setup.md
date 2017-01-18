---
layout: page
title: Setup
permalink: /setup/
---

If you want to follow along today, you'll need to connect to a remote computer.
This will be accomplished with a cryptographic network protocol called ssh.

### Mac OSX / macOS
If you are on a mac, you already have an implementation of ssh, so all you need to do is open up your terminal app.
To open the terminal app, you can navigate to your apps then utilities directory and double click on its icon, or use spotlight to find it.

It should look something like this:

![Terminal App]({{ page.root }}/assets/img/macterm.png)

In order to connect to your virtual machine, you'll want to type something like

~~~
$ ssh netid@spinup-######.yu.yale.edu
~~~
{: .bash}

(We'll show you how to find your specific hostname.)

### Windows
The simplest way to use ssh on windows is with [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty). You can download an installer
by clicking [here](https://the.earth.li/~sgtatham/putty/latest/x86/putty-0.67-installer.msi).

When you open putty.exe, you should see a window like this:

![Putty window]({{ page.root }}/assets/img/putty.png)

Type the host name (`spinup-######.yu.yale.edu`) into the "Host Name (or IP address)" box and click open. You will be prompted for your username and password. (We'll show you how to find your specific hostname.)

### Sample Files

Feel free to download a copy of the sample files on the computer in front of you, but in order to follow along, you need to download the files on the remote computer.

Copy the lines below and paste them into your terminal window. To paste in putty, right click the mouse in the window. In Terminal use <kbd>⌘</kbd> + <kbd>v</kbd>

~~~
wget https://brevans.github.io/PIL/data/PIL-data.zip
unzip PIL-data.zip
~~~
{: .bash}

>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/00-01-getdata.json">
> </asciinema-player>
>
{: .asciinema}

In the lesson, you will find out how to access and manipulate the data in this folder.  
