---
title: "The Command Line Interface"
teaching: 60
exercises: 30
questions:
- "How to use the Linux terminal"
objectives:
- "Learn the basic commands"
keypoints:
- "Learn the basic commands"
---

### Command Line Interface

At a high level, a HPC cluster is a big computer to be used by several users at the same time. The users expect to run a variety of scientific codes, store the data needed as input or generated as output. In HPC, computers usually communicate with each other for tasks that are too big for a single computer to deal and interact with us allowing us to make decisions and see errors.

Our interaction with computers happens in many different ways,
including through a keyboard and mouse, touch screen interfaces, or using speech recognition systems. However in HPC we need an efficient and still very light way of communicating with the head node. The front end machine in a HPC cluster. In contrast Desktop computers uses a Graphical User Interface.


The **graphical user interface** (GUI) is the most widely used way to interact with personal computers. We give instructions (to run a program, to copy a file, to create a new folder/directory) with the convenience of a few mouse clicks. This way of interacting with a computer is intuitive and very easy to learn. But this way of giving instructions to a computer scales very poorly if we are to give a large stream of instructions even if they are similar or identical. For example if we have to copy the third line of each of a thousand text files stored in thousand different directories and paste it into a single file line by line. Using the traditional GUI approach of clicks will take several hours to do this.

This is where we take advantage of the shell - a **command-line interface** to make such repetitive tasks automatic and fast. It can take a single instruction and repeat it as is or with some modification as many times as we want. The task in the example above can be accomplished in a few minutes at most.

The heart of a command-line interface is a **read-evaluate-print loop** (REPL). It is called so because when you type a command and press <kbd>Return</kbd> (also known as <kbd>Enter</kbd>) the shell
reads your command, evaluates (or "executes") it, prints the output of your command, loops back and waits for you to enter another command.

### The Shell


