---
title: "Shell Scripts"
teaching: 25
exercises: 0
questions:
- "How can I save and re-use commands?"
objectives:
- "Write a shell script that runs a command or series of commands for a fixed set of files."
- "Run a shell script from the command line."
- "Write a shell script that operates on a set of files defined by the user on the command line."
- "Create pipelines that include shell scripts you, and others, have written."
keypoints:
- "Save commands in files (usually called shell scripts) for re-use."
- "`bash filename` runs the commands saved in a file."
- "`$@` refers to all of a shell script's command-line parameters."
- "`$1`, `$2`, etc., refer to the first command-line parameter, the second command-line parameter, etc."
- "Place variables in quotes if the values might have spaces in them."
- "Letting users decide what files to process is more flexible and more consistent with built-in Linux commands."
---

We are finally ready to see what makes the shell such a powerful programming environment.
We are going to take the commands we repeat frequently and save them in files
so that we can re-run all those operations again later by typing a single command.
For historical reasons, a bunch of commands saved in a file is usually called
a **shell script**, but make no mistake: these are actually small programs.

Let's start by going back to `molecules/` and putting the following line into a
new file, `middle.sh`:

~~~
$ cd molecules
$ nano middle.sh
~~~
{: .bash}

The command `nano middle.sh` opens the file `middle.sh` within the text editor "nano"
(which runs within the shell).
If the file does not exist, it will be created.
We can use the text editor to directly edit the file---we'll simply insert the following line:

~~~
head -n 15 octane.pdb | tail -n 5
~~~
{: .source}

>## `output`
> <asciinema-player font-size="medium" poster="npt:0:1" rows="16" src="{{ page.root }}/assets/asciinema/06-01-middlesh.json">
> </asciinema-player>
>
{: .asciinema}

This is a variation on the pipe we constructed earlier:
it selects lines 11-15 of the file `octane.pdb`.
Remember, we are *not* running it as a command just yet:
we are putting the commands in a file.

Then we save the file (<kbd>CTRL</kbd>+<kbd>O</kbd> in nano),
 and exit the text editor (<kbd>CTRL</kbd>+<kbd>X</kbd> in nano).
Check that the directory `molecules` now contains a file called `middle.sh`.

Once we have saved the file,
we can ask the shell to execute the commands it contains.
Our shell is called `bash`, so we run the following command:

~~~
$ bash middle.sh
~~~
{: .bash}

>## `output`
> <asciinema-player font-size="medium" poster="npt:0:1" rows="16" src="{{ page.root }}/assets/asciinema/06-02-runmiddle.json">
> </asciinema-player>
>
{: .asciinema}

Sure enough,
our script's output is exactly what we would get if we ran that pipeline directly.

> ## Text vs. Whatever
>
> Programs like Microsoft Word or LibreOffice Writer are *word processors*. They
> include a lot more than just text in `.docx` and `.odt` files in order to show
> you the fancy layout and format that they do. We need to be a bit more
> careful when it comes to programming. Tools like `head` expect input files
> to contain nothing but the letters, digits, and punctuation.
> When editing programs, therefore, you should stick to a
> plain text editor.
{: .callout}

What if we want to select lines from an arbitrary file?
We could edit `middle.sh` each time to change the filename,
but that would probably take longer than just retyping the command.
Instead, let's edit `middle.sh` and make it more versatile:

~~~
$ nano middle.sh
~~~
{: .bash}

Now, within "nano", replace the text `octane.pdb` with the special variable called `$1`:

~~~
head -n 15 "$1" | tail -n 5
~~~
{: .output}

Inside a shell script,
`$1` means "the first filename (or other parameter) on the command line".
We can now run our script like this:

~~~
$ bash middle.sh octane.pdb
~~~
{: .bash}

>## `output`
> <asciinema-player font-size="medium" poster="npt:0:1" rows="16" src="{{ page.root }}/assets/asciinema/06-03-runmiddlearb.json">
> </asciinema-player>
>
{: .asciinema}

or on a different file like this:

~~~
$ bash middle.sh pentane.pdb
~~~
{: .bash}

>## `output`
> <asciinema-player font-size="medium" poster="npt:0:1" rows="16" src="{{ page.root }}/assets/asciinema/06-04-runmiddlepentane.json">
> </asciinema-player>
>
{: .asciinema}

