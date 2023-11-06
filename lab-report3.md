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