The Shell is a program which runs other programs rather than doing calculations itself.
Those programs can be as complicated as climate modeling software and as simple as a
program that creates a new directory. The simple programs which are used to perform
stand alone tasks are usually refered to as commands.
The most popular Unix shell is Bash, (the Bourne Again SHell --- so-called because
it's derived from a shell written by Stephen Bourne).
Bash is the default shell on most modern implementations of Unix
and in most packages that provide Unix-like tools for Windows.


When the shell is first opened, you are presented with a **prompt**,
indicating that the shell is waiting for input.

~~~
$
~~~
{: .language-bash}

The shell typically uses `$ ` as the prompt, but may use a different symbol.
We'll show the prompt in several ways, mostly as `$ ` but you can see other versions like `$> ` or `[training001@srih0001 ~]$ `. The last one is the default prompt for the user training001 at the Spruce head node.
Most importantly: when typing commands, either from these lessons or from other sources, *do not type the prompt*, only the commands that follow it.

So let's try our first command, which will list the contents of the current directory:

~~~
[training001@srih0001 ~]$ ls -al
~~~
{: .language-bash}
~~~
total 64
drwx------   4 training001 training   512 Jun 27 13:24 .
drwxr-xr-x 151 root        root     32768 Jun 27 13:18 ..
-rw-r--r--   1 training001 training    18 Feb 15  2017 .bash_logout
-rw-r--r--   1 training001 training   176 Feb 15  2017 .bash_profile
-rw-r--r--   1 training001 training   124 Feb 15  2017 .bashrc
-rw-r--r--   1 training001 training   171 Jan 22  2018 .kshrc
drwxr-xr-x   4 training001 training   512 Apr 15  2014 .mozilla
drwx------   2 training001 training   512 Jun 27 13:24 .ssh
~~~
{: .output}

> ## Command not found
> If the shell can't find a program whose name is the command you typed, it
> will print an error message such as:
>
> ~~~
> $ ks
> ~~~
> {: .language-bash}
> ~~~
> ks: command not found
> ~~~
> {: .output}
>
> Usually this means that you have mis-typed the command.
{: .callout}

### Why use the CLI?

The Command Line Interface was one of the first ways of interacting with computers. Previously the interaction happened with perforated cards or even switching cables on a big console. Still the CLI is a powerful way of talking with computers.

It is a different model of interacting than a GUI, and that will take some effort - and some time - to learn. A GUI presents you with choices and you select one. With a **command line interface** (CLI) the choices are combinations of commands and parameters, more like words in a language than buttons on a screen. They are not presented to you so you must learn a few, like learning some vocabulary in a new language. But a small number of commands gets you a long way, and we'll cover those essential few today.

### Flexibility and automation

The grammar of a shell allows you to combine existing tools into powerful
pipelines and handle large volumes of data automatically. Sequences of
commands can be written into a *script*, improving the reproducibility of
workflows and allowing you to repeat them easily.

In addition, the command line is often the easiest way to interact with remote machines and supercomputers.
Familiarity with the shell is near essential to run a variety of specialized tools and resources
including high-performance computing systems.
As clusters and cloud computing systems become more popular for scientific data crunching,
being able to interact with the shell is becoming a necessary skill.
We can build on the command-line skills covered here
to tackle a wide range of scientific questions and computational challenges.

## Exercise 1

Commands in Unix/Linux are very stable with some commands being around for decades now. So what your learn will be of good use in the future. This exercises pretend to give you a feeling of the different parts of a command.

Execute the command `cal`, we executed that in our previous episode. Execute it again like this `cal -y`. You should get an output like this:

~~~
[training001@srih0001 ~]$ cal -y
~~~
{: .language-bash}
~~~
                               2019                               

       January               February                 March       
Su Mo Tu We Th Fr Sa   Su Mo Tu We Th Fr Sa   Su Mo Tu We Th Fr Sa
       1  2  3  4  5                   1  2                   1  2
 6  7  8  9 10 11 12    3  4  5  6  7  8  9    3  4  5  6  7  8  9
13 14 15 16 17 18 19   10 11 12 13 14 15 16   10 11 12 13 14 15 16
20 21 22 23 24 25 26   17 18 19 20 21 22 23   17 18 19 20 21 22 23
27 28 29 30 31         24 25 26 27 28         24 25 26 27 28 29 30
                                              31
        April                   May                   June        
Su Mo Tu We Th Fr Sa   Su Mo Tu We Th Fr Sa   Su Mo Tu We Th Fr Sa
    1  2  3  4  5  6             1  2  3  4                      1
 7  8  9 10 11 12 13    5  6  7  8  9 10 11    2  3  4  5  6  7  8
14 15 16 17 18 19 20   12 13 14 15 16 17 18    9 10 11 12 13 14 15
21 22 23 24 25 26 27   19 20 21 22 23 24 25   16 17 18 19 20 21 22
28 29 30               26 27 28 29 30 31      23 24 25 26 27 28 29
                                              30
        July                  August                September     
Su Mo Tu We Th Fr Sa   Su Mo Tu We Th Fr Sa   Su Mo Tu We Th Fr Sa
    1  2  3  4  5  6                1  2  3    1  2  3  4  5  6  7
 7  8  9 10 11 12 13    4  5  6  7  8  9 10    8  9 10 11 12 13 14
14 15 16 17 18 19 20   11 12 13 14 15 16 17   15 16 17 18 19 20 21
21 22 23 24 25 26 27   18 19 20 21 22 23 24   22 23 24 25 26 27 28
28 29 30 31            25 26 27 28 29 30 31   29 30

       October               November               December      
Su Mo Tu We Th Fr Sa   Su Mo Tu We Th Fr Sa   Su Mo Tu We Th Fr Sa
       1  2  3  4  5                   1  2    1  2  3  4  5  6  7
 6  7  8  9 10 11 12    3  4  5  6  7  8  9    8  9 10 11 12 13 14
13 14 15 16 17 18 19   10 11 12 13 14 15 16   15 16 17 18 19 20 21
20 21 22 23 24 25 26   17 18 19 20 21 22 23   22 23 24 25 26 27 28
27 28 29 30 31         24 25 26 27 28 29 30   29 30 31
~~~
{: .output}

The command line is powerful enough to allow you to even do programming.
Execute this command and see the answer

~~~
[training001@srih0001 ~]$ n=1; while test $n -lt 10000; do echo $n; n=`expr 2 \* $n`; done
~~~
{: .language-bash}
~~~
1
2
4
8
16
32
64
128
256
512
1024
2048
4096
8192
~~~
{: .output}

If you are not getting this output check the command line very carefully. Even small changes could be interpreted by the shell as entirely different commands so you need to be extra careful and gather insight when commands are not doing what you want.

The `echo` and `cat` commands
-----------------------------

Your fist command will show you what those locations are. Execute:

~~~
$> echo $HOME
/users/<username>
$> echo $SCRATCH
/scratch/<username>
~~~
{: .output}

The first command to learn is `echo`. The command above uses `echo` to
show the contents of two shell variables `$HOME` and `$SCRATCH`. Shell
variables are ways to store information in such a way that the shell can
use it when needed. Each user on the cluster receives appropriated
values for those variables.

Let us explore a bit more the usage of `echo`. Enter this command line
and execute `ENTER`:

~~~
$> echo "I am learning UNIX Commands"
~~~
{: .language-bash}
~~~
I am learning UNIX Commands
~~~
{: .output}

The shell is actually able to do basic arithmetical operations, execute
this command:

~~~
$> echo $((23+45*2))
~~~
{: .language-bash}
~~~
113
~~~
{: .output}

Notice that as customary in mathematics products take precedence over
addition. That is called the PEMDAS order of operations, ie
\"Parentheses, Exponents, Multiplication and Division, and Addition and
Subtraction\". Check your understanding of the PEMDAS rule with this
command:

~~~
$> echo $(((1+2**3*(4+5)-7)/2+9))
~~~
{: .language-bash}
~~~
42
~~~
{: .output}

Notice that the exponential operation is expressed with the `**`
operator. The usage of `echo` is important, otherwise, if you execute
the command without `echo` the shell will do the operation and will try
to execute a command called `42` that does not exist on the system. Try
by yourself:

~~~
$> $ $(((1+2**3*(4+5)-7)/2+9))
~~~
{: .language-bash}
~~~
-bash: 42: command not found
~~~
{: .output}

As you have seen before, when you execute a command on the terminal in
most cases you see the output printed on the screen. The next thing to
learn is how to redirect the output of a command into a file. This will
be very important later to submit jobs and control where and how the
output is produced. Execute the following command:

~~~
$> echo "I am learning UNIX Commands" > report.log
~~~
{: .language-bash}

With the character `>` redirects the output from `echo` into a file
called *report.log*. No output is printed on the screen. If the file
does not exist it will be created. If the file exists previously, the
file is erased and only the new contents are stored.

To check that the file actually contains the line produced by echo,
execute:

~~~
$> cat report.log
~~~
{: .language-bash}
~~~
I am learning UNIX Commands
~~~
{: .output}

The cat (concatenate) command displays the contents of one or several
files. In the case of multiple files the files are printed in the order
they are described in the command line, concatenating the output so the
name of the command.

You can even use a nice trick to write a small text on a file. Execute
the following command, followed by the text that you want to write, at
the end execute `Ctrl-D` (`^D`), the *Control Key* followed by the `D`
key. I am annotating below the location where `^D` should be executed:

~~~
$> cat > report.log
I am learning UNIX Commands^D
$> cat report.log
I am learning UNIX Commands
~~~
{: .language-bash}

In fact, there are hundreds of commands, most of them with a variety of
options that change the behavior of the original command. You can feel
bewildered at first by a large number of existing commands, but in fact
most of the time you will be using a very small number of them.
Learning those will speed up your learning curve.

Another very simple command that is very useful in HPC is `date`.
Without any arguments, it prints the current date to the screen.
Example:

~~~
$> date
~~~
{: .language-bash}
~~~
Mon Nov  5 12:05:58 EST 2018
~~~
{: .output}

Folder commands
---------------

As we mentioned before, UNIX organizes data in storage devices as a
tree. The commands `pwd`, `cd` and `mkdir` will allow you to know where
you are, move your location on the tree and create new folders. Later we
will see how to move folders from one location on the tree to another.

The first command is `pwd`. Just execute the command on the terminal:

~~~
$> $ pwd
~~~
{: .language-bash}
~~~
/users/<username>
~~~
{: .output}

It is very important at all times to know where in the tree you are.
Doing research usually involves dealing with an important amount of
data, exploring several parameters or physical conditions. Organizing all the data
properly in meaningful folders is very important to
research endeavors.

When you log into a cluster, by default you are located on your `$HOME`
folder. That is why most likely the command `pwd` will return that
location in the first instance.

The next command is `cd`. This command is used to *change directory*.
The directory is another name for *folder*. The term *directory* is also
widely used. At least in UNIX the terms *directory* and *folder* are
exchangeable. Other Desktop Operating Systems like Windows and MacOS
have the concept of *smart folders* or *virtual folders*, where the
*folder* that you see on screen has no correlation with a directory in
the filesystem. In those cases the distinction is relevant.

There is another important folder defined in our clusters, its called
the scratch folder and each user has its own. The location of the folder
is stored in the variable `$SCRATCH`. Notice that this is internal
convection and is not observed in other HPC clusters.

Use the next command to go to that folder:

~~~
$> cd $SCRATCH
$> pwd
~~~
{: .language-bash}
~~~
/scratch/<username>
~~~
{: .output}

Notice that the location is different now, if you are using this account
for the first time you will not have files on this folder. It is time to
learn another command to list the contents of a *folder*, execute:

~~~
$> ls
$>
~~~
{: .language-bash}

Assuming that you are using your HPC account for the first time, you
will not have anything on your `$SCRATCH` folder. This is a good
opportunity to start creating one folder there and change your location
inside, execute:

~~~
$> mkdir test_folder
$> cd test_folder
~~~
{: .language-bash}

We have use two new commands here, `mkdir`allows you to create folders
in places where you are authorized to do so. For example your `$HOME`
and `$SCRATCH` folders. Try this command:

~~~
$> mkdir /test_folder
~~~
{: .language-bash}
~~~
mkdir: cannot create directory `/test_folder': Permission denied
~~~
{: .output}

There is an important difference between `test_folder` and
`/test_folder`. The former is a location in your current working
directory (CWD), the later is a location starting on the root directory
`/`. A normal user has no rights to create folders on that directory so
`mkdir` will fail and an error message will be shown on your screen.

The name of the folder is `test_folder`, notice the underscore between
*test* and *folder*. In UNIX, there is no restriction having files or
directories with spaces but using them become a nuisance on the command
line. If you want to create the folder with spaces from the command
line, here are the options:

~~~
$> mkdir "test folder with spaces"
$> mkdir another\ test\ folder\ with\ spaces
~~~
{: .language-bash}

In any case, you have to type extra characters to prevent the command
line application of considering those spaces as separators for several
arguments in your command. Try executing the following:

~~~
$> mkdir another folder with spaces
$> ls
~~~
{: .language-bash}
~~~
another folder with spaces  folder  spaces  test_folder  test folder with spaces  with
~~~
{: .output}

Maybe is not clear what is happening here. There is an option for `ls`
that present the contents of a directory:

~~~
$>ls -l
~~~
{: .language-bash}
~~~
total 0
drwxr-xr-x 2 myname mygroup 512 Nov  2 15:44 another
drwxr-xr-x 2 myname mygroup 512 Nov  2 15:45 another folder with spaces
drwxr-xr-x 2 myname mygroup 512 Nov  2 15:44 folder
drwxr-xr-x 2 myname mygroup 512 Nov  2 15:44 spaces
drwxr-xr-x 2 myname mygroup 512 Nov  2 15:45 test_folder
drwxr-xr-x 2 myname mygroup 512 Nov  2 15:45 test folder with spaces
drwxr-xr-x 2 myname mygroup 512 Nov  2 15:44 with
~~~
{: .output}

It should be clear, now what happens when the spaces are not contained
in quotes `"test folder with spaces"` or escaped as
`another\ folder\ with\ spaces`. This is the perfect opportunity to
learn how to delete empty folders. Execute:

~~~
$> rmdir another
$> rmdir folder spaces with
~~~
{: .language-bash}

You can delete one or several folders, but all those folders must be
empty. If those folders contain files or more folders, the command will
fail and an error message will be displayed.

After deleting those folders created by mistake, let\'s check the
contents of the current directory. The command `ls -1` will list the
contents of a file one per line, something very convenient for future
scripting:

~~~
$> ls -1
~~~
{: .language-bash}
~~~
another folder with spaces
test_folder
test folder with spaces
~~~
{: .output}

Commands for copy and move
--------------------------

The next two commands are `cp` and `mv`. They are used to copy or move
files or folders from one location to another. In its simplest usage,
those two commands take two arguments, the first argument is the source
and the last one the destination. In the case of more than two
arguments, the destination must be a directory. The effect will be to
copy or move all the source items into the folder indicated as the
destination.

Before doing a few examples with `cp` and `mv`let\'s use a very handy
command to create files. The command `touch` is used to update the
access and modification times of a file or folder to the current time.
In case there is not such a file, the command will create a new empty
file. We will use that feature to create some empty files for the
purpose of demonstrating how to use `cp` and `mv`.

Lets create a few files and directories:

~~~
$> mkdir even odd
$> touch f01 f02 f03 f05 f07 f11
~~~
{: .language-bash}

Now, lets copy some of those existing files to complete all the numbers
up to `f11`:

~~~
$> cp f03 f04
$> cp f05 f06
$> cp f07 f08
$> cp f07 f09
$> cp f07 f10
~~~
{: .language-bash}

This is good opportunity to present the `*` *wildcard*, use it to
replace an arbitrary sequence of characters. For instance, execute this
command to list all the files created above:

~~~
$> ls f*
~~~
{: .language-bash}
~~~
f01  f02  f03  f04  f05  f06  f07  f08  f09  f10  f11
~~~
{: .output}

The *wildcard* is able to replace zero or more arbitrary characters, see
for example:

~~~
$> ls f*1
~~~
{: .language-bash}
~~~
f01  f11
~~~
{: .output}

There is another way of representing files or directories that follow a
pattern, execute this command:

~~~
$> ls f0[3,5,7]
~~~
{: .language-bash}
~~~
f03  f05  f07
~~~
{: .output}

The files selected are those whose last character is on the list
`[3,5,7]`. Similarly, a range of characters can be represented. See:

~~~
$> ls f0[3-7]
~~~
{: .language-bash}
~~~
f03  f04  f05  f06  f07
~~~
{: .output}

We will use those special character to move files based on its parity.
Execute:

~~~
$> mv f[0,1][1,3,5,7,9] odd
$> mv f[0,1][0,2,4,6,8] even
~~~
{: .language-bash}

The command above is equivalent to execute the explicit listing of
sources:

~~~
$> mv f01 f03 f05 f07 f09 f11 odd
$> mv f02 f04 f06 f08 f10 even
~~~
{: .language-bash}

Delete files and Folders
------------------------

As we mentioned above, empty folders can be deleted with the command
`rmdir` but that only works if there are no subfolders or files inside
the folder that you want to delete. See for example what happens if you
try to delete the folder called `odd`:

~~~
$> rmdir odd
~~~
{: .language-bash}
~~~
rmdir: failed to remove `odd': Directory not empty
~~~
{: .output}

If you want to delete odd, you can do it in two ways. The command
`rm`allows you to delete one or more files entered as arguments. Let\'s
delete all the files inside odd, followed by the deletion of the folder
`odd` itself:

~~~
$> rm odd/*
$> rmdir odd
~~~
{: .language-bash}

Another option is to delete a folder recursively, this is a powerful but
also dangerous option. Even if deleting a file is not actually filling
with zeros the location of the data, on HPC systems the recovery of data
is practice unfeasible. Let\'s delete the folder even recursively:

~~~
$> rm -r even
~~~
{: .language-bash}

Summary of Basic Commands
-------------------------

The purpose of this brief tutorial is to familiarize you with the most
common commands used in UNIX environments. We have shown 10 commands
that you will be using, very often on your interaction. This 10 basic
commands and one editor from the next section is all that you need to be
ready for submitting jobs on the cluster.

The next table summarizes those commands.


| Command | Description       | Examples                     |
|---------|:------------------|:-----------------------------|
| `echo`  | Display a given message on the screen | `$> echo "This is a message"` |
|---------|-------------------|------------------------------|
| `cat`   | Display the contents of a file on screen <br> Concatenate files | `$> cat my_file` |
|---------|-------------------|------------------------------|
| `date`  | Shows the current date on screen | `$> date` <br> Wed Nov 7 10:40:05 EST 2018 |
|---------|-------------------|------------------------------|
| `pwd`   | Return the path to the current working directory | `$> pwd` <br> /users/username                  |
|---------|-------------------|------------------------------|
| `cd`    | Change directory  | `$> cd sub_folder`           |
|---------|-------------------|------------------------------|
| `mkdir` | Create directory  | `$> mkdir new_folder`        |
|---------|-------------------|------------------------------|
| `touch` | Change the access and modification time of a file <br> Create empty files     | `$> touch new_file` |
|---------|-------------------|------------------------------|
| `cp`    | Copy a file in another location <br> Copy several files into a destination directory  | `$> cp old_file new_file`  |
|---------|-------------------|------------------------------|
| `mv`    | Move a file in another location <br> Move several files into a destination folder | `$> mv old_name new_name`  |
|---------|-------------------|------------------------------|
| `rm`    | Remove one or more files from the file system tree | `$> rm trash_file` <br> `$> rm -r full_folder`         |
|---------|-------------------|------------------------------|

## Exercise 1

Create two folders called `one` and `two`.
On each one of them create one empty file. On the folder "one" the file will be like `none1` and on `two` the file should be `none2`.

Create also on those two folders, files `date1` and `date2` using the command `date` and output redirection `>` so for example for `date1` the command should be like this:

~~~
$> date > date1
~~~
{: .language-bash}

Check with `cat` that those file actually contain dates.

Now, create a couple of folders `empty_files` and `dates` and move the corresponding files `none1` and `none2` to `empty_files` and do the same for `date1` and `date2`.

The folders `one` and `two` should be empty now, delete them with `rmdir`
Do the same with folders `empty_files` and `dates`

{% include links.md %}

