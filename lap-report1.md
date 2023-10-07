# Lab Report 1 - Remote Access and FileSystem (Week 1)
Basic filesystem commands we learned in class 10/03/23
## Commands
* cd
	1. Share an example of using the command with no arguments.

		```console
		[user@sahara ~/lecture1]$ cd
		
		
		```
  
		Working Directory:
		```console
		[user@sahara ~/lecture1]$ pwd
		/home/lecture1
		```
	 	when running the `cd` command with no arguments we do not change directories. Since no argument was given the terminal did not know what directory to change to. The directory stayed the same. The command does not throw an error however the `cd` command should have a argument in order for it to work.
	2. Share an example of using the command with a path to a directory as an argument.

		```console
		[user@sahara ~/lecture1]$ pwd
		/home/lecture1
		[user@sahara ~/lecture1]$ cd messages/
		[user@sahara ~/lecture1/messages]$ pwd
		/home/lecture1/messages
		```
  
		Working Directory:
		```console
		[user@sahara ~/lecture1]$ pwd
		/home/lecture1
		```
	 	when running the `cd` command with a path to a directory as an argument changes the working directory. As you can see from the above code we change directories from `/home/lecture1` to `/home/lecture1/messages` using the `cd` command.
	3. Share an example of using the command with a path to a file as an argument.

		```console
		[user@sahara ~/lecture1/messages]$ cd en-us.txt 
		bash: cd: en-us.txt: Not a directory
		[user@sahara ~/lecture1/messages]$ pwd
		/home/lecture1/messages
		```
  
		Working Directory:
		```console
		[user@sahara ~/lecture1/messages]$ pwd
		/home/lecture1/messages
		```
	 	when running the `cd` command with a path to a file as an argument it outputs an error `bash: cd: en-us.txt: Not a directory` this says that the argument is not a directory which is true its a file. 

 * ls
	1. Share an example of using the command with no arguments.

		```console
		[user@sahara ~/lecture1]$ ls
		Hello.class  Hello.java  messages  README
		
		
		```
  
		Working Directory:
		```console
		[user@sahara ~/lecture1]$ pwd
		/home/lecture1
		```
	 	when running the `ls` command with no arguments it outputs a list of the files and directories in the working directory. The output is not a error.
	
 * cat
	1. Share an example of using the command with no arguments.

		```console
		[user@sahara ~/lecture1]$ cat
		
		
		```
  
		Working Directory:
		```console
		[user@sahara ~/lecture1]$ pwd
		/home/lecture1
		```
	 	when running the 'cat' command with no arguments the command hangs and does not output anything. I had to use 'ctrl + c' to exit the command. The output is an error, the 'cat' command needs an argument since no argument was given, and there was nothing to cat out.
	


