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
## Moving Files over SSH with scp
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

if you compile and run the class again, you should see the information produced by the getProperty method of the remote server.