> ## Double-Quotes Around Arguments
>
> In case the filename happens to contain any spaces,it is good practice to
> surround `$1` with double-quotes.
{: .callout}

We still need to edit `middle.sh` each time we want to adjust the range of lines,
though. Let's fix that by using the special variables `$2` and `$3` for the
number of lines to be passed to `head` and `tail` respectively:

~~~
$ nano middle.sh
~~~
{: .bash}

~~~
head -n "$2" "$1" | tail -n "$3"
~~~
{: .output}

We can now run:

~~~
$ bash middle.sh pentane.pdb 15 5
~~~
{: .bash}

>## `output`
> <asciinema-player font-size="medium" poster="npt:0:1" rows="16" src="{{ page.root }}/assets/asciinema/06-05-runmiddlearblines.json">
> </asciinema-player>
>
{: .asciinema}

By changing the arguments to our command we can change our script's
behaviour:

~~~
$ bash middle.sh pentane.pdb 20 5
~~~
{: .bash}

>## `output`
> <asciinema-player font-size="medium" poster="npt:0:1" rows="16" src="{{ page.root }}/assets/asciinema/06-06-runmiddlediffnums.json">
> </asciinema-player>
>
{: .asciinema}

This works,
but it may take the next person who reads `middle.sh` a moment to figure out what it does.
We can improve our script by adding some **comments** at the top:

~~~
$ nano middle.sh
~~~
{: .bash}

~~~
# Select lines from the middle of a file.
# Usage: bash middle.sh filename end_line num_lines
head -n "$2" "$1" | tail -n "$3"
~~~
{: .output}
>## `output`
> <asciinema-player font-size="medium" poster="npt:0:1" rows="16" src="{{ page.root }}/assets/asciinema/06-07-documentmiddle.json">
> </asciinema-player>
>
{: .asciinema}

A **comment** starts with a `#` character and runs to the end of the line.
The computer ignores comments, but they're invaluable for helping people
(including and possibly most importantly, your future self) understand and
use scripts. The only caveat is that each time you modify the script,
you should check that the comment is still accurate:
an explanation that sends the reader in the wrong
direction is worse than none at all.

What if we want to process many files in a single pipeline?
For example, if we want to sort our `.pdb` files by length, we would type:

~~~
$ wc -l *.pdb | sort -n
~~~
{: .bash}

because `wc -l` lists the number of lines in the files
(recall that `wc` stands for 'word count', adding the `-l` flag means 'count lines' instead)
and `sort -n` sorts things numerically.
We could put this in a file,
but then it would only ever sort a list of `.pdb` files in the current directory.
If we want to be able to get a sorted list of other kinds of files,
we need a way to get all those names into the script.
We can't use `$1`, `$2`, and so on
because we don't know how many files there are.
Instead, we use the special variable `$@`,
which means,
"All of the command-line parameters to the shell script."
We also should put `$@` inside double-quotes
to handle the case of parameters containing spaces
(`"$@"` is equivalent to `"$1"` `"$2"` ...)
Here's an example:

~~~
$ nano sorted.sh
~~~
{: .bash}

~~~
# Sort filenames by their length.
# Usage: bash sorted.sh one_or_more_filenames
wc -l "$@" | sort -n
~~~
{: .output}

