Hello again,

In this lab report we wil be editing fromt he command line using vim.
If you want to follow along, we will be using this link from my CSE 15L class, lab 7:
```https://github.com/ucsd-cse15l-s23/lab7```

# Why use vim?
Vim is a powerful and popular text editor used for various purposes, 
primarily in programming and system administration. Here are some reasons why Vim is widely used.
Vim is designed to be efficient and optimized for speed. It offers numerous keyboard 
shortcuts and commands that allow users to perform editing.Vim supports editing a wide range of file types,
including plain text, code files (such as Java, C, Python, etc.), configuration files, and more. 
It offers syntax highlighting, code folding, auto-indentation, and other features that enhance the editing experience 
for different programming languages.

Longer description is at the end of the report.

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
```$ git remote add <URL>```
and check to see if the file is in it
```git status```
Output should be like this
```
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   ListExamples.java
```

* now we want to commit the file we have just added
```$ git commit -m "(message)"```
`-m` allows us to write a message and what we have done.
* We can also use the command 
 ```$ git log```
 to see the logs of the changes, if you were to make some changes on the same file for a year as an example.
 
 * `$ git push origin main`
Which should give you the following output
```
info: please complete authentication in your browser...
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 12 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 306 bytes | 306.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/YourUseranme/lab7.git
   503ed81..b418fa1  main -> main
 ```
 And when checking on github, and looking at the commits:
 
 ![Image](Img1lab7)
 
 
 There concludes an end to this lab report.


# CHATGPT use
Input:
```why is vim use?```
Output:
```
Vim is a powerful and popular text editor used for various purposes, primarily in programming and system administration. Here are some reasons why Vim is widely used:

Efficiency: Vim is designed to be efficient and optimized for speed. It offers numerous keyboard shortcuts and commands that allow users to perform editing tasks quickly and efficiently. Once you become proficient with Vim, you can edit text more rapidly compared to traditional text editors.

Versatility: Vim supports editing a wide range of file types, including plain text, code files (such as Java, C, Python, etc.), configuration files, and more. It offers syntax highlighting, code folding, auto-indentation, and other features that enhance the editing experience for different programming languages.

Customization: Vim is highly customizable. You can configure its settings, create custom key mappings, and define your own commands. This flexibility allows you to tailor Vim to your workflow and preferences, making it a versatile and personalized editor.

Modal editing: Vim uses a modal editing paradigm, where it has different modes for different purposes. The most commonly used modes are the "normal" mode for navigating and issuing commands, the "insert" mode for entering text, and the "visual" mode for selecting and manipulating text. This mode-based approach enables efficient editing without constantly reaching for the mouse.

Extensibility: Vim supports an extensive plugin ecosystem. You can enhance its functionality by installing plugins that add features and integration with other tools. There are plugins available for code completion, version control integration, debugging, project management, and more.

Portability: Vim is available on various operating systems, including Linux, macOS, and Windows. It is a terminal-based editor that can be used in a command-line environment, making it convenient for remote editing on servers or systems without a graphical user interface (GUI).

Longevity: Vim has been around for several decades and has a large and active community of users and developers. It is continually maintained and receives updates, ensuring its compatibility with modern systems and evolving needs.

While Vim has a steep learning curve compared to more beginner-friendly editors, its power and efficiency make it a preferred choice for many programmers and system administrators who value its speed, flexibility, and extensibility.
```

 
 













