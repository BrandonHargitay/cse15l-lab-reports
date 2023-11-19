# Lab Report 4 - Vim (Week 7)
Performing shortcuts 
## Steps
1. I opened my terminal and manually typed `ssh cs15lfa23jk@ieng6.ucsd.ed` I found that my typing speed is faster then trying to use the `up` arrow to find my ssh command in the history
![Screenshot1](./images/step1.png) 
2. I typed `git clone` prior to starting `step 1` I made sure to copy the github URL so I could use `cmd + v` to paste the URL into my terminal to save time
![Screenshot1](./images/step2.png) 
3. I cloned the repo into my home directory so I had to use `cd` to change directory. I typed `cd la` then hit `<tab>` to auto complete the line then hit `<enter>` to run the full command which was `cd lab7/`
![Screenshot1](./images/step3_1.png) 
Once I was inside the `lab7` direcotry I ran the test by typing `bash te` then hit `<tab>` to autocomplete the line then clicked `<enter>` to run the command. The full command was `bash test.sh`
![Screenshot1](./images/step3_2.png) 
4. To fix the failing test I had to edit the java file. I typed `vim Lis` then hit `<tab>` to autocomplete but it only autocomplete till `vim ListExamples` I then typed a `.` then clicked `<tab>` again and it autocompleted then I hit `<enter>` to run the this command `vim ListExamples.java`
![Screenshot1](./images/step4.png)
The `jUnit` error stated that the error was on line 44 so instead of clicking `j` multiple times I could enter `43j` to move my cursor to line 44. I hit `e` to move my cursor to the end of the next word on the line where my cursor is. I pressed `r` to replace the letter that my cursor is on then pressed `2` now `index1` is `index2`. To save the changes and exit vim I typed `:wq`
![Screenshot1](./images/step4_2.png)
5. I now re ran the test and typed `bash te` clicked `<tab>` and it autocomapleted to `<bash test.sh` and clicked `<enter>` to run the test. I find it faster to type out the command then using the `up` arrow to use my previous commands. The tests were successful.
![Screenshot1](./images/step5.png)
6. To push and commit the changes I made I typed `git add Li` clicked `<tab>` to auto complete and to save more time ran two commands in one line by using `&&` I then typed `git commit -m "Fix Error"` the full command was `git add ListExamples.java && git commit -m "Fix error"` then to push the commit I typed `git push`
![Screenshot1](./images/step6.png)