# 2. Setting up a Dev Environment and Our First Script

> https://www.youtube.com/watch?v=iqd0GqKsVWE  
> July 29, 2024  

## Command History
+ To check your terminal history, use `cat ~/.bash_history`
	+ `~` is your home folder
	+ `cat [<filename>]` prints a file content to terminal
	+ `.bash_history` file stores your bash terminal history. It is updated everytime you close your terminal.
	+ To check current history, you can use command `history`

## Install packages.
+ `curl`, `vim` and `build-essential`
+ Use command `sudo apt install curl vim build-essential -y`
	+ Command line option `-y` here avoids asking you for confirmation, without it you will be asked Y/n everytime to install.
+ `build-essential` contains all the `C`, `C++` stuff, general compiling things.
+ `curl` is curl
+ `vim` is kinda like youravgdev's preferred editor in terminal: [6:20](https://youtu.be/iqd0GqKsVWE?t=379)

> [!NOTE]  
> Real programmers program in vim.  
> youravgdev knows **how to quit vim**.

+ Installing `nodejs`
	+ but youravgdev doesn't want to do it using `apt`, check the video to know why.
	+ Run volta install script
		```sh
		curl https://get.volta.sh | bash
		```
		+ `curl` gets the script at given web address
		+ `|` called pipe, passes that script to next command `bash`.
		+ `bash` runs the script.
	+ To actually use volta you need to restart terminal or run command `source ~/.bashrc`, since the installl script adds few lines in `~/.bashrc` file, which is a config file for bash terminal.
	+ `volta install node@lts` - volta installs latest LTS of nodejs into `~/.volta` directory.
	+ `node -v` to check nodeJS version thats installed.
	+ youravgdev generally prefer to use `yarn` package manager, but here npm is built into nodejs. `npm -v` to check

> [!TIP]  
> If you want to add a gitignore file to your nodejs project, then youravgdev uses this command &rArr; `npx gitignore node`

## **IDE**  
+ Download VScode, although it's not an IDE, but it's good for code editing.  
+ Get `.deb` file from VSCode official website.
+ To install `.deb` package:
	+ `cd ~/Downloads` - go to downloads folder
		+ `~` means your home folder. If your username is `avgdev`, `~` is short for `/home/avgdev/`
	+ `sudo apt install <filename_without_extension>.deb` -- replace `filename_without_extension` with the actual file name without extension `.deb`

## Few linux commands  
+ `cd [<directory>]` switch the working directory to given directory  
	+ `cd ~` goes to home directory
+ `cd -` goes to previously working directory (not parent directory)
+ `pwd` print current working directory  
+ `ls` list all the files in current working directory.
+ `mkdir <dirName>` to create a directory
+ `mkdir -p <dirName>` creates a directory if it doesn't exist
	+ if you do `mkdir ~/code/newfolder`, it fails if code folder doesn't exist
	+ but `mkdir -p ~/code/newfolder` creates code folder if doesn't exist, then creates newfolder.
+ `touch <filename>` creates an empty file
+ `which <commandName>` shows the absolute path of the executable

## **Automating using bash script**  
We can automate running commands by using a bash script.  
Here is an example bash script.  
	`post-install.sh`
	```bash
	#!/bin/bash
	# Get the basic dependencies setup
	sudo apt update
	sudo apt upgrade -y
	sudo apt install curl vim build-essential gnome-tweaks -y

	# Install volta (volta.sh)
	curl https://get.volta.sh | bash

	# Install nodeJS using volta from absolute path
	$HOME/.volta/bin/volta install node@lts
	```
	+ The first line is called `shebang` line, which tells which shell to use
	+ `gnome-tweaks` is like a user interface enhancer, allows you change cursor size, change keybindings etc.
	+ `$HOME` is an variable that stores path to user's home directory.
+ You can use oracle virtualbox for Virtual Machine manager. Download its deb file and install.
+ `echo $USER` prints the name of the user.
+ `groups <username>` shows all the groups user is in.
+ `sudo usermod -aG vboxusers <username>` to add user to vboxusers group. since it's needed for vbox to access usb devices.
+ To refresh groups
	+ `id -g` to get current primary group.
	+ `newgrp vboxusers` switches you to that group and adds that to the list returned by `groups <username>` or `id -G`
	+ `newgrp <originamGroupName> ` to switch back to original primary group.
