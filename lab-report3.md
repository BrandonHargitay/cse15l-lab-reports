# Lab Report 3 - Lab Report 3 - Bugs and Commands
Finding bugs and researching commands 
## Part 1
In `FileExample.java`, the code does not recursively list files in subdirectories, only including the contents of the specified directory.
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
The revised code corrects the bug by adding recursion, allowing `getFiles` to explore not just the immediate directory (`start`) but also all nested directories. Previously, the function only added files from the `start` directory, missing files in subdirectories. The new version, recursively calls `getFiles` for each file in a directory. This recursive call makes sure every file, is included. Additionally, it includes a null check (`if (files != null)`) before iterating over the directory contents, preventing potential NullPointerExceptions
## Part 2
### Less Command
```bash
less -pbecause ./technical/911report/chapter-1.txt

 Hani Hanjour, Khalid al Mihdhar, and Majed Moqed were flagged by CAPPS. The Hazmi brothers were also selected for extra scrutiny by the airline's customer service representative at the check-in counter. He did so because one of the brothers did not have photo identification nor could he understand English, and because the agent found both of the passengers to be suspicious. The only consequence of their selection was that their checked bags were held off the plane until it was confirmed that they had boarded the aircraft.
```
`-P` This command opens chapter-1.txt in the less viewer and immediately jumps to the first occurrence of the word "because." It's helpful for quickly locating specific information or keywords in a large text file, saving time by not having to scroll manually.
```bash
less -preport ./technical/911report/chapter-1.txt

 None of the checkpoint supervisors recalled the hijackers or reported anything suspicious regarding their screening.
```
`-P` This opens the file and jumps to the first occurrence of "report." Similar to the previous command, this is useful for quickly navigating to specific terms
- - -
```bash
less -N ./technical/911report/chapter-1.txt

1 
2         
3                 
4 "WE HAVE SOME PLANES"
5 
```
`-N` Displays the text of chapter-1.txt with line numbers in front of each line. Line numbers are used for referencing specific parts of the text, especially when discussing the document with others or editing it.
```bash
less -N ./technical/911report/chapter-2.txt

1 
2     
3         
4             THE FOUNDATION OF THE NEW TERRORISM
5             A DECLARATION OF WAR
```
`-N`Shows chapter-2.txt with line numbers. This is also useful for the same reason as above
- - -
```bash
less -J ./technical/911report/chapter-2.txt

*             It is the story of eccentric and violent ideas sprouting in the fertile ground of
*                 political and social turmoil. It is the story of an organization poised to seize its
*                 historical moment. How did Bin Ladin-with his call for the indiscriminate killing of
                  Americans-win thousands of followers and some degree of approval from millions more?
*             The history, culture, and body of beliefs from which Bin Ladin has shaped and spread
*                 his message are largely unknown to many Americans. Seizing on symbols of Islam's
*                 past greatness, he promises to restore pride to people who consider themselves the
                  victims of successive foreign masters. He uses cultural and religious allusions to
*                 the holy Qur'an and some of its interpreters. He appeals to people disoriented by
*                 cyclonic change as they confront modernity and globalization. His rhetoric
*                 selectively draws from multiple sources-Islam, history, and the region's political
*                 and economic malaise. He also stresses grievances against the United States widely
```
`-J`Opens chapter-2.txt and displays a status column indicating lines that match the current search.
This feature is useful for keeping track of search results within a document, especially in a long file.

```bash
less -J ./technical/911report/chapter-1.txt

Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millio
* ns of men and women readied themselves for work. Some made their way to the Twin Towers, the signature stru
* ctures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Penta
* gon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylv
* ania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush
*  went for an early morning run.
```
`-J`Opens chapter-1.txt with a status column showing lines matching the current search.
It helps in navigating through search results, particularly in long documents.
- - -
```bash
less -M ./technical/911report/chapter-2.txt

            THE FOUNDATION OF THE NEW TERRORISM
            A DECLARATION OF WAR
            In February 1998, the 40-year-old Saudi exile Usama Bin Ladin and a fugitive Egyptian
                physician, Ayman al Zawahiri, arranged from their Afghan headquarters for an Arabic
                newspaper in London to publish what they termed a fatwa issued in the name of a

/technical/911report/chapter-2.txt lines 11-30/948 3%
```
`-M`Opens chapter-2.txt in less with a detailed prompt showing the file name and current position within the file. This detailed prompt is useful for understanding your location within a large file.
```bash
less -M ./technical/911report/chapter-1.txt

    For those heading to an airport, weather conditions could not have been better for a safe and pleasant journey. Among the travelers were Mohamed Atta and Abdul Aziz al Omari, who arrived at the airport in Portland, Maine.

./technical/911report/chapter-1.txt lines 6-16/731 1%
```
`-M`Displays chapter-1.txt with a detailed prompt including the file name and current position.
It shows a clear context of your location within the file, which is  useful in long documents to track progress.
- - -
The command options were found by googling `less command options` I found a site that gave a description of the and picked the options that looked the most interesting
[https://phoenixnap.com/kb/less-command-in-linux](https://phoenixnap.com/kb/less-command-in-linux)
