Hello again,

In this lab report we wil be editing fromt he command line using vim.
If you want to follow along, we will be using this link from my CSE 15L class, lab 7:
```https://github.com/ucsd-cse15l-s23/lab7```

# Step 1: logging into ieng6

We would need to log in to our ieng6 account
```ssh cs15lsp23**@ieng6.ucs.edu```
and type in your password, unless you have generated a SSH key. I won't be able to explain that
part, as I, Myself have struggle for around two hours generating it.

# Step 2:cloneing the repository

we would need to clone the repository
```$ git clone https://github.com/ucsd-cse15l-s23/lab7```
next we want to change our directory 
```cd lab7```
and type in ```ls``` right after should bring up four files:
```ListExamples.java  ListExamplesTests.java  lib  test.sh```

# Step 3: Checking if the file runs correctly
We now want to check if ListExamples.java was written correctly by testing it with
ListExamplesTest.java.
***First***
we would want to compile the java files:
```javac -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" *.java```

BTW: The ```*``` in ```.java```, just helps let bash fill in whatever file that has ```.java```
which in this case is ```ListExamples.java``` and ```ListExamplestest.java```
---

***Second***
Then we would need to run the test:
```java -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ListExamplesTests```

After running it we recieved an error:
```
JUnit version 4.13.2
..E
Time: 0.601
There was 1 failure:
1) testMerge2(ListExamplesTests)
org.junit.runners.model.TestTimedOutException: test timed out after 500 milliseconds
        at java.base/java.util.Arrays.copyOf(Arrays.java:3512)
        at java.base/java.util.Arrays.copyOf(Arrays.java:3481)
        at java.base/java.util.ArrayList.grow(ArrayList.java:237)
        at java.base/java.util.ArrayList.grow(ArrayList.java:244)
        at java.base/java.util.ArrayList.add(ArrayList.java:454)
        at java.base/java.util.ArrayList.add(ArrayList.java:467)
        at ListExamples.merge(ListExamples.java:42)
        at ListExamplesTests.testMerge2(ListExamplesTests.java:19)

FAILURES!!!
Tests run: 2,  Failures: 1
```

# Step 4: learning about the different commands used
Now, that we know there's an error in the file, we would need to correct it. 
The error in question is that `index1 is used instead of index2 in the final loop in merge`.
So we would need to change the `1` in `Index1` to a `2`.
One method, which is very fast is by using `vim`, which will allow us to edit in the terminal.
by typing:
```vim ListExamples.java```
That file will now open up in the terminal, in which you can hastly correct it.
To get to the error we can use just our `keyboard`.
---
***Here are some keys that will be using to navigate through the terminal***

* `<h>` to go left
* `<j>` to go down
* `<k>` to go up
* `<l>` to go right
---

***More: list of keys to help speed up the editing***
those letter in `<>` are the keys you would press
those in `()` is what you would type out

* `(number) + <k>` allows us to move up n times
* `<SHIFT> + <g>` allows us to move to the end of the file
* `<e>` allows us to go to the last letter of the word
* `</> + (word)` allows us to search for the word
* `<n>` relating to the previous command,if there are more than one of the word we are searching for, this will
allow us to look through all the places where the (word) is contained.
* `<x>` deletes the letter where your cursor is hovering over` you will have to be in normal mode`
* `<i>` allows us to go into ***INSERT*** mode out of ***NORMAL*** mode, in which we can type into the terminal.
* `<w>` allows us to save our work
* `<u>` undo the last edit you made
* `<CTRL> + <r>` redo the last edit you made
* `<ESC>` can help exit out of ***INSERT*** mode, or allows us to exit vim by the next following commands
* `<:> + <q>` allows us to exit out of vim, however only if you have save the file.
* `<:> + <q> + <!>` allows us to exit out of vim without saving, only use this when you have made a mistake, and don't want to press ***UNDO*** over and over
* `<:> + <w> + <q>` one of the more used commands, allows us to save and exit.

# Step 5: making the edit
For the following list, I am going to include the list of keys pushed, to fix the file
those letter in `<>` are the keys you would press
those in `()` is what you would type out
---
***Slow and Simple***
* `(/)` ```index1``` `<ENTER>`
* `<n><n><n><n><n><n><n><n><n><n><n>`
* `<l><l><l><l><l>`
* `<x>`
* `<i>`
* `<2>`
* `<ESC><ESC>`
* `<:> + <w> + <q>`
* `<ENTER>`

***Faster and Better***
* `<SHIFT> + <g>`
* `<6> + <k>`
* `<e>`
* `<x>`
* `<i>`
* `<2>`
* `<ESC><ESC>`
* `<:> + <w> + <q>`
* `<ENTER>`

# Step 6: recompile and check if it works
Re-Using the same command from Step 3.
```javac -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" *.java```

```java -cp ".:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ListExamplesTests```

Output:
```
JUnit version 4.13.2
..
Time: 0.02

OK (2 tests)
```

***SUCCESS!!!!***

# Step 7: Commit and push
* To make sure the work has save 
```cat ListExamples.java```
will show the currect output with the change on line 44.

* now we want to add in the java file we have modified
```$ git add ListExamples.java```
and check to see if the file is in it
```git status```
Output should be like this
```
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   ListExamples.java

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ListExamples.class
        ListExamplesTests.class
        StringChecker.class
```

* now we want to commit the file we have just added
```$ git commit -m "(message)"```
`-m` allows us to write a message and what we have done.
* We can also use the command 
 ```$ git log```
 to see the logs of the changes, if you were to make some changes on the same file for a year as an example.
 
 













