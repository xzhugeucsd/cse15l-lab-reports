# Installing VScode
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/Installing%20VScode.png)
Install [Visual Studio Code](https://code.visualstudio.com/) if it isn't already installed. It is a powerful and free source-code editor. Features include Debugging support, syntax highlighting, intelligent code completion, snippets, code refactoring, and embedded Git.

# Remotely Connecting
For the first step, open a terminal. Your command will look like down below:

        $ ssh cs15lfa22ta1@ieng6.ucsd.edu

The last two letters will be different with your own course-specific account.

        $ cs15lfa22ta1@ieng6.ucsd.edu) Password:
Now type your password to log in the remote computer.

If your terminal is connected to a remote computer seccussfully. It will look similar like the image below:
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/Remotely%20Connecting.png)

# Trying Some Commands
Please try running some commands ``cd``,``ls``, ``pwd``, ``cp``, ``mkdir`` both on your client and the server after ssh-ing.
 * cd ~ (change the directionary to home path)
 * ls (list all the files in the directionary)
    * ls -lat
    * ls -a
    * ls directiory
 * cp (compile)
 * cat (print the context in teh file)

On the client:
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/Tring%20command1.png)

On the server:
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/trying%20command2.png)

# Moving Files with scp

There is a command called ``scp``, we will always run it from the client to the server. Basically ,this command helps us copy files back and forth between the computers.

        $ scp filename.java cs15lfa22ta1@ieng6.ucsd.edu:~/

First of all, you should create a file you want to copy to the server. Or you can use the **WhereAmI.java** example:

        class WhereAmI {
            public static void main(String[] args) {
            System.out.println(System.getProperty("os.name"));
            System.out.println(System.getProperty("user.name"));
            System.out.println(System.getProperty("user.home"));
            System.out.println(System.getProperty("user.dir"));
            }
        }

Now compile the WhereAmI.java using the ``javac`` and ``java`` commands to ensure the code is running correctly.

        $ javac WhereAmI.java
        $ java WhereAmI

Finally, we now run the ``scp`` command with the correct password:

        scp filename.java cs15lfa22ta1@ieng6.ucsd.edu:~/

![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/scp%20file.png)

Hint: You can also run the javac/java command on the ieng6 computer.
# Setting an SSH Key
An SSH key is creating a pair of files. A publics key on the server and a private key on the client. Then, the ``ssh-keygen`` command can use the pair of files to enter the password like a face-id!

        $ ssh-keygen

![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/Setting%20an%20SSH%20Key.png)

Then we need to copy the public key to the server. First we need to log in to the server.

        $ ssh cs15lfa22ta1@ieng6.ucsd.edu
        <enter Password>
Secondly, make directory to the server

        $ $ mkdir .ssh
        <logout>
Finally, you can access **ssh/scp** without entering your password.
![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/ssh%20with%20ssh%20key.png)
# Optimizing Remote Running
Writing commands in quotes at the end of an `ssh` will directly run it on the server.

        $ ssh cs15lfa22ta1@ieng6.ucsd.edu "ls-a"

Semicolons can be used to run multiple commands on the same lines.

        $ cp filename.java otherfile.java; javac otherfile.java; java otherfile

The up-arrow can recall the last command.

        $ ↑

![](https://github.com/xzhugeucsd/cse15l-lab-reports/blob/main/Optimizing%20Remote%20Running.png)
