---
layout: post
current: post
cover: assets/images/zsh-homer-simpson.png
navigation: True
title: How to be a Real Computer Science Major
date: 2018-10-16
tags: [terminal]
class: post-template
subclass: 'post tag-terminal'
author: swapneel
---

This post focuses on how to modify/hack your terminal with different plugins such that you can make Homer Simpson spout meaningful software engineering quotes on launching it.

*Note: This post contains a healthy dose of sarcasm.*

**Most of this article can be represented by this meme.**

![Computer Science Major - Z Shell, Oh-My-Zsh, Terminal](assets/images/cs-meme.jpeg)
Expectations are aplenty when you study Computer Science

In this case, however, we are going to bring alive the *What I think I do* part. We’re going to pump our terminals full of steroids and make it spout pointless nonsense that — to the non-CS folk— makes us look like we know what we are doing. 

**And we will do this in less than 30 minutes, starting now.**

>Didn’t see that coming, did ya?


## The Terminal

The essence of most work we do as programmers boils down to a simple aspect of our lives — the terminal. Sure, we have graphical user interfaces (GUIs) that make life easier for the non-geeks among us, but the mark of a true Computer Science Major is that you have spent 4 long years learning how to open and operate the terminal.

>If you wish to open the GUIs, instead of doing it visually by clicking on the icon, open a terminal and type the command that launches the GUI. I guarantee you will feel greater satisfaction about being a CS major than you currently do.

On a more serious note, until a while ago I realized most of us seriously under-utilise the terminal at the early stages in our career (and also look extremely uncool doing it). We could use a pointer from the people who have spent years working on this stuff just to help noobs (such as myself) feel much better about being geeks.

>So you’re using a Linux distro (or Mac OSX)? That’s awesome. But you’re still using the plain old bash terminal? Probably something that looks like this.

![The Bourne Again Shell or Bash](assets/images/good-old-bash.png)
Good old Bash :’)

>Or you’ve become a programmer and modified the default profile to something that is actually colorful. Good job. In that case, you’re looking at something of this sort.

![Homebrew has Profiles for the Terminal](assets/images/homebrew-profiles.png)
Homebrew has profiles that you can activate ([Photo Credit](www.jejemaes.net))

**What if I told you that you can get from these terminals to this next one in a matter of about 29.7 minutes (average case, varies with innate geekiness quotient).**

![The Awesome Terminal](assets/images/awesome-terminal.png)
The “OMFG THAT LOOKS AWESOME” Terminal

**Ladies and Gentlemen, I present to you, the Z Shell.**

