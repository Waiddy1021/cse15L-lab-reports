Lab Report 5

2023/06/04

In this lab report we will be going through a conversation between a TA and a student
who is having trouble with their program. It will be provided in like a 3rd person POV.


# Student Reporting the error

---

All students in CSE15L run through a problem with their code more then once, in any course. In this example the student is having
problems tring to get their code to run.

All students in CSE15L can write a post through the course's EdStem. When writing a post to help debug. The student
will be provided with a template and questions as to what the problem is. What you guys have input and what the output you are
recieving, and what are you expecting.

![Image](lab5Image1.png)

![Image](lab5Image2.png)

![Image](lab5Image3.png)

# TA's Response

---

**TA thought process**

What the TA might do is to read through the students problem,
Once read through the TA's first instance is to go through the error given 
in the terminal, then go through the code that is provided by the student.
 
Since the problem is occuring with the file TestListExamples.java
The TA would focus more on the lines that has to do with the Test file

 
**TA'S Response**

Based on the error picture given by the student, The TA might give a response 
that will consider changing the javac and java lines, since it is having trouble 
trying to compile the files
especially the CPATH.
 
What the TA might consider is:

Number 1: rewrite the junit and hamcrest for CPATH in line 1: CPATH =  ```../lib/junit-4.13.2.jar:../lib/hamcrest-core-1.3.jar:.``` instead.    

                                                                                                                                    
or

Number 2: remove the $CPATH and direct put in that quote on the javac and java in line 56 & 57. Which is basically the same
as Number 1, but it helps to see it in the javac and java line instead of continously scrolling up and down to check if
the the CPATH is written correctly.
 
Since the TA is gieven the description that the Student is using vim to edit and see his files.
The TA might include some keys to press and edit it

**Keys such as**

---

*  < i > to go into insert mode
  
*  < delete > to remove the $CPATH
  
*  < ESC > to exit out on insert mode
  
*  < : > + < w > + < q > to save and exit the file.
 
# Student's fix code

---

After typing in the suggested cpath the TA had suggested,
The student ran some test, and got his expected outputs

** links used by the student to run test**

---
Link 1:https://github.com/ucsd-cse15l-f22/list-methods-corrected,[Link](https://github.com/ucsd-cse15l-f22/list-methods-corrected):

Should pass all test

Link 2:https://github.com/ucsd-cse15l-f22/list-methods-filename,[Link](https://github.com/ucsd-cse15l-f22/list-methods-filename):

Return invalid due to the file name not matching

Link 3:https://github.com/ucsd-cse15l-f22/list-methods-lab3,[Link](https://github.com/ucsd-cse15l-f22/list-methods-lab3):

Shoud return some error with the test
  
**OutPuts when running the test with the link**

```
[cs15lsp23ix@ieng6-203]:graderWaiddy:505$ bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected
Finished cloning
All tests passed

[cs15lsp23ix@ieng6-203]:graderWaiddy:507$ bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-filename
Please submit a valid file, check the name or location of your file!

[cs15lsp23ix@ieng6-203]:graderWaiddy:508$ bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-lab3
Finished cloning
Test(s) failed:1
```
  
# Reflection

---

One thing that I have learned, is how to write the grader test. When we first started on that lab. 
I had a lot of problems writing the codes for it to work. However after a couple more tries, and an other
  lab deticated to writing the grade.sh again. I was able to get some help from my lab TA, and my lab partners.
Also after learning about vim, I have used it constantly when writing codes, I find it very useful and quick. 
especially the search method for a certain word.
  


 
 
 





