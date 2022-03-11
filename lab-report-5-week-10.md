[Link back to index page](https://mialyssa.github.io/cse15l-lab-reports/)

# Lab 5 - Week 10: Comparing Markdown Implementations 

For this lab report, two tests from the 652 commonmark-spec tests were chosen where my group's implementation had different answers than the implementation 
provided [here](https://github.com/ucsd-cse15l-w22/markdown-parse).


## Test file 577

__The original ```test-files/577.md``` contains ```![foo](train.jpg)``` as it's contents.__
* The provided markdown parse and my markdown parse gave different outputs when comparing ```Test-files/577.md```. I used the ```diff``` bash command to compare the files 
that were outputted on each repository's markdown parse. The process was similar to this:

```
[cs15lwi22alz@ieng6-201]:markdown-parse-lab10:$ bash script.sh > results.txt (run markdownparse and save results to a txt file)
[cs15lwi22alz@ieng6-201]:markdown-parse-mialyssa:$ bash script.sh > results.txt (run markdownparse and save results to a txt file)
[cs15lwi22alz@ieng6-201]:$ diff markdown-parse-lab10/results.txt markdown-parse-mialyssa/results.txt >  markdown-parse-lab10/diff.txt (run diff and save it to a txt file)
```
Output of the ```diff``` comparison:

![diff comparison of 577](https://user-images.githubusercontent.com/97639434/157852351-793f4bcf-7062-4275-b253-b7ddacd96f00.png)

* According to [commonmark](https://spec.commonmark.org/dingus/), the correct output
should be a broken link, or ```[]``` as our output. Therefore, my markdown parse (the top output) was more correct than the provided markdown parse (bottom output).
* The bug is that the code is not accounting for the appearance of images. The symptom is that the link output was ```train.jpg```, when it should be ```[]```, meaning 
it did not check for any ```!``` denoting an image.

## Test file 505

__The original ```test-files/505.md``` contains ```[link](/url "title \"&quot;")``` as it's contents.__
* Both my markdown and the provided markdown gave different answers, neither of which were correct according to commonmark. This was found using the same method as above,
using ```diff``` and commonmark to get the list of different outcomes comparing each testfile.

Output of the ```diff``` comparison:

![diff comparison of 505](https://user-images.githubusercontent.com/97639434/157855810-4fd0eacb-2daa-402e-aeea-042a4a319d1c.png)

* According to commonmark, the output should be ```[url]```, while everything inside the quotes should be omitted as it is a title. However, my markdown parse (top) 
outputted everything regardless between the brackets, while the provided markdown parse did not return anything.
* The bug is that the contents in between the quotes are not omitted, as it is part of a title. The code should check for closed sets of quotation marks within a
set of brackets or parenthesis, as the contents within them are to be removed from the link.
