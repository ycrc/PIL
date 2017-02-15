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

*Make note of the resource name listed below. I you do not see your netid please ask for help.*

> ## Hostnames
>
> | Hostname                  | netid  |
> |---------------------------|--------|
> | spinup-00041a.yu.yale.edu | ab2772 |
> | spinup-0003fd.yu.yale.edu | adj24  |
> | spinup-00040a.yu.yale.edu | agt24  |
> | spinup-0003ed.yu.yale.edu | agw27  |
> | spinup-000377.yu.yale.edu | aj478  |
> | spinup-000373.yu.yale.edu | ajm229 |
> | spinup-0003e8.yu.yale.edu | amc266 |
> | spinup-0003fb.yu.yale.edu | asg48  |
> | spinup-0003e7.yu.yale.edu | asm87  |
> | spinup-00040f.yu.yale.edu | asm87  |
> | spinup-000379.yu.yale.edu | ba352  |
> | spinup-000418.yu.yale.edu | be59   |
> | spinup-000413.yu.yale.edu | cdt25  |
> | spinup-0003f0.yu.yale.edu | cdy6   |
> | spinup-000402.yu.yale.edu | clh64  |
> | spinup-00041e.yu.yale.edu | db934  |
> | spinup-0003f7.yu.yale.edu | dbs58  |
> | spinup-000378.yu.yale.edu | dd698  |
> | spinup-000403.yu.yale.edu | dgb9   |
> | spinup-0003ee.yu.yale.edu | dk659  |
> | spinup-00040e.yu.yale.edu | ea327  |
> | spinup-00040b.yu.yale.edu | ef426  |
> | spinup-00041c.yu.yale.edu | enc24  |
> | spinup-0003ff.yu.yale.edu | fg223  |
> | spinup-000372.yu.yale.edu | fjd27  |
> | spinup-0003e6.yu.yale.edu | fn32   |
> | spinup-0003ef.yu.yale.edu | gac6   |
> | spinup-000417.yu.yale.edu | gjy3   |
> | spinup-00040d.yu.yale.edu | hew25  |
> | spinup-000406.yu.yale.edu | hz65   |
> | spinup-0003f5.yu.yale.edu | ia85   |
> | spinup-000407.yu.yale.edu | jj574  |
> | spinup-0003e4.yu.yale.edu | jpd67  |
> | spinup-00041b.yu.yale.edu | jrm236 |
> | spinup-000409.yu.yale.edu | jx98   |
> | spinup-000412.yu.yale.edu | jz574  |
> | spinup-00037a.yu.yale.edu | khp6   |
> | spinup-000405.yu.yale.edu | kjc37  |
> | spinup-0003f9.yu.yale.edu | les67  |
> | spinup-0003fa.yu.yale.edu | lg583  |
> | spinup-0003f6.yu.yale.edu | map95  |
> | spinup-000414.yu.yale.edu | mh839  |
> | spinup-0003fc.yu.yale.edu | mo455  |
> | spinup-0003eb.yu.yale.edu | ms3477 |
> | spinup-000411.yu.yale.edu | msm223 |
> | spinup-000401.yu.yale.edu | mt52   |
> | spinup-0003ec.yu.yale.edu | nb556  |
> | spinup-0003f8.yu.yale.edu | nym4   |
> | spinup-0003fe.yu.yale.edu | pg336  |
> | spinup-000369.yu.yale.edu | prd3   |
> | spinup-000376.yu.yale.edu | rc832  |
> | spinup-0003e5.yu.yale.edu | rc883  |
> | spinup-0003ea.yu.yale.edu | rr687  |
> | spinup-0003e9.yu.yale.edu | sej36  |
> | spinup-000374.yu.yale.edu | sl857  |
> | spinup-000371.yu.yale.edu | spm35  |
> | spinup-00040c.yu.yale.edu | sw838  |
> | spinup-0003f2.yu.yale.edu | sz243  |
> | spinup-0003f4.yu.yale.edu | ta375  |
> | spinup-00041d.yu.yale.edu | tc572  |
> | spinup-0003f3.yu.yale.edu | tem35  |
> | spinup-000408.yu.yale.edu | ts749  |
> | spinup-000415.yu.yale.edu | vn54   |
> | spinup-000416.yu.yale.edu | wc478  |
> | spinup-0003f1.yu.yale.edu | ytc5   |
> | spinup-000410.yu.yale.edu | yz435  |
> | spinup-000404.yu.yale.edu | zc83   |
> | spinup-000400.yu.yale.edu | zt74   |
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
