# Week 6 Lab Report 3 (Copying whole directories with scp -r)

## Part 1
* This part was the simplest for me since I was able to do this on my first try without an issue. I typed in the command `scp` with the flag `-r` and I added the `destination name` and the `directory`. 
* The line looked like this: `scp -r . ieng6:~/markdown-parse`

![Image](https://raw.githubusercontent.com/ayoza/cse15l-lab-reports/main/Lab%20Report%203%20SS/LR3_SS1.png)

## Part 2
* Here was where I faced a difficult issue while running the file remotely. I had no problem connecting with `ssh ieng6`. I check the files with an `ls` call and did a `cd markdown-parse` to get into the `markdown-parse` directory.
* I ran into the problem when I ran `make test` as running that command produced a "Cannot find symbol" error. I looked on Piazza and found that another student had the same error so I fixed it by adding `/software/CSE/oracle-java-se-14/jdk-14.0.2/bin/` to the front of my javac and java commands.
* I ran `make test` again with the fix and the output is below.

![Image](https://raw.githubusercontent.com/ayoza/cse15l-lab-reports/main/Lab%20Report%203%20SS/LR3_SS2.png)

## Part 3
* After solving the previous issue this one was much simpler as I was able to refer back to lab 1 to get a skeleton of how it should look.
* Here was what I typed into the terminal: `scp -r . ieng6:~/markdown-parse; ssh ieng6; "cd markdown-parse; make test"`. The output from this is below.



![Image](https://raw.githubusercontent.com/ayoza/cse15l-lab-reports/main/Lab%20Report%203%20SS/LR3_SS3.png)

and

![Image](https://raw.githubusercontent.com/ayoza/cse15l-lab-reports/main/Lab%20Report%203%20SS/LR3_SS4.png)