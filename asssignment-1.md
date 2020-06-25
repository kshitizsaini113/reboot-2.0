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

For this task we will be *using the **mkdir** command* to create te specified directories.

#### Directory without name
![Pic-1](https://github.com/kshitizsaini113/reboot-2.0/blob/master/1/QUESTION%202/1.png?raw=true)

1. Here we need to create a directory without any name, so considering the syntax of mkdir command
```
mkdir DIRECTORY_NAME
```
2. But, as we wish to create a directory without any name, and we can't leave the arguments blank, so we will use **"** to specify the name
```
mkdir " "
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