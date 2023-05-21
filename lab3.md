Hello again to you all,

In this lab report, we will learn about 4 commands on:
```
grep
```

One standard command we add know how to use grep is 
```
grep "term" file.txt
```

How ever there are more ways on how you could use grep, In this report I will demonstrate four different ways.
We will be using the file ```pmed.0020191.txt```, Since it has the least amount of words in it.

# Number 1
```
grep -v "string" file.txt
```
The option "-v" invert the match, will will return all lines in that file.txt that DOES NOT contain the string.
***First Example***
```
grep -v "Lori" pmed.0020191.txt
```
will return:
```
    Constructing Ethical Guidelines for Biohistory” [1], neither advocates nor argues against
        biohistorical research; instead, it points out that such investigations are currently
        taking place without guidelines—ethical, scientific, moral, or religious. The question
        remains: if such guidelines were to be established, what individuals, institutions,
        governments, medical examiners, family members, or intrepid biographers are to be given
        permission? Who is to decide what is “historically significant”? Not to mention the
        meta-question: who is to decide who is to decide? I apologize to the authors if my brief
        comments [2] implied that they took a position on this issue.
```
---
***Second Example***
```
grep -v "I" pmed.0020191.txt
```
will return:
```
 The excellent article by Jordan Paradise, Lori B. Andrews, and colleagues, “Ethics.
        Constructing Ethical Guidelines for Biohistory” [1], neither advocates nor argues against
        biohistorical research; instead, it points out that such investigations are currently
        taking place without guidelines—ethical, scientific, moral, or religious. The question
        remains: if such guidelines were to be established, what individuals, institutions,
        governments, medical examiners, family members, or intrepid biographers are to be given
        permission? Who is to decide what is “historically significant”? Not to mention the
        comments [2] implied that they took a position on this issue.
```
notice how in the first example output, The line that contains the string ```Lori``` is no where to be found, however it appears in the second example.
One way this method could be useful, is when you are writing methods, and when testing it throws out the wrong exception. You could use this method to help you find the problem immediatly without having to search through the file.


# Number 2
```
grep -i "term" file.txt
```
This option "-i" allows us to search for a term, not really specifically as it will return any word that matches/ or contains that term reguardless is its capitalized or not.
***First Example***
```
grep -i "biohistory" pmed.0020191.txt
```

will return:
```
 Constructing Ethical Guidelines for Biohistory” [1], neither advocates nor argues against
```
---
***Second Example***
```
grep -i "exam" pmed.0020191.txt
```
will return:
```
governments, medical examiners, family members, or intrepid biographers are to be given
```

In the first example only one line contained the word ```biohistory```, now in the line we see that Biohistory was capitalized, but it still returned the line.
In the second example we narrowed the term down to ```exam``` and returned the line with the word ```examiners```, as ```exam``` is in it.
One way this method could be useful, is when you are searching for a long word, or  a complicated word.For example if a word like ```onomatopoeia```, 
is in the text file, for me it is a difficult word to spell, however I would know the first five letters, and let grep do its job.
# Number 3
```
grep -w "term" file.txt
```
The option "-w" will only allow you to search for that specific term in that line.
***First Example***
```
grep -w "what"
```
will return:
```
 remains: if such guidelines were to be established, what individuals, institutions,
 permission? Who is to decide what is “historically significant”? Not to mention the
 ```
 ---
 ***Second Example***
 ```
 -w "exam" file.txt
 ```
 will return:
 ```
 
 ```
 
 We see in the first example, The lines returned only included the term ```what``` nothing more and nothing less
 However, we see in the Second Example that nothing was returned, ass previously mentioned -w only allows us to search for that specific term. Unlike
 the second method provided in Number 2. Where ```grep -i "exam" pmed.0020191.txt```, was able to return the line with the word ```examiners```.
 For example if you want to search through a file where it mentions ```cats``` or ```cat```, but there are certain words such as ```category```. Then
 this method would definely help narrow down the output bash will give, or mention in example two, show that there are no relation to the word you have mention and should move to to a different file.
 
 # Number 4
 ```
 grep -r "term" directory/
 ```
 
 Unlike the method given for Number 1, "-r" is the complete opposite of the method, and will return the line with the term in it, However since we are using directory 
 for this method.It will go through all files in the specified directory and its subdirectories, and returns the names of any files that contain the specified term.
 ***First Example***
 ```
 grep -r "Lori" /home/linux/ieng6/cs15lsp23/cs15lsp23ix/stringsearch-data/technical
 ```
 will return:
 ```
 /home/linux/ieng6/cs15lsp23/cs15lsp23ix/stringsearch-data/technical/government/Media/Good_guys_reward.txt:
 He has two law partners, Lori Mannicci and Linda Gardner. They
/home/linux/ieng6/cs15lsp23/cs15lsp23ix/stringsearch-data/technical/government/Media/Legal_Aid_attorney.txt:
Schwartz replaced former Legal Aid attorney Lori Rubenstein at
/home/linux/ieng6/cs15lsp23/cs15lsp23ix/stringsearch-data/technical/plos/pmed.0020060.txt:
The Lincoln testing question spurred bioethicist Lori Andrews and her colleagues at the
/home/linux/ieng6/cs15lsp23/cs15lsp23ix/stringsearch-data/technical/plos/pmed.0020191.txt:
The excellent article by Jordan Paradise, Lori B. Andrews, and colleagues, “Ethics.
/home/linux/ieng6/cs15lsp23/cs15lsp23ix/stringsearch-data/technical/plos/pmed.0020192.txt:
Science piece with Lori B. Andrews that Hayden references, I am troubled
 ```
 ---
 ***Second Example***
 ```
 grep -r "what" /home/linux/ieng6/cs15lsp23/cs15lsp23ix/stringsearch-data/technical
 ```
 will return(The output was too long, like serveral hundreds)
 But here is one where in one file.txt it has many of the same term in it:
 ```
 /home/linux/ieng6/cs15lsp23/cs15lsp23ix/stringsearch-data/technical/plos/pmed.0020272.txt:
 must do what they can to reduce false conclusions.
/home/linux/ieng6/cs15lsp23/cs15lsp23ix/stringsearch-data/technical/plos/pmed.0020272.txt:
what is the consequence of setting it higher?
/home/linux/ieng6/cs15lsp23/cs15lsp23ix/stringsearch-data/technical/plos/pmed.0020272.txt:
that what matters is the totality of the evidence.
```

