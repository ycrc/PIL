---
layout: page
title: Setup
permalink: /setup/
---

[![Yale Spinup]({{ page.root }}/assets/img/spinup_logo_word.png)](https://spinup.internal.yale.edu/)

We'll be connecting to virtual computers hosted in the cloud for you for the purposes of this course.
After we finish today, feel free to spin up your own virtual machine at Yale by logging in to [spinup.internal.yale.edu](https://spinup.internal.yale.edu/) using CAS from anywhere on campus or via VPN.

### Find your Host!
If you want to follow along today, you'll need to connect to a remote computer.
This will be accomplished with a cryptographic network protocol called ssh.

*Make note of the resource name listed below. If you do not see your netid please ask for help.*

> ## Hostnames
>
> | Host Name                 | IP address  | NetID    |
> |---------------------------|-------------|----------|
> | spinup-0006c4.yu.yale.edu | 10.5.33.89 | boydenlm |
> | spinup-0006c5.yu.yale.edu | 10.5.34.132 | seh88 |
> | spinup-0006c6.yu.yale.edu | 10.5.35.246 | dh462 |
> | spinup-0006c7.yu.yale.edu | 10.5.35.206 | ebb36 |
> | spinup-0006c8.yu.yale.edu | 10.5.33.252 | ls957 |
> | spinup-0006c9.yu.yale.edu | 10.5.32.58 | sjt39 |
> | spinup-0006ca.yu.yale.edu | 10.5.34.87 | dz259 |
> | spinup-0006cb.yu.yale.edu | 10.5.35.12 | hy283 |
> | spinup-0006cc.yu.yale.edu | 10.5.34.213 | lrs44 |
> | spinup-0006cd.yu.yale.edu | 10.5.32.80 | ab2822 |
> | spinup-0006ce.yu.yale.edu | 10.5.34.117 | sl2524 |
> | spinup-0006cf.yu.yale.edu | 10.5.35.59 | wz262 |
> | spinup-0006d0.yu.yale.edu | 10.5.35.196 | rc832 |
> | spinup-0006d1.yu.yale.edu | 10.5.32.12 | dt485 |
> | spinup-0006d2.yu.yale.edu | 10.5.35.66 | mf573 |
> | spinup-0006d3.yu.yale.edu | 10.5.35.219 | dee2 |
> | spinup-0006d4.yu.yale.edu | 10.5.33.150 | ldb28 |
> | spinup-0006d5.yu.yale.edu | 10.5.32.194 | wh334 |
> | spinup-0006d6.yu.yale.edu | 10.5.32.233 | xl493 |
> | spinup-0006d7.yu.yale.edu | 10.5.34.225 | sh2352 |
> | spinup-0006d9.yu.yale.edu | 10.5.33.167 | sa828 |
> | spinup-0006da.yu.yale.edu | 10.5.32.118 | cq39 |
> | spinup-0006db.yu.yale.edu | 10.5.35.103 | kyw5 |
> | spinup-0006dc.yu.yale.edu | 10.5.33.30 | zc263 |
>
{: .solution}

### Mac OSX / macOS
If you are on a mac, you already have ssh. All you need to do is open up your terminal app.
To open the terminal app, you can navigate to your apps then utilities directory and double click on its icon, or use spotlight to find it.

It should look something like this:

![Terminal App]({{ page.root }}/assets/img/macterm.png)

In order to connect to your virtual machine, you'll want to type something like

~~~
$ ssh netid@spinup-######.yu.yale.edu
~~~
{: .bash}

Replace "netid" with your netid and the `#`'s with the host name listed above

You may also be asked for the password you use to log into your mac.
Once that is entered, you'll be asked for the password for
`netid@spinup-######.yu.yale.edu`, which is your netid password.

### Windows
The simplest way to use ssh on windows is with [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty). You can download an installer
by [clicking here](https://the.earth.li/~sgtatham/putty/latest/x86/putty-0.67-installer.msi).

When you open putty.exe, you should see a window like this:

![Putty window]({{ page.root }}/assets/img/putty.png)

Type your host name from above (`spinup-######.yu.yale.edu`) into the "Host Name
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
