
# History

<b>Git</b> is a software for version control, mainly used for software development but it can be used to track and keep the history of any file type.
It was originally created by Linus Torvalds, the creator of the [[Linux Kernel]], in 2005 and since then the main maintainer of the project is Junio Hamano.
It's written primarily in [[C]] but it has some GUI and programming scrips written in Shell Script, Perl, TcL and Python.
It's a command line based tool although it does have support for [[GIT Gui]] which is a community managed project that develops loads and loads of options for the user but the most well known of them is [[GitHub]].

___


# Installation

Through the official Git [website](https://git-scm.com/downloads) download the most recent version and download the one for your operating system and install it.
After that you pretty much settled to start using Git.

### Troubleshooting

If you're on windows and you get the message `git is not recognized in the system` you'll need to add some variables to the environment variables in your system.

```
C:\Program Files\Git\cmd\
```
and
```
C:\Program Files\Git\bin\
```

___

# Commands

Anyone can start using Git with some simple commands

`git init` -> Make an existing directory into a git repository

`git clone [url]` -> Copies an entire repository from the URL given

`git config --global user.name "firstname lastname"` -> sets a name to identify in the history

`git config --global user.email [email]` -> sets a name to identify in the history

`git config --global color.ui auto` -> sets automatic command line coloring for Git

`git status` -> show modified files in the working directory

`git add [file]` -> stages a file for the next commit

`git reset [file]` -> unstage a file for the next commit

`git diff --staged` -> diff of what is staged but not yet commited

`git commit -m "[message]"` -> commit your staged content as a new commit snapshot

`git push` -> Transmits commits to the branch of the repository 




