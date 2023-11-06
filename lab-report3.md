# Lab Report 3 - Lab Report 3 - Bugs and Commands
Finding bugs and researching commands 
## Part 1
The issue with the `getFile` method in `fileExample.java`  is that it incorrectly processes individual files. It attempts to list contents within a file, which is an operation only applicable to directories, not to files.