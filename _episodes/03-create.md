---
title: "Working With Files and Directories"
teaching: 15
exercises: 0
questions:
- "How can I create, copy, and delete files and directories?"
- "How can I edit files?"
objectives:
- "Create a directory hierarchy that matches a given diagram."
- "Create files in that hierarchy using an editor or by copying and renaming existing files."
- "Display the contents of a directory using the command line."
- "Delete specified files and/or directories."
keypoints:
- "`cp old new` copies a file."
- "`mkdir path` creates a new directory."
- "`mv old new` moves (renames) a file or directory."
- "`rm path` removes (deletes) a file."
- "`rmdir path` removes (deletes) an empty directory."
- "Use of the Control key may be described in many ways, including `Control-X`, <kbd>CTRL</kbd>+<kbd>X</kbd>, and `^X`."
- "The shell does not have a trash bin: once something is deleted, it's really gone."
- "Nano is a very simple text editor: please use something else for real work."
---

We now know how to explore files and directories,
but how do we create them in the first place?
Let's go back to our `PIL-data` directory
and use `ls -F` to see what it contains:

~~~
$ pwd
$ ls -F
~~~
{: .bash}

>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-01-pwdls.json">
> </asciinema-player>
>
{: .asciinema}

## **Make a Directory**

Let's create a new directory called `thesis` using the command `mkdir thesis`
(which has no output):

~~~
$ mkdir thesis
$ ls -F
~~~
{: .bash}

>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-02-mkdir.json">
> </asciinema-player>
>
{: .asciinema}

