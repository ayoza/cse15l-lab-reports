# Week 4 Lab Report 2

## Original Markdown File
![Image](https://raw.githubusercontent.com/ayoza/cse15l-lab-reports/main/Lab%20Report%202%20SS/LR2_OG.png)
## Code Change #1

### Code Change

![Image](https://raw.githubusercontent.com/ayoza/cse15l-lab-reports/main/Lab%20Report%202%20SS/LR2_CC1.png)

### Link to the Test File

[test-file2](https://github.com/ayoza/markdown-parse/blob/main/test-file2.md?plain=1)

### Screenshot of the Output Error

![Image](https://raw.githubusercontent.com/ayoza/cse15l-lab-reports/main/Lab%20Report%202%20SS/LR2_OUTPUT1.png)

### Description

The issue is that the test never actually outputted a failure which means the program is stuck in an infinite loop. Because there is text after the last link, the program is never able to exit the loop because the `currentIndex` that must increase to the `markdown.length` for the loop to end will no longer increase. Therefore we must change the continuation condition to fix the error.


## Code Change #2

### Code Change

![Image](https://raw.githubusercontent.com/ayoza/cse15l-lab-reports/main/Lab%20Report%202%20SS/LR2_CC2.png)

### Link to the Test File

[test-file5](https://github.com/ayoza/markdown-parse/blob/main/test-file5.md?plain=1)

### Screenshot of the Output Error

![Image](https://raw.githubusercontent.com/ayoza/cse15l-lab-reports/main/Lab%20Report%202%20SS/LR2_OUTPUT2.png)

### Description

The program picks up a non-link string because it is in parentheses and after an open and close bracket. The fix is to make sure that the parentheses come immediatel after the closed bracket.


## Code Change #3

### Code Change

![Image](https://raw.githubusercontent.com/ayoza/cse15l-lab-reports/main/Lab%20Report%202%20SS/LR2_CC3.png)

### Link to the Test File

[test-file8](https://github.com/ayoza/markdown-parse/blob/main/test-file8.md?plain=1)

### Screenshot of the Output Error

![Image](https://raw.githubusercontent.com/ayoza/cse15l-lab-reports/main/Lab%20Report%202%20SS/LR2_OUTPUT3.png)

### Description

The issue was that there was a bracket with no content and a parentheses with content immediately after and the program read the content within the parentheses as a link and added it to the ArrayList. I fixed this by ensuring that the close bracket did not come immediately after the open bracket.