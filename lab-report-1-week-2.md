[Link back to index page](https://mialyssa.github.io/cse15l-lab-reports/)

# Lab 1 - Week 2: Logging into a course-specific account remotely

## Setting up and Installing VS Code

Install VSCode with [this link.](https://code.visualstudio.com/) The interface should look like this:

![Installing VS Code](https://user-images.githubusercontent.com/97639434/149594407-c008ca37-da50-4de2-acce-8ee1b3dd1c4f.png)

## Connecting Remotely 

Connecting remotely requires [installing SSH.](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) Then lookup your [course specific account here.](https://sdacs.ucsd.edu/~icc/index.php) 
Open a new terminal in VSCode and connect to the SSH server using the code specific email for ieng6:
```ssh cs15lwi22alz@ieng6.ucsd.edu```

When connected, it should look like this: 

![Remotely Connecting](https://user-images.githubusercontent.com/97639434/149598134-bf5b5819-b38a-45b0-ba4b-1c4f8df0d220.png)

Now you are connected to the ieng6 server in the UCSD CSE Basement. 

## Trying Some Commands 

Here are a couple of commands that can be used while in the remote server:

* ```ls``` command lists files in current directory
* ```ls -l``` lists all files in the current directory plus additional info such as last edited 
* ```ls -a``` lists all files including hidden files in the current directory
* ```ls -lat``` lists all files including hidden files in current directory and provides additional info
* ```pwd``` gives absolute path of directory
* ```cd``` by itself takes you back to the home directory
* ```mkdir``` creates a new folder
* ```rmdir``` removes an empty directory
* ```rmdir -rf``` removes nonempty directory along with it's contents
* ```scp``` copies file onto server
* ```alias``` lets you make custom linux commands (kinda)	
* ```open``` followed by a filename opens the file 
* ```rev``` reverses every string given to it (Ctrl + C to exit)
* ```touch``` creates a new file
* ```rm``` removes a file
* ```du``` gets the size of files and folders in a directory
* ```echo``` produces whatever follows as text output

![Trying Some Commands](https://user-images.githubusercontent.com/97639434/149598715-905eef64-ddb3-4583-aae2-ff59496d8b48.png)

## Moving Files with scp

Moving files from your client (home computer) to the server (SSH) must be done from the client computer. To exit the server, type ```exit``` or ```logout```.
Using the file name, use scp to transfer the desired file into the server:
```scp fileName.java cs15lwi22alz@ieng6.ucsd.edu:~/```

Then you can log in and using ```ls```, it should appear in the server. (In this case, I added the *WhereAreYou.java* file)

![Moving Files with scp](https://user-images.githubusercontent.com/97639434/149599685-9d23b532-4956-4218-b266-a5814ae7083f.png)

## Setting up an SSH Key

Setting an SSH Key eliminates the need to type in the password to ```cse15lwi22alz@ieng6.ucsd.edu``` every time you log in.
To do so, follow in the client (not on the server):
1. type in the client ```ssh-keygen```
2. Enter the location to save the keys in: ```/Users/mialy/.ssh/id_rsa```
3. (bypass the passphrase by pressing enter 3 times)
4. Now make a directory called ```.ssh``` in the server: ```mkdir .ssh``` (log into server first)
5. Logout, and now the password is no longer required to log in anymore! This is due to the last step creating a copy of the public key to the ```.ssh``` directory of the User on the server.

(However, most of the images in this report do not show the need for a password, as I had already completed it in lab)

![Setting an SSH Key - Step 4](https://user-images.githubusercontent.com/97639434/149600346-2bc5d4e8-2a18-4c42-a92a-cbf09957de54.png)

## Optimizing Remote Running

To make this run even smoother and faster, strategies that can be used are quality of life instances such as
* pressing the up arrow key to select code that was already inputted before
* putting multiple lines of code in a single line using semicolons (__;__)
* Using quotes to access a command remotely while logging in
* Using an alias to create a keyword to do a bunch of code at once (using the above methods)
> ```alias test="scp WhereAreYou.java cs15lwi22alz@ieng6.ucsd.edu:~/; ssh cs15lwi22alz@ieng6.ucsd.edu 'javac WhereAreYou.java';ssh cs15lwi22alz@ieng6.ucsd.edu 'java WhereAreYou'" ```

![Optimizing Remote Running](https://user-images.githubusercontent.com/97639434/149601466-6c966840-a367-4b95-ba8b-9bc3e3eb05a9.png)

Previously, before setting up our SSH key, it took almost __15+ keystrokes__ to access our files. Now, as we have already typed them all out previously, we can combine them all into one line. Utilizing the up arrow keys and typing in ```;``` after each command, we can tackle this task in under __7 keystrokes__.

``` scp WhereAreYou.java cs15lwi22alz@ieng6.ucsd.edu:~/; ssh cs15lwi22alz@ieng6.ucsd.edu; javac WhereAreYou.java; java WhereAreYou ```


