# Lab Report 3 - Lab Report 3 - Bugs and Commands
Finding bugs and researching commands 
## Part 1
The issue with the `getFile` method in `fileExample.java`  is that it incorrectly processes individual files. It attempts to list contents within a file, which is an operation only applicable to directories, not to files.
- - -
A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)

```java
public class FileExampleTest {

    @Test
    public void testSingleFileRetrieval() throws IOException {
        File tempFile = new File(System.getProperty("java.io.tmpdir"), "sampleTestFile.txt");
        boolean isFileCreated = tempFile.createNewFile();
        assertTrue(isFileCreated);

        List<File> retrievedFiles = FileExample.getFiles(tempFile);

        assertEquals("Should only have one file in the list", 1, retrievedFiles.size());
        assertEquals("The retrieved file should be the one that was created", tempFile, retrievedFiles.get(0));

    }
}
```
---
An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)