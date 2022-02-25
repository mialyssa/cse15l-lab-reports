[Link back to index page](https://mialyssa.github.io/cse15l-lab-reports/)

# Lab 3 - Week 6: Copy Whole Directories with ```scp -r```

## Introduction
Copying entire directories into ieng6 is useful for when we work with multiple files and libraries for our code. Especially when working with github and bash, Linux works best over windows.

Using ```scp``` we can recursively copy the directory and all the folders and files within it so it transfers safely. 

For this lab, we will copy the directory ```markdown-parse-COPY``` into the ieng6 server, transfering all of these files inside it: 

![markdown parse COPY contents](https://user-images.githubusercontent.com/97639434/153683135-df3b9e10-d993-49bd-b3cb-02f60101c584.png)

## Copying the directory into the ```ieng6``` account

While having the specified directory open with it's terminal, use ``scp -r``` to connect to the remote server:

``` 
$ scp -r . cs15lwi22alz@ieng6.ucsd.edu:~/markdown-parse-COPY 
```

Notes:

```-r``` means to work recursively.

```.``` means "this" source, aka the current directory.

```cs15lwi22alz@ieng6.ucsd.edu``` is the server we want to copy the directory over to.

```~/markdown-parse-COPY``` is the specified directory (and its contents) to copy, and is successfully done if the name does not already exist.

![running scp -r command](https://user-images.githubusercontent.com/97639434/153683347-144389bc-0e61-4254-baa7-d90ff69da796.png)


## Logging into ieng6 and running the directory

Now when we log into our ieng6 account, we will find the directory loaded into the server.
![ls in ieng6](https://user-images.githubusercontent.com/97639434/153683529-2aef3068-c7e7-4334-b3d9-400fb72b50d4.png)

Use ```cd markdown-parse-COPY``` to go into the directory.

We can now run the makefile, which compiles and runs markdownParse and markdownParseTest, to show that is has successfully transfered. 

![running makefile](https://user-images.githubusercontent.com/97639434/153685608-c43c9c0a-832b-4e82-b514-b27b06483ab2.png)


## Hastening the process

Like in lab 1, we can combine all these steps into one line, using ```;``` to combine all the commands.

To remove the directory within the server, ```cd``` back into the main hub and type ```rm -r markdown-parse-COPY``` to successfully remove the directory and it's contents.

Here is the entire process represented using two lines:
```
scp -r . cs15lwi22alz@ieng6.ucsd.edu:~/markdown-parse-COPY; ssh cs15lwi22alz@ieng6.ucsd.edu
```
Once in the remote server:
```
cd markdown-parse-COPY; bash makefile; bash makefile
```
![running commands on one line](https://user-images.githubusercontent.com/97639434/153686227-5de46469-9538-456b-840c-282e60a02dc9.png)

pushing to github repo from ieng6:

    ```git add .```
    
    ```git commit -m "message"```
    
    ```git push```
