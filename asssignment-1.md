# Assignment-1

![Assignment](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/ASSIGNMENT_1.png?raw=true)

![Assignment](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/ASSIGNMENT_2.png?raw=true)

## Question 1 : Block System Call :

* Block system call for date command 
* That means you don't have to uninstall date command but if you run kernel must not accept 
* Do the same Firefox as well

For this task we will be *removing the execution permission from the commands* so that they do not get executed when used, not even for root user. For this we will need the root user access. 

![Pic-1](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%201/9.png?raw=true)

1. We will edit the .bashrc file and set the alias for the commands.
```
alias date=": date"
alias firefox=":firefox"
```
2. When we run the commands from the user no output will be shown and even the commands will not be uninstalled.


## Question 2 : Play with Directory :

* Create a directory without name from command line
* create a directory with name "-okgoogle"

For this task we will be *using the **mkdir** command* to create the specified directories.

#### Directory without name
![Pic-1](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%202/1.png?raw=true)

1. Here we need to create a directory without any name, so considering the syntax of mkdir command
```
mkdir DIRECTORY_NAME
```
2. But, as we wish to create a directory without any name, and we can't leave the arguments blank, so we will use **"** to specify the name
```
mkdir ''$'\n'
```
> It will create a driectory without any name in the current folder. 
3. The directory is visible both in CLI and GUI.

#### Directory with name -okgoogle
![Pic-2](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%202/2.png?raw=true)

1. Here we need to create a directory without any name, so considering the syntax of mkdir command
```
mkdir DIRECTORY_NAME
```
2. But, as we wish to create a directory with the name begining with **-**, but mkdir is consider -o as option here and shows that *no such option is available for mkdir*, so we will specify the current folder and then specifying the name will not be considered as option.
```
mkdir ./-okgoogle
```
> It will create a driectory without any name in the current folder. 
>> Even, using **"** in the case without using **./** will result in error, as now also mkdir will accept that as option for mkdir.
3. The directory is visible both in CLI and GUI.

## Question 3 : Create Directory Structure :

**NOTE:** We are allowed to use a single command and only one time.

* Create a directory structure as described above

For this task we will be *using the **mkdir** command* to create the specified directories.

#### Directory Structure
![Pic-1](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%203/1.png?raw=true)

1. Here we need to create a directory structure and that too in one line so we will use **-p** option with the command
```
mkdir -p A/{B/{G/K/Reboot.txt,H/J/Reboot.txt},C/{I/J/Reboot.txt,J/L/Reboot.txt},D/{F/L/Reboot.txt,E/M/Reboot.txt}}
```
2. We will see the directory using the tree command
```
tree A
```
> It will create a driectory without any name in the current folder.

## Question 4 : Sharing the files and folder 

* Create two users name jack and jill from command line.
* Create all the data under home directory of each users.
* Login with jack user and create a file name jack.txt using vim editor and write "hello jack".
* From jack user also create two directories name jack1 & jack2. 
* Now login from Jill user and create a file. Jill.txt using vim editor and write "hey jiil"
* From Jill also create two directoires named jill1 & jill2.

**IMPORTANT :** Swap these files and directories in between user and to swap don't use root account.

#### File Sharing between users
![Pic-1](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%204/1.png?raw=true)

1. First we need to create the users jack and jill. Now we need to set the password for the users.
```
sudo adduser jack
sudo adduser jill

sudo passwd jack
sudo passwd jill
```
2. We need to add the home directories of the users to each other's group.
```
sudo chgrp jill /home/jack
sudo chgrp jack /home/jill
```
3. Switch to jack and create the files and folders. We can use ls to view the content.
```
su - jack -> Enter password for jack
vim jack.txt
mkdir jack1
mkdir jack2
ls
logout
```
4. Switch to jill and create the files and folders. We can use ls to view the content.
```
su - jill -> Enter password for jill
vim jill.txt
mkdir jill1
mkdir jill2
ls
logout
```
5. Now we can access each other user's file from the other user.
```
su - jack
mv jack1 /home/jill
mv jack2 /home/jill
mv jack.txt /home/jill
cd /home/jill
mv jill.txt $HOME
mv jill1 $HOME
mv jill2 $HOME
ls
cd
ls
logout
```
![Pic-2](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%204/2.png?raw=true)