As you might guess from its name,
`mkdir` means "make directory".
Since `thesis` is a relative path
(i.e., doesn't have a leading slash),
the new directory is created in the current working directory.

> ## Good names for files and directories
>
> Complicated names of files and directories can make your life very painful
> when working on the command line. Here we provide a few useful
> tips for the names of your files from now on.
>
>  **1. Don't use whitespaces.**
>
>    White spaces can make a name more meaningful
>    but since whitespace is used to break arguments on the command line
>    is better to avoid them on name of files and directories.
>    You can use `-` or `_` instead of whitespace.
>
>
>  **2. Don't begin the name with `-` (dash).**
>
> Commands treat names starting with `-` as options.
>
>  **3. Stick with letters, numbers, `.` (period), `-` (dash) and `_` (underscore).**
>
>    Many other characters have a special meaning on the command line
>    that we will learn during this lesson. Some will only make your command not work,
>    but some of them may even cause you to lose some data!
>
> If you need to refer to names of files or directories that have whitespace
> or another non-alphanumeric character, you should surround the name in quotes (`""`).
{: .callout}

Since we've just created the `thesis` directory, there's nothing in it yet. Lets go there:

~~~
$ ls -F thesis
$ cd thesis
~~~
{: .bash}
>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-03-cdthesis.json">
> </asciinema-player>
>
{: .asciinema}

## **Edit Some Text**
Let's run a text editor called Nano to create a file called `draft.txt`.

> ## Which Editor?
>
> When we say, "`nano` is a text editor," we really do mean "text": it can
> only work with plain character data, not tables, images, or any other
> human-friendly media. We use it in examples because almost anyone can
> drive it anywhere without training, but please use something more
> powerful for real work. On Linux systems (such as Linux and Mac OS X),
> many programmers use [Emacs](http://www.gnu.org/software/emacs/) or
> [Vim](http://www.vim.org/) (both of which are take some time to learn),
> or a graphical editor such as [Gedit](http://projects.gnome.org/gedit/).
> On Windows, you may wish to use [Notepad++](http://notepad-plus-plus.org/).
>
{: .callout}

~~~
$ nano draft.txt
~~~
>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-04-nano.json">
> </asciinema-player>
>
{: .asciinema}

Let's type in a few lines of text.
Once we're happy with our text, we can press <kbd>CTRL</kbd>+<kbd>O</kbd>
(press the Ctrl or Control key and, while
holding it down, press the O key) to write our data to disk
(we'll be asked what file we want to save this to:
press Return to accept the suggested default of `draft.txt`).

Once our file is saved, we can use <kbd>CTRL</kbd>+<kbd>X</kbd> to quit the editor and
return to the shell.

> ## Control, Ctrl, or ^ Key
>
> The Control key is also called the "Ctrl" key. There are various ways
> in which using the Control key may be described. For example, you may
> see an instruction to press the Control key and, while holding it down,
> press the X key, described as any of:
>
> * `Control-X`
> * `Control+X`
> * `Ctrl-X`
> * `Ctrl+X`
> * `^X`
>
> In nano, along the bottom of the screen you'll see `^G Get Help ^O WriteOut`.
> This means that you can use <kbd>CTRL</kbd>+<kbd>G</kbd> to get help and
> <kbd>CTRL</kbd>+<kbd>O</kbd> to save your
> file.
{: .callout}

## **Delete a File**

`nano` doesn't leave any output on the screen after it exits,
but `ls` now shows that we have created a file called `draft.txt`.
Let's tidy up by running `rm draft.txt`.This command removes files
(`rm` is short for "remove"). If we run `ls` again, its output is empty once more,
which tells us that our file is gone:

~~~
$ ls
$ rm draft.txt
$ ls
~~~
{: .bash}
>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-05-rmdraft.json">
> </asciinema-player>
>
{: .asciinema}

> ## Deleting Is Forever!
>
> The Linux shell doesn't have a trash bin that we can recover deleted
> files from (though most graphical interfaces to Linux do).  Instead,
> when we delete files, they are unhooked from the file system so that
> their storage space on disk can be recycled. Tools for finding and
> recovering deleted files do exist, but there's no guarantee they'll
> work in any particular situation, since the computer may recycle the
> file's disk space right away.
{: .callout}

Let's re-create that file
and then move up one directory to `/home/nelle/data-shell` using `cd ..`:

~~~
$ pwd
$ nano draft.txt
$ ls
$ cd ..
~~~
{: .bash}

>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-06-nanoagain.json">
> </asciinema-player>
>
{: .asciinema}

If we try to remove the entire `thesis` directory using `rm thesis`,
we get an error message:

~~~
$ rm thesis
~~~
{: .bash}

>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-07-rmoops.json">
> </asciinema-player>
>
{: .asciinema}

## **Delete Everything**
This happens because `rm` by default only works on files, not directories.

To really get rid of `thesis` we must also delete the file `draft.txt`.
We can do this with the [recursive](https://en.wikipedia.org/wiki/Recursion) option for `rm`:

> ## With Great Power Comes Great Responsibility
>
> Removing the files in a directory recursively can be a very dangerous operation.
> If we're concerned about what we might be deleting we can
> add the "interactive" flag `-i` to `rm` which will ask us for confirmation
> before each step
>
> ~~~
> $ rm -r -i thesis
> ~~~
> {: .bash}
>
> > ## `output`
> > <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-08-rmi.json"></asciinema-player>
> >
> {: .asciinema}
>
> This removes everything in the directory, then the directory itself, asking
> at each step for you to confirm the deletion.
{: .callout}

Let's create that directory and file one more time.
(Note that this time we're running `nano` with the path `thesis/draft.txt`,
rather than going into the `thesis` directory and running `nano` on `draft.txt` there.)

~~~
$ mkdir thesis
$ nano thesis/draft.txt
$ ls
$ ls thesis
~~~
{: .bash}

>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-09-nanoagainagain.json">
> </asciinema-player>
>
{: .asciinema}

## **Move a File**
`draft.txt` isn't a particularly informative name,
so let's change the file's name using `mv`,
which is short for "move":

~~~
$ mv thesis/draft.txt thesis/quotes.txt
$ ls thesis
~~~
{: .bash}
>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-10-mv.json">
> </asciinema-player>
>
{: .asciinema}

The first parameter tells `mv` what we're "moving",
while the second is where it's to go.
In this case,
we're moving `thesis/draft.txt` to `thesis/quotes.txt`,
which has the same effect as renaming the file.
Sure enough,
`ls` shows us that `thesis` now contains one file called `quotes.txt`:

One has to be careful when specifying the target file name, since **`mv` will
silently overwrite any existing file with the same name**, which could
lead to data loss. An additional flag, `mv -i` (or `mv --interactive`),
can be used to make `mv` ask you for confirmation before overwriting.

Just for the sake of consistency,
`mv` also works on directories --- there is no separate `mvdir` command.

Let's move `quotes.txt` into the current working directory.
We use `mv` once again,
but this time we'll just use the name of a directory as the second parameter
to tell `mv` that we want to keep the filename,
but put the file somewhere new.
(This is why the command is called "move".)
In this case,
the directory name we use is the special directory name `.` that we mentioned earlier.
The effect is to move the file from the directory it was in to the current working directory.
`ls` now shows us that `thesis` is empty:

~~~
$ mv thesis/quotes.txt .
$ ls thesis
$ ls
~~~
{: .bash}
>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-11-mvup.json">
> </asciinema-player>
>
{: .asciinema}

## **Copy a File**

The `cp` command works very much like `mv`,
except it copies a file instead of moving it.
We can check that it did the right thing using `ls`
with two paths as parameters. Unlike some Linux commands,
`ls` can be given multiple paths at once:

~~~
$ cp quotes.txt thesis/quotations.txt
$ ls . thesis/
~~~
{: .bash}
>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-12-cp.json">
> </asciinema-player>
>
{: .asciinema}

To prove that we made a copy,
let's delete the `quotes.txt` file in the current directory
and then run that same `ls` again.

~~~
$ rm quotes.txt
$ ls quotes.txt thesis/quotations.txt
~~~
{: .bash}
>## `output`
> <asciinema-player rows="16" src="{{ page.root }}/assets/asciinema/03-13-rmquotes.json">
> </asciinema-player>
>
{: .asciinema}

We won't find `quotes.txt` in the current directory,
but copy in `thesis` that we didn't delete remains.

> ## What's In A Name?
>
> You may have noticed that all of Nelle's files' names are "something dot
> something", and in this part of the lesson, we always used the extension
> `.txt`.  This is just a convention: we can call a file `mythesis` or
> almost anything else we want. However, most people use two-part names
> most of the time to help them (and their programs) tell different kinds
> of files apart. The second part of such a name is called the
> **filename extension**, and indicates
> what type of data the file holds: `.txt` signals a plain text file, `.pdf`
> indicates a PDF document, `.cfg` is a configuration file full of parameters
> for some program or other, `.png` is a PNG image, and so on.
>
> This is just a convention, albeit an important one. Files contain
> bytes: it's up to us and our programs to interpret those bytes
> according to the rules for plain text files, PDF documents, configuration
> files, images, and so on.
>
> Naming a PNG image of a whale as `whale.mp3` doesn't somehow
> magically turn it into a recording of whalesong, though it *might*
> cause the operating system to try to open it with a music player
> when someone double-clicks it.
{: .callout}

> ## Renaming Files
>
> Suppose that you created a `.txt` file in your current directory to contain a list of the
> statistical tests you will need to do to analyze your data, and named it: `statstics.txt`
>
> After creating and saving this file you realize you misspelled the filename! You want to
> correct the mistake, which of the following commands could you use to do so?
>
> 1. `cp statstics.txt statistics.txt`
> 2. `mv statstics.txt statistics.txt`
> 3. `mv statstics.txt .`
> 4. `cp statstics.txt .`
>
> > ## Solution
> > 1. No.  While this would create a file with the correct name, the incorrectly named file still exists in the directory
> > and would need to be deleted.
> > 2. Yes, this would work to rename the file.
> > 3. No, the period(.) indicates where to move the file, but does not provide a new file name; identical file names
> > cannot be created.
> > 4. No, the period(.) indicates where to copy the file, but does not provide a new file name; identical file names
> > cannot be created.
> {: .solution}
{: .challenge}

> ## Moving and Copying
>
> What is the output of the closing `ls` command in the sequence shown below?
>
> ~~~
> $ pwd
> ~~~
> {: .bash}
> ~~~
> /home/jamie/data
> ~~~
> {: .output}
> ~~~
> $ ls
> ~~~
> {: .bash}
> ~~~
> proteins.dat
> ~~~
> {: .output}
> ~~~
> $ mkdir recombine
> $ mv proteins.dat recombine
> $ cp recombine/proteins.dat ../proteins-saved.dat
> $ ls
> ~~~
> {: .bash}
>
> 1.   `proteins-saved.dat recombine`
> 2.   `recombine`
> 3.   `proteins.dat recombine`
> 4.   `proteins-saved.dat`
>
> > ## Solution
> > We start in the `/home/jamie/data` directory, and create a new folder called `recombine`.
> > The second line moves (`mv`) the file `proteins.dat` to the new folder (`recombine`).
> > The third line makes a copy of the file we just moved.  The tricky part here is where the file was
> > copied to.  Recall that `..` means "go up a level", so the copied file is now in `/home/jamie`.
> > Notice that `..` is interpreted with respect to the current working
> > directory, **not** with respect to the location of the file being copied.
> > So, the only thing that will show using ls (in `/home/jamie/data`) is the recombine folder.
> >
> > 1. No, see explanation above.  `proteins-saved.dat` is located at `/home/jamie`
> > 2. Yes
> > 3. No, see explanation above.  `proteins.dat` is located at `/home/jamie/data/recombine`
> > 4. No, see explanation above.  `proteins-saved.dat` is located at `/home/jamie`
> {: .solution}
{: .challenge}

> ## Organizing Directories and Files
>
> Jamie is working on a project and she sees that her files aren't very well
> organized:
>
> ~~~
> $ ls -F
> ~~~
> {: .bash}
> ~~~
> analyzed/  fructose.dat    raw/   sucrose.dat
> ~~~
> {: .output}
>
> The `fructose.dat` and `sucrose.dat` files contain output from her data
> analysis. What command(s) covered in this lesson does she need to run so that the commands below will
> produce the output shown?
>
> ~~~
> $ ls -F
> ~~~
> {: .bash}
> ~~~
> analyzed/   raw/
> ~~~
> {: .output}
> ~~~
> $ ls analyzed
> ~~~
> {: .bash}
> ~~~
> fructose.dat    sucrose.dat
> ~~~
> {: .output}
{: .challenge}

> ## Copy with Multiple Filenames
>
> What does `cp` do when given several filenames and a directory name, as in:
>
> ~~~
> $ mkdir backup
> $ cp thesis/citations.txt thesis/quotations.txt backup
> ~~~
> {: .bash}
>
> What does `cp` do when given three or more filenames, as in:
>
> ~~~
> $ ls -F
> ~~~
> {: .bash}
> ~~~
> intro.txt    methods.txt    survey.txt
> ~~~
> {: .output}
> ~~~
> $ cp intro.txt methods.txt survey.txt
> ~~~
> {: .bash}
{: .challenge}

> ## Listing Recursively and By Time
>
> The command `ls -R` lists the contents of directories recursively,
> i.e., lists their sub-directories, sub-sub-directories, and so on
> in alphabetical order at each level.
> The command `ls -t` lists things by time of last change,
> with most recently changed files or directories first.
> In what order does `ls -R -t` display things?
{: .challenge}

> ## Creating Files a Different Way
>
> We have seen how to create text files using the `nano` editor.
> Now, try the following command in your home directory:
>
> ~~~
> $ cd                  # go to your home directory
> $ touch my_file.txt
> ~~~
> {: .bash}
>
> 1.  What did the touch command do?
>     When you look at your home directory using the GUI file explorer,
>     does the file show up?
>
> 2.  Use `ls -l` to inspect the file's.  How large is `my_file.txt`?
>
> 3.  When might you want to create a file this way?
{: .challenge}

> ## Moving to the Current Folder
>
> After running the following commands,
> Jamie realizes that she put the files `sucrose.dat` and `maltose.dat` into the wrong folder:
>
> ~~~
> $ ls -F
> raw/ analyzed/
> $ ls -F analyzed
> fructose.dat glucose.dat maltose.dat sucrose.dat
> $ cd raw/
> ~~~
> {: .bash}
>
> Fill in the [blanks] to move these files to the current folder
> (i.e., the one she is currently in):
>
> ~~~
> $ mv [blank]/sucrose.dat  [blank]/maltose.dat [blank]
> ~~~
> {: .bash}
> > ## Solution
> > ~~~
> > $ mv ../analyzed/sucrose.dat  ../analyzed/maltose.dat .
> > ~~~
> >
> {: .solution}
{: .challenge}

> ## Using `rm` Safely
>
> What happens when we type `rm -i thesis/quotations.txt`?
> Why would we want this protection when using `rm`?
>
> > ## Solution
> >
> > Ask for confirmation.
> {: .solution}
{: .challenge}

> ## Copy a folder structure sans files
>
> You're starting a new experiment, and would like to duplicate the file
> structure from your previous experiment without the data files so you can
> add new data.
>
> Assume that the file structure is in a folder called '2016-05-18-data',
> which contains folders named 'raw' and 'processed' that contain data files.
> The goal is to copy the file structure of the `2016-05-18-data` folder
> into a folder called `2016-05-20-data` and remove the data files from
> the directory you just created.
>
> Which of the following set of commands would achieve this objective?
> What would the other commands do?
>
> ~~~
> $ cp -r 2016-05-18-data/ 2016-05-20-data/
> $ rm 2016-05-20-data/data/raw/*
> $ rm 2016-05-20-data/data/processed/*
> ~~~
> {: .bash}
> ~~~
> $ rm 2016-05-20-data/data/raw/*
> $ rm 2016-05-20-data/data/processed/*
> $ cp -r 2016-05-18-data/ 2016-5-20-data/
> ~~~
> {: .bash}
> ~~~
> $ cp -r 2016-05-18-data/ 2016-05-20-data/
> $ rm -r -i 2016-05-20-data/
> ~~~
> {: .bash}
{: .challenge}