We see after putting in the directory ```/home/linux/ieng6/cs15lsp23/cs15lsp23ix/stringsearch-data/technical```, for the output, it automactically fills in the files
in the folder, and searches for the term, also allowing we to see which folder it was in. In the Second example we see that all the output has the same
directory ```/home/linux/ieng6/cs15lsp23/cs15lsp23ix/stringsearch-data/technical/plos/pmed.0020272.txt ```, but there several lines that contained ```what```.

This lab report wouldn't be possible without the help of ChatGPT, which allowed me to see serveral different ways to use grep. For me personally, after learning new ways to use grep. I think ```grep -w "word" file.txt``` is the most helpful method. Also you guys may not be able to see this, but in the terminal in VScode, The ```term``` you search for will be highlighted in red.


The link to ChatGPT can be found here: [Link](https://chat.openai.com/?model=text-davinci-002-render)

There are many different methods that ChatGPT can give to you, also It doesn't have to be the command ```grep```, There are many more options you could ask ChatGPT.

# CHATGPT use
what I input:
``` What ways could you use "grep" in bash for java?```

What chatGPT responded with:
```When using grep in Bash to search for patterns in Java code, you can employ various options and techniques. Here are a few examples:

Basic usage: To search for a specific string or pattern within Java files, you can use the following command:

grep "pattern" file.java
This will display all lines in the file.java that match the given pattern.

Case-insensitive search: If you want to perform a case-insensitive search, you can use the -i option:

grep -i "pattern" file.java
Recursive search: If you have a directory containing multiple Java files and you want to search for a pattern in all of them, you can use the -r (or --recursive) option:

grep -r "pattern" directory/
Counting occurrences: To count the number of occurrences of a pattern within a file, you can use the -c (or --count) option:

grep -c "pattern" file.java
Inverting the match: If you want to display lines that do not match a specific pattern, you can use the -v (or --invert-match) option:

grep -v "pattern" file.java
Regular expressions: grep supports regular expressions, which can be useful for more complex pattern matching. For example, to search for lines containing either "apple" or "banana," you can use the alternation (|) operator:

grep "apple\|banana" file.java
Redirecting output: You can redirect the output of grep to a file using the > operator. For instance, to save the matched lines to a new file:

grep "pattern" file.java > matched_lines.txt
These are just a few examples of how you can utilize grep in Bash to search for patterns in Java code. The grep command offers many other options and features, which you can explore further by referring to its documentation (man grep).
```
I also use ChatGPT to help come up with examples for the method ```grep -w``` as I couldn't come up with anything myself:
```in what ways is "grep -w" useful?```

What ChatGPT output:
```
The grep -w command is useful when you want to perform a "whole word" search using grep. It allows you to match patterns that are complete words 
and not just substrings. Here are a few ways grep -w can be useful:

Searching for exact word matches: When you want to search for a specific word and exclude partial matches or substrings, grep -w is handy. For example, if you want to find occurrences of the word "cat" in a file but exclude words like "catch" or "category," you can use:

grep -w "cat" file.txt
```


 

