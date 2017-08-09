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
> | spinup-00064b.yu.yale.edu | 10.5.35.199 | rla35 |
> | spinup-00064c.yu.yale.edu | 10.5.34.80 | kem225 |
> | spinup-00064d.yu.yale.edu | 10.5.33.52 | ry87 |
> | spinup-00064e.yu.yale.edu | 10.5.32.155 | dd698 |
> | spinup-00064f.yu.yale.edu | 10.5.32.29 | arh42 |
> | spinup-000650.yu.yale.edu | 10.5.32.28 | bms53 |
> | spinup-000651.yu.yale.edu | 10.5.35.202 | rd557 |
> | spinup-000652.yu.yale.edu | 10.5.35.45 | jx98 |
> | spinup-000653.yu.yale.edu | 10.5.34.175 | dl784 |
> | spinup-000654.yu.yale.edu | 10.5.35.144 | cma78 |
> | spinup-000655.yu.yale.edu | 10.5.33.107 | djt25 |
> | spinup-000656.yu.yale.edu | 10.5.35.137 | hh468 |
> | spinup-000657.yu.yale.edu | 10.5.35.43 | ed473 |
> | spinup-000658.yu.yale.edu | 10.5.33.133 | nr267 |
> | spinup-000659.yu.yale.edu | 10.5.35.135 | jos23 |
> | spinup-00065a.yu.yale.edu | 10.5.35.152 | hs679 |
> | spinup-00065b.yu.yale.edu | 10.5.32.63 | aa768 |
> | spinup-00065c.yu.yale.edu | 10.5.34.191 | yl553 |
> | spinup-00065d.yu.yale.edu | 10.5.33.4 | jw597 |
> | spinup-00065e.yu.yale.edu | 10.5.34.230 | amc294 |
> | spinup-00065f.yu.yale.edu | 10.5.32.108 | mt52 |
> | spinup-000660.yu.yale.edu | 10.5.35.100 | sg998 |
> | spinup-000661.yu.yale.edu | 10.5.34.97 | ts747 |
> | spinup-000662.yu.yale.edu | 10.5.33.112 | ta363 |
> | spinup-000663.yu.yale.edu | 10.5.33.74 | wg89 |
> | spinup-000664.yu.yale.edu | 10.5.33.185 | mas384 |
> | spinup-000665.yu.yale.edu | 10.5.33.188 | ls957 |
> | spinup-000666.yu.yale.edu | 10.5.34.43 | jmh45 |
> | spinup-000667.yu.yale.edu | 10.5.35.9 | arh42 |
> | spinup-000668.yu.yale.edu | 10.5.34.58 | rd557 |
> | spinup-000669.yu.yale.edu | 10.5.32.173 | eberhart |
> | spinup-00066a.yu.yale.edu | 10.5.32.233 | ym267 |
> | spinup-00066b.yu.yale.edu | 10.5.33.79 | yx265 |
> | spinup-00066c.yu.yale.edu | 10.5.35.115 | lag48 |
> | spinup-00066d.yu.yale.edu | 10.5.35.157 | pw374 |
> | spinup-00066e.yu.yale.edu | 10.5.34.226 | dh462 |
> | spinup-00066f.yu.yale.edu | 10.5.32.121 | ae388 |
> | spinup-000670.yu.yale.edu | 10.5.34.216 | lr579 |
> | spinup-000671.yu.yale.edu | 10.5.33.100 | amc294 |
> | spinup-000672.yu.yale.edu | 10.5.32.196 | dl785 |
> | spinup-000673.yu.yale.edu | 10.5.34.107 | sn334 |
> | spinup-000674.yu.yale.edu | 10.5.33.10 | dfl28 |
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
