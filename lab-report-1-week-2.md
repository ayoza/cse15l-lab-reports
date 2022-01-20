# Step 1 - Visual Studio Code
* Go to the [VSCode Website](https://code.visualstudio.com/) and follow the steps to download.
* Open the application and a window like below should open.

![Image](https://ayoza.github.io/cse15l-lab-reports/LR1_1.png)

# Step 2 - Remotely Connecting
* Find your course specific account [here](https://sdacs.ucsd.edu/~icc/index.php).
* Open terminal on VSCode and type $ ssh cs15lwi22zz@ieng6.ucsd.edu but replace the "zz" with your course-specific account letters.
* Respond with "yes" to the following question.
* Then enter your password to log in.

![Image](https://ayoza.github.io/cse15l-lab-reports/LR1_2.png)

# Step 3 - Run Some Commands
* Try to run a command once logged in.
* cd, ls, pwd, mkdir, and cp are all options to test.
* Command + D will log you out.
* Typing the "exit" command will also log you out.

![Image](https://ayoza.github.io/cse15l-lab-reports/LR1_3.png)

# Step 4 - Moving Files Over SSH with SCP
* Enter scp [file name here] cs15lwi22zz@ieng6.ucsd.edu:~/
* Enter password
* Then you can run the code through the server with javac and java commands.

![Image](https://ayoza.github.io/cse15l-lab-reports/LR1_4.png)

# Step 5 - SSH Keys
* This is a way to authenticate your login without having to type a passwordd every time.
* Type $ ssh-keygen in order to create a private and public key.
* Then add the public key by logging into the server, entering mkdir .ssh and logging out.
* Finally, enter the command scp /Users/[username]/.ssh/id_rsa.pub cs15lwi22zz@ieng6.ucsd.edu:~/.ssh/authorized_keys

![Image](https://ayoza.github.io/cse15l-lab-reports/LR1_5.png)

# Step 6 - Making Remote Running Even More Pleasant
* There are other shortcuts that make remote connecting much quicker and easier.
* $ ssh cs15lwi22zz@ieng6.ucsd.edu "ls" will login and run the command then logout.
* $ ssh cs15lwi22zz@ieng6.ucsd.edu "javac [file].java; java [class]" login and run the java file then logout.

![Image](https://ayoza.github.io/cse15l-lab-reports/LR1_6.png)
