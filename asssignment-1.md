# Assignment-1

![Assignment](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/ASSIGNMENT.png?raw=true)

## Question 1 : Block System Call :

* Block system call for date command 
* That means you don't have to uninstall date command but if you run kernel must not accept 
* Do the same Firefox as well

For this task we will be *removing the execution permission from the commands* so that they do not get executed when used, not even for root user. For this we will need the root user access. 

#### Date Command
![Pic-1](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%201/1.png?raw=true)

1. Here in the images for date, first we need to find where the command is located so I have used the **which** command to find that.
```
which date
```
2. Further, as the command is executing and we need to block the execution of the command without uninstalling it so I have used **chmod** and removed the execution permission from the command.
```
sudo chmod -x /usr/bin/date
```
> I have performed this operation with sudo privilages as I need to change the permission for all the users, even root.
3. Try executing the command, and the command will not be accessible. Not even with root user.

#### Firefox Command
![Pic-2](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%201/2.png?raw=true)

1. Here in the images for firefox, first we need to find where the command is located so I have used the **which** command to find that.
```
which firefox
```
2. Further, as the command is executing and we need to block the execution of the command without uninstalling it so I have used **chmod** and removed the execution permission from the command.
```
sudo chmod -x /usr/bin/firefox
```
> I have performed this operation with sudo privilages as I need to change the permission for all the users, even root.
>> This will remove the permission to access the command even from the GUI click in the App List. 
3. Try executing the command, and the command will not be accessible. Not even with root user.

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