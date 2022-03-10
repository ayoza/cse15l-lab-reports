# Lab Report 5
[MY CODE](https://github.com/ayoza/markdown-parse/blob/main/MarkdownParse.java)

[LAB 9 CODE](https://github.com/ucsd-cse15l-w22/markdown-parse/blob/main/MarkdownParse.java)

---
## How I found the tests with different results 
1. I used my markdown-parse folder as the workspace and copies the Lab 9 MarkdownParse.java into a file that I changed to be MDParseCS.java.
2. Then I ran a diff loop in bash which gave me the tests that gave different outputs. There were 36 files that had different outputs.

The Bash Code
```
javac MarkdownParse.java
javac MDParseCS.java

for file in test-files/*.md;
do
  if diff <(java MarkdownParse $file) <(java MDParseCS $file);
  then
    :
  else
    echo $file
  fi
done
```
---

## Test 1: `test-files/22.md`

* The 22.md file
    * `[foo](/bar\* "ti\*tle")`
* My output
    * `[/bar\* "ti\*tle"]`
* Lab 9 output
    * `[]`
* The expected output
    * `[/bar\*]`
* Neither output is correct
* I believe that within the parentheses of a link you are able to have a single space if the second one is in quotations. The link will be the the part that is not in quotations.
* For the Lab 9 file, the problem is that the getLinks method will not add the link if there are any spaces in the parentheses. Here is the code that could be adjusted to make the fix.
```
String potentialLink = markdown.substring(openParen + 1, closeParen).trim();
            //if there is no spaces and no line breaks in the line
            if(potentialLink.indexOf(" ") == -1 && potentialLink.indexOf("\n") == -1) 
            {
                toReturn.add(potentialLink);
                currentIndex = closeParen + 1;
            }
            else {
                //if there is a space the link will not be added
                currentIndex = currentIndex + 1;
            }
```


---

## Test 2: `test-files/483.md`
* The 483.md file
    * `[](./target.md)`
* My output
    * `[]`
* Lab 9 output
    * `[./target.md]`
* The expected output
    * `[]`
* My lab output is correct but the Lab 9 output is not.
* The reason that there should not be a link here is because there are no characters within the brackets. You cannot hyperlink text that does not exist which means that this is not a link. There is not something wrong with the existing code in lab 9. Instead the lab is lacking a way to test if there is text withing the brackets.