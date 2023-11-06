# Lab Report 3 - Lab Report 3 - Bugs and Commands
Finding bugs and researching commands 
## Part 1
The code does not recursively list files in subdirectories, only including the contents of the specified directory.
- - -
A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)
```bash
some-files/
|-  a.txt
|-  more-files/
    |-  b.txt
    |-  c.java
|-  even-more-files/
    |-  d.java
    |-  a.txt
```

```java
public class FileTest {
    @Test
    public void testRecursion(){
        File start = new File("some-files/");
        
        List<File> files = FileExample.getFiles(start);
        
        int count = 5; 
        
        assertEquals("ERROR! expected count does not match actual count", count, files.size());
        
        assertTrue(files.contains(new File("some-files/a.txt")));
        assertTrue(files.contains(new File("some-files/more-files/b.txt")));
        assertTrue(files.contains(new File("some-files/more-files/c.java")));
        assertTrue(files.contains(new File("some-files/even-more-files/d.java")));
        assertTrue(files.contains(new File("some-files/even-more-files/a.txt")));
    }
  
}
```
- - -
An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)
```java
@Test
    public void testSingleDirectory() throws IOException {
        File start = new File("some-files/a.txt");
        
        List<File> files = FileExample.getFiles(start);
        
       
        final int count = 1; 
        assertEquals("ERROR! expected count does not match actual count", count, files.size());
        
        assertTrue(files.contains(new File("some-files/a.txt")));
    }
```
- - -
The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)
![Screenshot1](./images/lab3_junit.png)
- - -
The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)
### Before
```java
static List<File> getFiles(File start) throws IOException {
	  File f = start;
	  List<File> result = new ArrayList<>();
	  result.add(start);
	  if(f.isDirectory()) {
	    File[] paths = f.listFiles();
	    for(File subFile: paths) {
	      result.add(subFile);
	    }
	  }
	  return result;
	}
```
### After

```java
	static List<File> getFiles(File start) throws IOException {
	  List<File> result = new ArrayList<>();
        if (start.isDirectory()) {
            File[] files = start.listFiles();
            if (files != null) {
                for (File file : files) {
                    result.addAll(getFiles(file));
                }
            }
        } else {
            result.add(start);
        }
        return result;
	}
```
This change fixes the bug by recursively traversing all directories and collecting files from each directory, not just the top-level directory.
## Part 2
### Less Command
```bash
less -pbecause ./technical/911report/chapter-1.txt

 Hani Hanjour, Khalid al Mihdhar, and Majed Moqed were flagged by CAPPS. The Hazmi brothers were also selected for extra scrutiny by the airline's customer service representative at the check-in counter. He did so because one of the brothers did not have photo identification nor could he understand English, and because the agent found both of the passengers to be suspicious. The only consequence of their selection was that their checked bags were held off the plane until it was confirmed that they had boarded the aircraft.
```
```bash
less -preport ./technical/911report/chapter-1.txt

 None of the checkpoint supervisors recalled the hijackers or reported anything suspicious regarding their screening.
```
Opens the first item that fits the given pattern in a text file on the page.
- - -
