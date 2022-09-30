# Remote Access Tutorial
## Installing VSCode
Hello! You will need to first install Visual Studio Code to begin the work.

The link is here [link](https://code.visualstudio.com/download). 

You can choose the download type based on the type of your type.

After you successfully download the Visual Studio Code, it should look like this:

![Image](https://github.com/JasonDai1219/cse15l-lab-reports/blob/main/VS%20Code.png)

If you have already installed Visual Studio Code before, you can skip and go to the nex part.

---
## Remotely Connecting
Hello! In this part, you can begin to connect to the server!

You will first need to type the following code in your Visual Studio Code's terminal:

the terminal look like this:

![Image](https://github.com/JasonDai1219/cse15l-lab-reports/blob/main/Terminal.png)

the command is:
`ssh cs15lfa22pv@ieng6.ucsd.edu`

You will probably get a message like this, but it is fine, just type yes:
```
⤇ ssh cs15lfa22zz@ieng6.ucsd.edu
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
Password:
```

After you enter your password, if you get something like this, then it means you have connected to the remote server successfully:
```
Last login: Sun Jan  2 14:03:05 2022 from 107-217-10-235.lightspeed.sndgca.sbcglobal.net
quota: No filesystem specified.
Hello cs15lfa22pv, you are currently logged into ieng6-203.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   23:25:01   0  0.08,  0.17,  0.11
ieng6-202   23:25:01   1  0.09,  0.15,  0.11
ieng6-203   23:25:01   1  0.08,  0.15,  0.11

Sun Jan 02, 2022 11:28pm - Prepping cs15lfa22
```

On your terminal, it should display this:

![Image](https://github.com/JasonDai1219/cse15l-lab-reports/blob/main/Remote.png)
---
## Trying Some Commands
after connecting to the remote server, you can try several commands in the terminal to explore this new stuff!

`cd`

`ls-lat`

`ls -a`

`ls <directory>` and the directory can be `/home/linux/ieng6/cs15lfa22/cs15lfa22abc`, where abc is other people's username.

`cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/`

`cat /home/linux/ieng6/cs15lfa22/public/hello.txt`

if you want to disconnect from the server, you can try:

`exit` or Ctrl-D

Here is an example of using cp and cat command:


![Image](https://github.com/JasonDai1219/cse15l-lab-reports/blob/main/Commands.png)


---
## Moving Files with scp
It would be more efficient for us to be able to move our local files, by using the `scp` command.

Where you can first try that by creating a class:

```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```
By now, you can use javac and java to compile and run the class. In this class, you should see the name of your OS system, the user name, home, and directory.

Then you are ready to move the file to the remote server, by using the following command:

`scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/`

if you compile and run the class again by using javac and java, you should see the information produced by the getProperty method of the remote server.

This is what I got for compiling and running on the remote server's terminal:

![Image](https://github.com/JasonDai1219/cse15l-lab-reports/blob/main/File.png)

---
## Setting a SSH Keys
As before, when we want to log into the remote server, we need to always type the password. But now there is a way to skip that part.

we can use the `ssh-keygen` command to save password on server and local log in portion.

when you enter the `ssh-keygen` command, we should see the following:

```
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/joe/.ssh/id_rsa): /Users/joe/.ssh/id_rsa
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/joe/.ssh/id_rsa.
Your public key has been saved in /Users/joe/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:jZaZH6fI8E2I1D35hnvGeBePQ4ELOf2Ge+G0XknoXp0 joe@Joes-Mac-mini.local
The key's randomart image is:
+---[RSA 3072]----+
|                 |
|       . . + .   |
|      . . B o .  |
|     . . B * +.. |
|      o S = *.B. |
|       = = O.*.*+|
|        + * *.BE+|
|           +.+.o |
|             ..  |
+----[SHA256]-----+
```

if the computer prompts `Enter file in which to save the key (/Users/xxx/.ssh/id_rsa)`: press enter to continue.

if youb are a Windows user, follow the extra steps from this link:
[link]( https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation)

Then you can try to log in the remote server again and type `mkdir .ssh` on the terminal and then log out.

Then back on the local device, try to type `scp /Users/joe/.ssh/id_rsa.pub cs15lfa22@ieng6.ucsd.edu:~/.ssh/authorized_keys`

After finishing all steps in this part, you should see that you do not need to enter the password again to log onto the remote server like this:

![Image](https://github.com/JasonDai1219/cse15l-lab-reports/blob/main/Key.png)
---
## Optimizing Remote Running

there are ways to actually make running remote server more efficiently, such as:

`$ scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/; javac WhereAmI.java; java WhereAmI`, which runs compiles and runs the java file in just one command line by separating them by semicolons.

and also `ssh cs15lfa22pv@ieng6.ucsd.edu "ls"` to log in and also list out all the files.

It is also convienient to use the up arrow to retrieve your previous command.
