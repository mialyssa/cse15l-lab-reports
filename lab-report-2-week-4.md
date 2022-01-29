[Link back to index page](https://mialyssa.github.io/cse15l-lab-reports/)

# Lab 2 - Week 4: Testing and Debugging

## Code Change 1: Accounting for words inbetween parenthesis and brackets
![repo commit image](https://user-images.githubusercontent.com/97639434/151639615-c1657892-a41c-4991-806a-845171ebe695.png)
[Link to the test file containing failure-inducing input]() 

Symptom: 
![vscode containing error msg](https://user-images.githubusercontent.com/97639434/151638494-a1a122c8-bc46-4bf1-b6cc-b5d72e64205d.png)

The input contained ```"hello"``` in between the parenthesis and brackets messed up the reading of the link. The program ended up breaking and forced to exit as a result. The bug was that the code did not account for the appearance of any characters inbetween the end parenthesis and beginning bracket of a link, and tried to store it as a link.



## Code Change 2: Accounting for unnecessary brackets and parenthesis
![repo commit image](https://user-images.githubusercontent.com/97639434/151639024-90d7164f-ec5c-4b97-9b7f-304443bc83c8.png)
[Link to the test file containing failure-inducing input](https://github.com/mialyssa/markdown-parse/blob/main/breaks-first-commit-2.md) 

Symptom: 
![vscode containing error msg](https://user-images.githubusercontent.com/97639434/151640363-a47a80f1-8be9-48f1-a622-e7223dac577c.png)



The link was formatted wrong, however the symptom shows that it was still considered a link. The input had an extra set of brackets within the link name (```[link[]]```).



## Code Change 3: Accounting for images
![repo commit image](https://user-images.githubusercontent.com/97639434/151637256-b017d910-3442-432c-89d5-1c1268f87eda.png)
* Code change 1 and 3 happened in the same commit. This image references the second if-statement as a new bug fix.

[Link to the test file containing failure-inducing input](https://github.com/mialyssa/markdown-parse/blob/main/test-file6.md) 

Symptom: 
![vscode containing error msg](https://user-images.githubusercontent.com/97639434/151639833-8412a075-5ecb-474f-99d1-c82397d57e76.png)
The file contained the formatting for an image link, however the program counted it as a regular link and added it to the arraylist, as shown by the symptom. The bug was that the program did not search for any ```!``` that would indicate the difference between an image and a page link.