~~~
$ bash sorted.sh *.pdb ../creatures/*.dat
~~~
{: .bash}

>## `output`
> <asciinema-player font-size="medium" poster="npt:0:1" rows="16" src="{{ page.root }}/assets/asciinema/06-08-sorted.json">
> </asciinema-player>
>
{: .asciinema}

> ## Why Isn't It Doing Anything?
>
> What happens if a script is supposed to process a bunch of files, but we
> don't give it any filenames? For example, what if we type:
>
> ~~~
> $ bash sorted.sh
> ~~~
> {: .bash}
>
> but don't say `*.dat` (or anything else)? In this case, `$@` expands to
> nothing at all, so the pipeline inside the script is effectively:
>
> ~~~
> $ wc -l | sort -n
> ~~~
> {: .bash}
>
> Since it doesn't have any filenames, `wc` assumes it is supposed to
> process standard input, so it just sits there and waits for us to give
> it some data interactively. From the outside, though, all we see is it
> sitting there: the script doesn't appear to do anything. To stop it we can use
> either the kill("STOP NOW") or end of file ("I'm all done!") control codes by typing
> <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>D</kbd>, respectively.
{: .callout}


Suppose we have just run a series of commands that did something useful --- for example,
that created a graph we'd like to use in a paper.
We'd like to be able to re-create the graph later if we need to,
so we want to save the commands in a file.
Instead of typing them in again (and potentially getting them wrong)
we can do this:

~~~
$ history | tail -n 5 > redo-figure-3.sh
~~~
{: .bash}

The file `redo-figure-3.sh` now contains:

~~~
297 bash goostats -r NENE01729B.txt stats-NENE01729B.txt
298 bash goodiff stats-NENE01729B.txt /data/validated/01729.txt > 01729-differences.txt
299 cut -d ',' -f 2-3 01729-differences.txt > 01729-time-series.txt
300 ygraph --format scatter --color bw --borders none 01729-time-series.txt figure-3.png
301 history | tail -n 5 > redo-figure-3.sh
~~~
{: .source}

After a moment's work in an editor to remove the serial numbers on the commands,
and to remove the final line where we called the `history` command,
we have a completely accurate record of how we created that figure.

In practice, most people develop shell scripts by running commands at the
shell prompt a few times to make sure they're doing the right thing,
then saving them in a file for re-use. This style of work allows
people to recycle what they discover about their data and their workflow
with one call to `history` and a bit of editing to clean up the output
and save it as a shell script.

## **Nelle's Pipeline: Creating a Script**

An off-hand comment from her supervisor has made Nelle realize that
she should have provided a couple of extra parameters to `goostats` when
she processed her files. This might have been a disaster if she had done all
the analysis by hand, but thanks to `for` loops, it will only take a couple
of hours to re-do (and that time is mostly computer work, not hers).

First she clears the old output:
~~~
$ rm stats-NENE0*
~~~
{: .bash}

Experience has taught her that if something needs to be done twice,
it will probably need to be done a third or fourth time as well.
She runs the editor and writes the following:

~~~
# Calculate reduced stats for data files at J = 100 c/bp.
for datafile in "$@"
do
    echo $datafile
    bash goostats -J 100 -r $datafile stats-$datafile
done
~~~
{: .bash}

(The parameters `-J 100` and `-r` are the ones her supervisor said she should have used.)
She saves this in a file called `do-stats.sh`
so that she can now re-do the first stage of her analysis by typing:

~~~
$ bash do-stats.sh *[AB].txt
~~~
{: .bash}

She can check the output with:

~~~
$ less stats-NENE01729A.txt
~~~
{: bash}

and quit less but typing <kbd>Q</kbd>

She can also do this:

~~~
$ bash do-stats.sh *[AB].txt | wc -l
~~~
{: .bash}
so that the output is just the number of files processed
rather than the names of the files that were processed.

>## `output`
> <asciinema-player font-size="medium" poster="npt:0:1" rows="16" src="{{ page.root }}/assets/asciinema/06-09-goorevisit.json">
> </asciinema-player>
>
{: .asciinema}

One thing to note about Nelle's script is that
it lets the person running it decide what files to process.
She could have written it as:

~~~
# Calculate reduced stats for  A and Site B data files at J = 100 c/bp.
for datafile in *[AB].txt
do
    echo $datafile
    bash goostats -J 100 -r $datafile stats-$datafile
done
~~~
{: .bash}

The advantage is that this always selects the right files:
she doesn't have to remember to exclude the 'Z' files.
The disadvantage is that it *always* selects just those files ---
she can't run it on all files (including the 'Z' files),
or on the 'G' or 'H' files her colleagues in Antarctica are producing,
without editing the script. If she wanted to be more adventurous,
she could modify her script to check for command-line parameters,
and use `*[AB].txt` if none were provided. Of course, this introduces another
tradeoff between flexibility, complexity, and her time.

> ## Variables in Shell Scripts
>
> In the `molecules` directory, imagine you have a shell script called `script.sh` containing the
> following commands:
>
> ~~~
> head -n $2 $1
> tail -n $3 $1
> ~~~
> {: .bash}
>
> While you are in the `molecules` directory, you type the following command:
>
> ~~~
> $ bash script.sh '*.pdb' 1 1
> ~~~
> {: .bash}
>
> Which of the following outputs would you expect to see?
>
> 1. All of the lines between the first and the last lines of each file ending in `.pdb`
>    in the `molecules` directory
> 2. The first and the last line of each file ending in `.pdb` in the `molecules` directory
> 3. All of the first, then all of the last lines of each file ending in `.pdb`
> in the `molecules` directory
> 4. The first and the last line of each file in the `molecules` directory
> 5. An error because of the quotes around `*.pdb`
>
> >## Solution
> >
> > 3
> >
> {: .solution}
{: .challenge}

> ## List Unique Species
>
> Leah has several hundred data files, each of which is formatted like this:
>
> ~~~
> 2013-11-05,deer,5
> 2013-11-05,rabbit,22
> 2013-11-05,raccoon,7
> 2013-11-06,rabbit,19
> 2013-11-06,deer,2
> 2013-11-06,fox,1
> 2013-11-07,rabbit,18
> 2013-11-07,bear,1
> ~~~
> {: .output}
>
> Write a shell script called `species.sh` that takes any number of
> filenames as command-line parameters, and uses `cut`, `sort`, and
> `uniq` to print a list of the unique species appearing in each of
> those files separately.
>
> > ## Solution
> > example species.sh:
> > ~~~
> > for $filename in $@
> > do
> >     echo "### $filename ###"
> >     cut -d , -f 2 $filename | sort | uniq
> >     echo "### $filename ###"
> > done
> > ~~~
> > {: .bash}
> {: .solution}
{: .challenge}

> ## Find the Longest File With a Given Extension
>
> Write a shell script called `longest.sh` that takes the name of a
> directory and a filename extension as its parameters, and prints
> out the name of the file with the most lines in that directory
> with that extension. For example:
>
> ~~~
> $ bash longest.sh /tmp/data pdb
> ~~~
> {: .bash}
>
> would print the number of lines and name of the `.pdb` file in `/tmp/data`
> that has the most lines.
>
> > ## Solution
> > example longest.sh:
> > ~~~
> > wc -l ${1}/*.${2} | sort -rn | head -n 2 | tail -n 1
> > ~~~
> > {: .bash}
> {: .solution}
{: .challenge}

> ## Script Reading Comprehension
>
> Joel's `data` directory contains three files: `fructose.dat`,
> `glucose.dat`, and `sucrose.dat`. Explain what a script called
> `example.sh` would do when run as `bash example.sh *.dat` if it
> contained the following lines:
>
> ~~~
> # Script 1
> echo *.*
> ~~~
> {: .bash}
>
> ~~~
> # Script 2
> for filename in $1 $2 $3
> do
>     cat $filename
> done
> ~~~
> {: .bash}
>
> ~~~
> # Script 3
> echo $@.dat
> ~~~
> {: .bash}
>
> > ## Solution
> >
> > Script 1 output:
> > ~~~
> > example.sh fructose.dat  glucose.dat  sucrose.dat
> > ~~~
> > {: .output}
> >
> > Script 2 output:
> > ~~~
> > #All the data in fructose.dat, glucose.dat, and sucrose.dat
> > ~~~
> > {: .output}
> >
> > Script 3 output:
> > ~~~
> > fructose.dat glucose.dat sucrose.dat.dat
> > ~~~
> > {: .output}
> >
> {: .solution}
{: .challenge}

> ## Debugging Scripts
>
> Suppose you have saved the following script in a file called `do-errors.sh`
> in Nelle's `north-pacific-gyre/2012-07-03` directory:
>
> ~~~
> # Calculate reduced stats for data files at J = 100 c/bp.
> for datafile in "$@"
> do
>     echo $datfile
>     bash goostats -J 100 -r $datafile stats-$datafile
> done
> ~~~
> {: .bash}
>
> When you run it:
>
> ~~~
> $ bash do-errors.sh *[AB].txt
> ~~~
> {: .bash}
>
> the output is blank.
> To figure out why, re-run the script using the `-x` option:
>
> ~~~
> bash -x do-errors.sh *[AB].txt
> ~~~
> {: .bash}
>
> What is the output showing you?
> Which line is responsible for the error?
>
> > ## Solution
> >
> > You'll see a "trace" of what bash is executing. Notice that echo isn't
> > echoing anything? That's because we never defined a variable called
> > `datfile`, so bash just evaluates that to nothing.
> >
> {: .solution}
{: .challenge}
