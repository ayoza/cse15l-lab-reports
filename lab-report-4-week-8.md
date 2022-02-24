# Lab Report 4
## Repositories
* [My Repository](https://github.com/ayoza/markdown-parse)

* [Reviewed Repository](https://github.com/Obarquinho/markdown-parse)

## Snippet 1
### Should Produce
    [`google.com, google.com, ucsd.edu]
### Code To Test It
I put it in a separate test file to separate it from the other test files
```
import static org.junit.Assert.*;
import org.junit.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.List;

public class SnippetTest {
    
    @Test
    public void testSnippet1() throws IOException {
        String contents= Files.readString(Path.of("./snippet1.md"));

        List<String> expect = List.of("`google.com", "google.com", "ucsd.edu");
        assertEquals(expect, MarkdownParse.getLinks(contents));
    }
}
```
### My Output
    [url.com, `google.com, google.com]
### Reviewed Output
    [url.com, `google.com, google.com]
### Question
Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change.
* I think that this code, while fairly simple to fix for this test would require a lot of changes since I would need to fix two errors. The first that I do not check if there is a code symbol within the brackets and before the open bracket which is why my method accepts `url.com` as a link. The second is that my code checks if there is an open paren directly after the first closed bracket which is why `ucsd.edu` is not read as a link.


## Snippet 2
### Should Produce
    [a.com, a.com(()), example.com]
### Code To Test It
```
import static org.junit.Assert.*;
import org.junit.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.List;

public class SnippetTest {
    
    @Test
    public void testSnippet2() throws IOException {
        String contents= Files.readString(Path.of("./snippet2.md"));

        List<String> expect = List.of("a.com", "a.com(())", "example.com");
        assertEquals(expect, MarkdownParse.getLinks(contents));
    }

}
```
### My Output
    [a.com, a.com((]

### Reviewed Output
    [a.com, a.com((]
### Question
Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? If yes, describe the code change. If not, describe why it would be a more involved change.
* This would also be simple yet large change since there is also two issues to fix. One is similar to the previous one which is that my code checks if there is an open paren directly after the first closed bracket which means `example.com` is not added to the links. The second is that my `getLinks()` method considers the link from the open bracket that begins the link to the first close bracket regardless of if there is another closed bracket after it which is why the `a.com(())` is read as `a.com((`.

## Snippet 3
### Should Produce
I believe that the other two links should not be included since they are not hyperlinked on the preceding text.

    [https://ucsd-cse15l-w22.github.io/]
### Code To Test It
```
import static org.junit.Assert.*;
import org.junit.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.List;

public class SnippetTest {
    @Test
    public void testSnippet3() throws IOException {
        String contents= Files.readString(Path.of("./snippet3.md"));

        List<String> expect = List.of("https://ucsd-cse15l-w22.github.io/");
        assertEquals(expect, MarkdownParse.getLinks(contents));
    }
}
```

### My Output

    [
    https://www.twitter.com
    , 
    https://ucsd-cse15l-w22.github.io/
    , github.com

    And there's still some more text after that.

    [this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



    ]


### Reviewed Output
    [
    https://www.twitter.com
    , 
    https://ucsd-cse15l-w22.github.io/
    , github.com

    And there's still some more text after that.

    [this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



    ]
### Question
Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change.
* This is an issue that is complicated and will take a lot of lines to fix. The main issue is that I will likely have to find a way to check if there is a double space between lines in the markdown file and I do not have any code that can test this in my current java file.


