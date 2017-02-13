---
layout: page
title: Setup
permalink: /setup/
---

If you want to follow along today, you'll need to connect to a remote computer.
This will be accomplished with a cryptographic network protocol called ssh.

### Find your Host!

We'll be connecting to virtual computers hosted here at Yale to follow along
with the exercises today. In order to find the name and address of yours:

*  Log into [spinup.internal.yale.edu](https://spinup.internal.yale.edu/) using CAS.

*  Click on Sandbox, or the link for the space listed in your "spaces"

* Make note of the resource name listed. It will look something like
`netid@spinup-######.yu.yale.edu` **This is your host name**.


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

Where you replace netid with your netid and the `#`'s with the host name you
found for yourself by logging into
[spinup.internal.yale.edu](https://spinup.internal.yale.edu/)

You may be asked for the password you use to log into mac, then you'll be asked
for the password for `netid@spinup-######.yu.yale.edu`, which is your
netid password.

### Windows
The simplest way to use ssh on windows is with [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty). You can download an installer
by clicking [here](https://the.earth.li/~sgtatham/putty/latest/x86/putty-0.67-installer.msi).

When you open putty.exe, you should see a window like this:

![Putty window]({{ page.root }}/assets/img/putty.png)

Type the host name (`spinup-######.yu.yale.edu`) into the "Host Name
(or IP address)" box and click open. You will be prompted for your
username and password. Your username is your netid and your password is your
netid password.

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
