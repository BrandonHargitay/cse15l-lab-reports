# Lab Report 5 - Remote Acess
Design a debugging scenario
## Part 1 – Debugging Scenario
1. The original post from a student with a screenshot showing a symptom and a description of a guess at the bug/some sense of what the failure-inducing input is. (Don’t actually make the post! Just write the content that would go in such a post)
- - -
Hi everyone, I'm having trouble with my grading script. I run it with bash `grade.sh <GITHUB_URL>`, but it seems to be failing to compile the Java files. I suspect it might be related to the classpath or the JAR files, but I'm not sure. Here's the error message I get:
```console
Error: Could not find or load main class org.junit.runner.JunitCore
Caused by: java.lang.ClassNotFoundException: org.junit.runner.JunitCore
```
![Screenshot1](./images/lab5_1.png) 
2. A response from a TA asking a leading question or suggesting a command to try (To be clear, you are mimicking a TA here.)
- - -
The error message suggests there's a problem with finding the necessary classes for JUnit. It might be related to the classpath. Could there be a typo in the path? Could you share your the `javac` command you ran. Also, try running `ls -l lib` to list the contents of your lib directory and share the output. This will help confirm whether the JAR files are in the expected location.
3. Another screenshot/terminal output showing what information the student got from trying that, and a clear description of what the bug is.
- - -
Here is the result of running `ls -l lib` and here is the `javac` command I was running.
```console
❯ ls -l lib
total 840
-rw-r--r--  1 hargy  staff   45024 Nov  7 10:32 hamcrest-core-1.3.jar
-rw-r--r--  1 hargy  staff  384581 Nov  7 10:32 junit-4.13.2.jarj
```
```console
javac -cp .:libb/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.jav
```
