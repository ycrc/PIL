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

It should look something like this: REPLACE

![Terminal App](https://www.imore.com/sites/imore.com/files/styles/larger/public/field/image/2016/02/say-terminal-command-screenshot.jpg)

In order to connect to your virtual machine, you'll want to type something like

~~~
$ ssh user@host.yale.edu
~~~
{: .bash}

You will then be prompted to enter your password.

### Windows
The simplest way to use ssh on windows is with [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty). You can download an installer
by clicking [here](https://the.earth.li/~sgtatham/putty/latest/x86/putty-0.67-installer.msi).

When you open putty.exe, you should see a window like this:

![Putty window]({{ page.root }}/assets/img/putty.png)

Type the host name into the "Host Name (or IP address)" box and click open. You will be prompted for your username and password.

### Sample Files

Feel free to download a copy of the sample files on the computer in front of you, but in order to follow along, you need to download the files on the remote computer.

Copy the lines below and paste them into your terminal window. To paste in putty, right click the mouse in the window. In Terminal use <kbd>⌘</kbd> + <kbd>v</kbd>

~~~
wget https://brevans.github.io/PIL/data/PIL-data.zip
unzip PIL-data.zip
~~~
{: .bash}

>## Playback
> <script type="text/javascript" src="https://asciinema.org/a/290be69rt5nwph2cpq8gjitvt.js"
> id="asciicast-99527" data-size="small" async></script>
>
{: .solution}

In the lesson, you will find out how to access the data in this folder.  
