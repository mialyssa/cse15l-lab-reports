[Link back to index page](https://mialyssa.github.io/cse15l-lab-reports/)

# Lab 4 - Week 8: Debugging
[Reviewed repository](https://github.com/annakkin/markdown-parse) | [My repository](https://github.com/mialyssa/markdown-parse)

## Snippet 1
Expected output: ```[`google.com, google.com, ucsd.edu]```

![snippet1 proper output](https://user-images.githubusercontent.com/97639434/155817867-691ee734-675d-43e7-a854-ec49a8d45097.png)

JUnit Test made in ```MarkdownParseTest.java``` to test snippet:

![JUnit Test](https://user-images.githubusercontent.com/97639434/157138220-18be9c17-e347-434e-ac98-eb36c766b1f3.png)

What my MarkdownParse outputted:

![my output for snippet 1](https://user-images.githubusercontent.com/97639434/157137311-996863c2-c077-4f2a-aee1-85f41b12733a.png)

What the reviewed MarkdownParse outputted:

![annakkin's output for snippet 1](https://user-images.githubusercontent.com/97639434/157137778-281fde6f-3bd8-47f0-bee7-8f98a7eb85af.png)

Is there a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks?
> I do not think there is a small solution, since backticks are meant to segment out code so that it does not get triggered. To account for cases such as ```url.com```, the code would have to ignore what ever is within the backticks and take precedence before running the correct code. This would probably take around 15-20 lines of code.


## Snippet 2
Expected output: ```[a.com, a.com(()), example.com]```

![snippet2 proper output](https://user-images.githubusercontent.com/97639434/155818863-85ba578e-e1e3-41e7-9e5f-26b76e6534d5.png)

JUnit Test made in ```MarkdownParseTest.java``` to test snippet:

![JUnit Test](https://user-images.githubusercontent.com/97639434/155819179-dfce8a8d-d8c8-4dba-9e36-130b08c4776f.png)


What my MarkdownParse outputted:

![my output for snippet 2](https://user-images.githubusercontent.com/97639434/155819295-5ac053a2-af3c-469c-9667-dea3e895f6e2.png)


What the reviewed MarkdownParse outputted:

![annakkin's output for snippet 2](https://user-images.githubusercontent.com/97639434/155819528-eb2c306b-b61c-4f2f-b80d-3fa8e0aa97cf.png)

Is there a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets?
> No, I think it would be between 10 - 20 lines of code. We can use stacks to keep the most recent ```nextOpenBracket``` pair with the most recent ```nextCloseBracket``` and pop them off the stack once they have been paired (same with the parenthesis). This can ensure that the nested brackets and parenthesis will confuse the Markdown as long as there is a complete pair.


## Snippet 3
Expected output: ```[https://ucsd-cse15l-w22.github.io/]```

![snippet3 proper output](https://user-images.githubusercontent.com/97639434/155819094-e8edbba1-421d-458d-a717-b4ffa5946a9a.png)

JUnit Test made in ```MarkdownParseTest.java``` to test snippet:

![JUnit Test](https://user-images.githubusercontent.com/97639434/155819395-aeeb7146-82c9-4bdc-b9db-fc7486ac6f87.png)



What my MarkdownParse outputted:

![my output for snippet 3](https://user-images.githubusercontent.com/97639434/155819430-fa4022d3-05ca-4dac-9567-6c37aca88b98.png)


What the reviewed MarkdownParse outputted:

![annakkin's output for snippet 3](https://user-images.githubusercontent.com/97639434/155819591-e6f58916-7ce8-46e1-b7f6-fdc1b4ec0e96.png)

Is there a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses?
> Yes, if the line ends and the brackets or parentheses are not complete yet, we continue onto the next line and search for the end bracket there. If it still doesnt exist, then that is when the link is considered broken. Based on the output of both our implementations, line breaks work with brackets, so adding a parenthesis implementation would have similar results.