6. The files have been shared between the users without using root permissions.

## Question 5 : Play with Files and Directories :

* Create 4 files named 'abc.txt', 'ok', 'fine' and 'g.txt' under /tmp directory.
* Create 3 directories 'aa', 'aaa', 'aaaa' under /tmp directory.
* Give ls command to list the content of /tmp directory.
* Make sure it will only list the content (file|directory) having 2 char in their name.

For this task we will be *using the **mkdir, touch and ls** command* to create directories, files and viewing the content respectively.

![Pic-1](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%205/1.png?raw=true)

1. We need to create multiple directories in /tmp folder and such can be achieved using
```
touch /tmp/{abc.txt,ok,fine,g.txt}
```
2. We need to create multiple directories in /tmp folder and such can be achieved using
```
mkdir /tmp/{aa,aaa,aaaa}
```
3. For listing only files and directories with 2 characters,
```
ls --ignore='???*' --ignore='?' /tmp
```
> --ignore option will ignore the files matching specified pattern.
>> ???* will ignore all the files having three or more characters in their name.
>>
>> ? will ignore files having single name character.

## Question 6 : Run command without any output :

* Open terminal and type any command.
* Once you press 'enter' your output of given command must not print.
* You are not allowed to redirect output anywhere.

![Pic-1](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%206/1.png?raw=true)

1. We will use **:** before the command, for not printing it's output
```
: $(COMMAND)
```
> **:** specifies to do nothing.
>
> **$(COMMAND)** specifies to run the command.

## Question 7 : Create Shell Script :

* Create a shell script named /root/delvex.sh.
* Make sure it will run /bin/sh shell.
* A user will be running this script my using a command name opensource
* When a user  run like  "opensource  time" it must give current time only.
* When it runs like "opensource user"  it will give list of interactive shell users only.
* When run like "opensource 100"  it must print "Hello Delvex" 100 times in interval of 1 sec.
* If runs like  "opensource windows"  then it must shutdown OS.
* if run opensource command without any parameter  then it must show out:
    1) Name of Kernel
    2) Version of Kernel
    3) Current date DD/MM/YY
    4) Name of OS
    5) Last reboot time

> Each output for last option must be in a separate line.

![Pic-1](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%207/1.png?raw=true)

1. Create a file named delvex.sh using vim
```
vim /root/delvex.sh
```
2. Create the shell script as specified
```
#!/bin/sh

if [ $# == 0 ]
then
	echo ""
	uname -r
	echo ""
	cat /proc/version
	echo ""
	date +%D
	echo ""
	cat /etc/os-release | head -n 1
	echo ""
	last reboot | head -n 1
	echo ""
elif [ $1 == "time" ]
then
	echo ""
	date +%T
	echo ""
elif [ $1 == "user" ]
then
	echo ""
	users
	echo ""
elif [ $1 == "100" ]
then
	echo ""
	count=0
	while [ $count -le 100 ]
	do
		echo "Hello Delvex"
		sleep 1
	done
	echo ""
elif [ $1 == "windows" ]
then
	echo ""
	shutdown
	echo ""
fi
```
3. Add execution permission to the script and the directory
```
chmod +x /root/delvex.sh
chmod +x /root
```
4. Create a script as opensource and call the script from there.
```
vim /usr/bin/opensource
```
5. Add the following to the above created script
```
#!/bin/sh

/root/delvex.sh $@
```
6. All execution permission to the script and run from an user.
```
chmod +x /usr/bin/opensource
```

## Question 8 : Create a user with default settings :
 
* Create a user name delvex and password of this user will be fedora.
* When user got created below listed things will come by default.
* History size will be 5000.
* History file will be  /home/delvex/myhist.txt .
* Default shell will be  /bin/sh .

![Pic-1](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%208/1.png?raw=true)

1. Edit the /etc/bashrc file and edd the following to the end.
```
if [ $USER == "delvex" ]
then
	HISTSIZE=5000
	HISTFILE=/home/delvex/myhist.txt
	SHELL=/bin/sh
	export HISTSIZE HISTFILE SHELL
fi
```
2. Create the user delvex and set the password.
```
useradd delvex
passwd delvex
```
3. Changes will be reflected in user.