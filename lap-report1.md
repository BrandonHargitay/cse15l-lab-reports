# Lab Report 1 - Remote Access and FileSystem (Week 1)
Basic filesystem commands we learned in class 10/03/23
## Commands
* <h3>cd</h3>
	1. Share an example of using the command with no arguments.

		```console
		[user@sahara ~]$ cd lecture1/
		[user@sahara ~/lecture1]$ pwd
		/home/lecture1
		[user@sahara ~/lecture1]$ cd
		[user@sahara ~]$ pwd
		/home
		
		
		```
  
		Working Directory:
		```console
		[user@sahara ~/lecture1]$ pwd
		/home/lecture1
		```
	 	when running the `cd` command with no arguments the directory changes to the home directory. We can see this by using `pwd` before and after running the `cd` command
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
	 	when running the `cd` command with a path to a file as an argument it outputs an error `bash: cd: en-us.txt: Not a directory` this says that the argument is not a directoy, you can only use `cd` with a path to a directory as an argument.

 * <h3>ls</h3>
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
	 	when running the `ls` command with no arguments it outputs a list of the files and directories in the working directory. The output is not an error.
	2. Share an example of using the command with a path to a directory as an argument.

		```console
		[user@sahara ~/lecture1]$ ls messages/
		en-us.txt  es-mx.txt  hu.txt  zh-cn.txt
		```
  
		Working Directory:
		```console
		[user@sahara ~/lecture1]$ pwd
		/home/lecture1
		```
	 	when running the `ls` command with a path to a directory as an argument it outputs the files and directories inside the directory that was passed as an argument. The output is not an error.
	3. Share an example of using the command with a path to a file as an argument.

		```console
		[user@sahara ~/lecture1]$ ls messages/en-us.txt 
		messages/en-us.txt
		```
  
		Working Directory:
		```console
		[user@sahara ~/lecture1]$ pwd
		/home/lecture1
		```
	 	when running the `ls` command with a path to a file as an argument it outputs the argument that was passed. This output was not an error.
 * <h3>cat</h3>
	1. Share an example of using the command with no arguments.

		```console
		[user@sahara ~]$ cat
		test
		test
		what
		what
		
		
		```
  
		Working Directory:
		```console
		[user@sahara ~/lecture1]$ pwd
		/home/lecture1
		```
	 	when running the `cat` command with no arguments the command seems like it hangs and does not output anything *BUT* if you enter a word and hit enter the word will cat out. eg. If I type test and click enter test will output. This is not an error, however, I do not see how this can be useful.
	2. Share an example of using the command with a path to a directory as an argument.

		```console
		[user@sahara ~/lecture1]$ cat messages/
		cat: messages/: Is a directory
		```
  
		Working Directory:
		```console
		[user@sahara ~/lecture1]$ pwd
		/home/lecture1
		```
	 	when running the `cat` command with a path to a directory as an argument it outputs an error `cat: messages/: Is a directory` since the argument is a directory there is nothing to cat out.
	3. Share an example of using the command with a path to a file as an argument.

		```console
		[user@sahara ~/lecture1]$ cat Hello.java 
		import java.io.IOException;
		import java.nio.charset.StandardCharsets;
		import java.nio.file.Files;
		import java.nio.file.Path;
		
		public class Hello {
		  public static void main(String[] args) throws IOException {
		    String content = Files.readString(Path.of(args[0]), StandardCha
		rsets.UTF_8);    
		    System.out.println(content);
		  }
		```
  
		Working Directory:
		```console
		[user@sahara ~/lecture1]$ pwd
		/home/lecture1
		```
	 	when running the `cat` command with a path to a file as an argument it outputs the contents of the argument. In this case, it outputed the contents of the `Hello.java` file. This is not a error.