The idea is basically to use a bunch of plugins and themes that help you modify your terminal into a beautiful piece of art that you want to stare at all day long. There’s also the added functionality like auto-completion, command history, but that’s less important (editor's note: *sarcasm*).

>Just look at how pretty it is.

The short explanation is just as you have your default bash shell, you have a version of this that has been customised via plugins and themes that make it much easier to code, navigate, and generally exist in the terminal (as most real programmers do).

>As history goes, the Z Shell was brought to earth by angels that wanted to enable Artificial Intelligence to take over the world decades before the Rosetta Stone prophesied it would.

>Show me, Master.

Okay, fine. Now that you’ve made it until this part, I’m going to share the codebase that enables you to do this to your terminal. I’ve added customisations for your Vim text editor as well in case you want a change in scene from Sublime Text 3 (the decision to switch comes with the added bonus of looking much geekier than ever before). Have at it!

Here’s your Stairway to Heaven.

**[DotFiles](https://github.com/SwapneelM/dotfiles)**

**Now before you jump to it, I’ve added a considerable amount of theoretical explanations underpinning the files/code that you’re modifying. Do yourself a favor and go through these to avoid destroying your system configurations (just kidding, or am I?).**

(editor's note:*he was not kidding*)

# Dotfiles 

**What exactly are dotfiles?**

**tl;dr**
- Configuration files on unix, or 'dotfiles', often begin with a dot. For example, .vimrc stores your vim settings, .bashrc stores your bash settings, etc.

- In UNIX file systems, dotfiles are text-based configurations files that stores settings of almost every application, service and tool running on your system. These files control the behavior of applications from boot to termination and everything in between. People create backups and elaborate setups of their dotfiles and often share them on GitHub or other code hosting platforms. Helping them setup, their systems faster and restore their configurations when needed.

### .bashrc / .bash_profile / .zshrc / .vimrc

- These files are basically used to define environment variables and append paths that you would require for installed applications. When you run `source ~/.bashrc`, you are just refreshing the definitions of the variables in the file. The same goes for your `~/.bash_profile` or `~/.zshrc` folder.

- In the case of your `.vimrc` file, it contains specific configurations for settings and plugins that are used when you open your text editor with the `vi` command. Each time you modify it, you probably need to shut and reopen the vim editor to refresh those settings. There are also ways to do it from within vim (without shutting it) such as `:so %`. 
Reference: [How to reload .vimrc without shutting vim](https://superuser.com/questions/132029/how-do-you-reload-your-vimrc-file-without-restarting-vim#132030)

Stack Overflow: [The difference between .bashrc, .bash_profile, .environment](https://stackoverflow.com/questions/415403/whats-the-difference-between-bashrc-bash-profile-and-environment)

- You copy the same `.vimrc` file and rename it to `init.vim` for your Neovim to use (it must lie within `~/.config/nvim`). But you get that it is the same idea - define custom settings in an `rc` file and then `source` it whenever necessary.

**Why do we need them?**

Now, imagine I destroy your laptop in a way that the data can’t ever be recovered. (Pretty dark, right?) and ask you to restore all your little shortcuts, tweaks, and settings that you took hours to configure in your applications. An impossible task. Not really. This is actually where dotfiles come in, these nifty text files that you save, contain thousands of key-value pairs defining each and every aspect of your applications. You can restore your system back to that point in a matter of minutes. (answer by Vipul Gupta)

Quora: [What are dotfiles](https://www.quora.com/What-are-dotfiles)

### sh 
- sh (or the Shell Command Language) is a programming language described by the POSIX standard. It has many implementations (ksh88, dash, ...). bash can also be considered an implementation of sh. Because sh is a specification, not an implementation, /bin/sh is a symlink (or a hard link) to an actual implementation (such as bash) on most POSIX systems. 

### bash
- bash started as an sh-compatible implementation (although it predates the POSIX standard by a few years), but as time passed it has acquired many extensions. Many of these extensions may change the behavior of valid POSIX shell scripts, so by itself bash is not a valid POSIX shell. Rather, it is a dialect of the POSIX shell language. bash supports a --posix switch, which makes it more POSIX-compliant. It also tries to mimic POSIX if invoked as sh.

Read more: [What is the difference between bash and sh](https://stackoverflow.com/questions/5725296/difference-between-sh-and-bash#5725402)

### zsh

- Zsh is a shell designed for interactive use, although it is also a powerful scripting language. Many of the useful features of bash, ksh, and tcsh were incorporated into zsh; many original features were added. The introductory document details some of the unique features of zsh. It assumes basic knowledge of the standard UNIX shells; the intent is to show a reader already familiar with one of the other major shells what makes zsh more useful or more powerful. This document is not at all comprehensive; read the manual entry for a description of the shell that is complete, concise and up-to-date, although somewhat overwhelming and devoid of examples.

Z Shell on [Source Forge](http://zsh.sourceforge.net/)


## Non-root users

#### What does this mean?

* Usually, when you log into your personal computer, you have 'administrator privileges' or 'root privileges' i.e. you can run the `sudo` command. This gives you a lot of control over the installation but also holds you responsible should anything go wrong. Technically, you could actually wipe the entire system clean (delete *literally* everything). Please don't try this.

* Anyway, this root privilege means you can create and install files in the system directories, `/usr/bin`, `/bin`, and so on. That also means that when you run `sudo make install`, your software also gains privileges to copy and create files in the corresponding system directories. That's why it doesn't require much manual copy-pasting labor to get it installed and running.

* However, often whilst configuring this stuff on a new system, you do not have root privileges (and never will, in the near future). In this case, you need to understand some concepts in order to debug the installation should you run into issues (which you shouldn't, but we all know you will).

* When you run a command, the system searches for it on the path. What is this path I speak of? Well, the system stores all its 'commands' which are basically files that are run in the shell in a folder called `/bin`, which, on different systems, is symlinked (symbolically linked, or 'points to') `/usr/bin`, `/usr/sbin`, or whatever else. The point is, all your code to be executed when you type `ls`, or `echo`, or `ifconfig` is stored in such directories that are then put on the system path.

* The system path is essentially a variable that contains a list of ALL the locations/directories to search for a command. You can add, remove, or delete all the paths (please note the original content of the variable before you clear it). Try using `echo $PATH` to see how this works on Unix. You should see a list of directories that contain the code to be run following each command you type.

* For instance when you type `python xyz.py`, the system first looks in `bin`, or whatever directory is first in your `$PATH` variable and finds a link to where the python installation is. Then it executes all your code in `xyz.py` accordingly. This directory called `bin` is common for all users of the system. So the same code runs for all of them when they type `ls`.

* Now you get why you cannot allow anyone to modify the `bin` folder. It's simply because the next time **User X** types `python`, or `ls`, you don't want this modified code by **User Y** to start downloading the latest episode of Sacred Games (or maybe you do) or worse, a computer virus.

* So, as a non-root user, when you try to install things, there are some directories where you cannot write files to. On top of it, some restrictions also mean you cannot `sudo apt-get install` or `brew install`, or `yum install` packages. In such a case, you can usually just download the packages from Github (or elsewhere) and manually install them. The instructions vary by package. 

* The idea, however, is that you can always install in a random directory (in this case, we prefer the `$HOME` or `~` directory) and then add the file to your `$PATH` variable. This tells the system that it has to also look in (for instance) `~/neofetch-5.0.0/` to find the `neofetch` command (in case you have not installed it using `brew` or `apt-get`).

* The same goes for neovim, where I have first added the path to neovim installation to the `$PATH` variable and then added a line called `alias vi='nvim'` which means the `vi` command which I conventionally used to open the `vim` editor is now replaced by the `nvim` command which is searched for on the path and found in the neovim directory:

        # added by NeoVim
        export PATH="$HOME/neovim/bin:$PATH"

        # Remove this line if you do not have neovim installed
        alias vi='nvim'


#### More Cool Modifications to the Terminal
* For more cool tutorials check out this section on [Awesome ZSH Plugins](https://github.com/unixorn/awesome-zsh-plugins#generic-zsh)

#### Additional Stuff
* [Hacking your Terminal with ASCII Artwork](https://codeburst.io/how-i-hacked-my-terminal-so-a-happy-whale-would-spout-software-quotes-at-me-6791e6c74fc6)





