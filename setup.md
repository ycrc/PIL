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
> | spinup-000528.yu.yale.edu | 10.5.32.185 | amd243   |
> | spinup-00050e.yu.yale.edu | 10.5.32.27  | arh42    |
> | spinup-000523.yu.yale.edu | 10.5.32.20  | boydenlm |
> | spinup-000514.yu.yale.edu | 10.5.33.109 | Cdg44    |
> | spinup-00050f.yu.yale.edu | 10.5.33.254 | cdy6     |
> | spinup-000520.yu.yale.edu | 10.5.32.97  | chd23    |
> | spinup-00051f.yu.yale.edu | 10.5.35.239 | cj283    |
> | spinup-00052a.yu.yale.edu | 10.5.35.177 | cm792    |
> | spinup-00051e.yu.yale.edu | 10.5.34.104 | ea327    |
> | spinup-00051b.yu.yale.edu | 10.5.35.123 | fws7     |
> | spinup-000516.yu.yale.edu | 10.5.34.207 | gc397    |
> | spinup-000525.yu.yale.edu | 10.5.34.204 | gcd9     |
> | spinup-000531.yu.yale.edu | 10.5.33.43  | hc468    |
> | spinup-000530.yu.yale.edu | 10.5.32.85  | ia85     |
> | spinup-00052d.yu.yale.edu | 10.5.35.44  | jb2428   |
> | spinup-00051c.yu.yale.edu | 10.5.33.55  | jeb247   |
> | spinup-00052b.yu.yale.edu | 10.5.35.156 | jm3244   |
> | spinup-000524.yu.yale.edu | 10.5.35.200 | jrm236   |
> | spinup-00051d.yu.yale.edu | 10.5.32.208 | meh68    |
> | spinup-000529.yu.yale.edu | 10.5.34.99  | mm3327   |
> | spinup-000511.yu.yale.edu | 10.5.32.100 | mz294    |
> | spinup-000522.yu.yale.edu | 10.5.34.3   | nr267    |
> | spinup-000517.yu.yale.edu | 10.5.34.243 | pc576    |
> | spinup-000513.yu.yale.edu | 10.5.32.88  | pg336    |
> | spinup-000521.yu.yale.edu | 10.5.32.8   | pjk38    |
> | spinup-000512.yu.yale.edu | 10.5.32.5   | py64     |
> | spinup-000532.yu.yale.edu | 10.5.35.40  | sd755    |
> | spinup-00051a.yu.yale.edu | 10.5.33.192 | sh773    |
> | spinup-00050d.yu.yale.edu | 10.5.34.109 | sjd25    |
> | spinup-000527.yu.yale.edu | 10.5.35.28  | sk2478   |
> | spinup-00052c.yu.yale.edu | 10.5.34.76  | ssb54    |
> | spinup-00052e.yu.yale.edu | 10.5.34.31  | sy266    |
> | spinup-000510.yu.yale.edu | 10.5.35.159 | wr225    |
> | spinup-00052f.yu.yale.edu | 10.5.33.117 | wx36     |
> | spinup-000518.yu.yale.edu | 10.5.35.36  | xw273    |
> | spinup-000515.yu.yale.edu | 10.5.35.174 | yh345    |
> | spinup-000519.yu.yale.edu | 10.5.33.42  | yz435    |
> | spinup-000526.yu.yale.edu | 10.5.35.22  | zop2     |
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
