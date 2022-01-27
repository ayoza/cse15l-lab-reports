# Week 4 Lab Report 2

## Original Markdown File
![Image](lr2og)
## Code Change #1

Screenshot of the code change diff 

![Image](lr2cc1)

Link to the test file for a failure-inducing input 

[test-file2]

Screenshot of output for the error 

![Image](lr2output1)

### Description

The issue is that the test never actually outputted a failure which means the program is stuck in an infinite loop. Because there is text after the last link, the program is never able to exit the loop because the `currentIndex` that must increase to the `markdown.length` for the loop to end will no longer increase. Therefore we must change the continuation condition to fix the error.


## Code Change #2
Screenshot of the code change diff 

![Image](lr2cc2)

Link to the test file for a failure-inducing input 

[test-file5]

Screenshot of output for the error 

![Image](lr2output2)

### Description

The program picks up a non-link string because it is in parentheses and after an open and close bracket. The fix is to make sure that the parentheses come immediatel after the closed bracket.


## Code Change #3
### Screenshot of the code change diff 

![Image](lr2cc3)

### Link to the test file for a failure-inducing input 

[test-file8]

### Screenshot of output for the error 

![Image](lr2output3)

### Description

The issue was that there was a bracket with no content and a parentheses with content immediately after and the program read the content within the parentheses as a link and added it to the ArrayList. I fixed this by ensuring that the close bracket did not come immediately after the open bracket.