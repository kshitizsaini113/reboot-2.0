# Assignment-2

### 1. Write a shell script to print factora of a number. The command must be similar to factor command.

```
#!/bin/bash

if [ $# -eq 1 ]
then
	if [ $1 -ge 1 ]
	then
		number=$1
		printf "$number : 1"
		while [ $number -gt 1 ]
		do
			i=2
			while [ $i -le $number ]
			do
				if [ $(( $number % $i)) -eq 0 ]
				then
					number=$(( number / i))
					printf "$i "
					break
				else
					printf ""
				fi
				i=$(( $i + 1 ))
			done
		done
		echo ""
	else
		echo "Argument must be a positive number"
	fi
else
	echo "Command accepts only one argument"
	echo "Try again"
fi
```

#### How will this script work

**This script will accept one argument and will print the factors for that number.**
```
[root@localhost ~]# k_factor 90909
90909 : 3 3 3 7 13 37 
```
1. The command will print the factors if a positive number is given as argument.
2. The command will give error to use a positive number 0 or a negative number is supplied.
3. The command will give error to accept only one argument if no or multiple arguments are supplied.

### 2. Write a shell script to check currently connected devices to our router & print the IP, Mac and OS-Name of the connected devices.

```
#!/bin/bash

arp-scan --localnet
```

#### How will this script work

The script will connect with all the interface and will scan the connected devices for their IP Address, Mac Address and the device name.

### 3. For a user make input-output invisible on shell. (like password is invisible on shell).

**Invisible Reading in Shell Script :** For reading invisible like reading password.

```
read -s VARIABLE_NAME
```
> -s represents silent input.

**Invisible Reading on Terminal :** We can set the terminal settings accordingly.

```
stty -echo
```
> Now, no command typed on the terminal will be shown to the user. We need to place the code in .bashrc file for the user.
```
stty echo
```
> Now the commands will be visible again.

### 4. Create a shell script, if the script is executed successfully, create it's binary and place it in the /usr/bin folder.

> We need to install **gcc** and **shc** for converting the script to binary.

**shc :** Bash script compiler. Used to hide source code and remove dependency by converting the script to binary.

```
shc -f FILENAME
```

> **.x.c :** C source code generated from FILE before compiling.
>
> **.x :** Compiled binary

We can rename the file and remove .x from the file and then we can execute the command directly.

### 5. Write a shell script which will take history of top 5 users and run those command in the specified namespace. Top 5 users will be selected on the basis of who has run more unique commands. We will take top 20 commands & re-run them in their specific users.