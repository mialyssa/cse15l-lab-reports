# Logging into a course-specific account remotely

Install VSCode with https://code.visualstudio.com/ The interface should look like this:

![Installing VS Code](https://user-images.githubusercontent.com/97639434/149594407-c008ca37-da50-4de2-acce-8ee1b3dd1c4f.png)

Connecting remotely requires [installing SSH.](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) Then lookup your [course specific account here.](https://sdacs.ucsd.edu/~icc/index.php) 
Open a new terminal in VSCode and connect to the SSH server using the code specific email for ieng6:
> ssh cs15lwi22alz@ieng6.ucsd.edu

When connected, it should look like this: 

![Remotely Connecting](https://user-images.githubusercontent.com/97639434/149598134-bf5b5819-b38a-45b0-ba4b-1c4f8df0d220.png)

Now you are connected to the ieng6 server in the UCSD CSE Basement. 

Here are a couple of commands that can be used while in the remote server:

* __ls__ command lists files in current directory
* __ls -l__ lists all files in the current directory plus additional info such as last edited 
* __ls -a__ lists all files including hidden files in the current directory
* __ls -lat__ lists all files including hidden files in current directory and provides additional info
* __pwd__ gives absolute path of directory
* __cd__ by itself takes you back to the home directory
* __mkdir__ creates a new folder
* __rmdir__ removes a directory
* __scp__ copies file onto server
* __alias__ lets you make custom linux commands (kinda)	
* __open__ followed by a filename opens the file 
* __rev__ reverses every string given to it (Ctrl + C to exit)
* __touch__ creates a new file
* __rm__ removes a file
* __du__ gets the size of files and folders in a directory
* __echo__ produces whatever follows as text output

![Trying Some Commands](https://user-images.githubusercontent.com/97639434/149598715-905eef64-ddb3-4583-aae2-ff59496d8b48.png)

Moving files from your client (home computer) to the server (SSH) must be done from the client computer. To exit the server, type __exit.__
Using the file name, use scp to transfer the desired file into the server:
> scp fileName.java cs15lwi22zz@ieng6.ucsd.edu:~/

Then you can log in and using __ls__, it should appear in the server. (In this case, I added the *WhereAreYou.java* file)

![Moving Files with scp](https://user-images.githubusercontent.com/97639434/149599685-9d23b532-4956-4218-b266-a5814ae7083f.png)



![Setting an SSH Key]

![Optimizing Remote Running]
