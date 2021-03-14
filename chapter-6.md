# Chapter 6 - Your first c program 
We've spent the last five chapters getting to the point where we actually code! Finally, we're here... Please take a seat!

## Let's get started 
1. Use your terminal app to ssh into your iDevice as the **mobile** user
2. Type `cd /tmp` (this will place you in the temporary folder)
3. Type `nano my-first-program.c` (this will create the file `my-first-program.c`) <br>
Note the `.c`, this is very important. The suffix of a file is known as an extension. Different files have different extensions. For example, a text file may have the ending `.txt`, a photo file may have the ending `.png` and a website file may have the ending `.html` <br>
The `.c` of the `my-first-program` tells the operating system that we want our file to be a c file. This is especially vital for our compiler (clang) as it will treat different extensions differently
4. **Type** the following code. **Do not copy and paste** This is because by copying and pasting, you do not actively learn. <br>

## Program 6.1
```c
#include <stdio.h>
int main(void) 
{
	puts("Hello World!");
	return 0;
}
```
Again, do not **copy and paste** actually type the code.

5. Once you're done typing, save your changes by typing `ctrl` + `x` + `enter`
6. Type the following: <br>
`clang my-first-program.c -o my-first-program` to compile the c program
7. If there is no output from your screen, that means you were successful. Otherwise, you have typed something wrong. Look again at program 6.1 and determine what you have done wrong.
8. Finally, type `./my-first-program`. This will give you the output <br>
`Hello World!`

## An explanation of program 6.1
### Comments 
A comment is a very useful thing. In life, we can use comments for many different things. For example, a teacher may leave comments on a students work to help them improve, a friend might comment on your clothes to prevent you from getting embarrassed when you go out. <br>
Just as comments are useful in the real world, they're also necessary for code. Lots of programs may span thousands of lines. It would be very difficult to remember what is happening at each part of the program. Comments allow you to write down what you are thinking or why you have done something. This may be crucial if you are working on a project with more than just one person; no two humans think the same. Comments also allow you to write things down for yourself - for example, if you need to fix a bug. <br>
There are two types of comments in c: single line comments and multi-line comments.

### Creating single line comments
A single line comment begins with two slashes `(//)` and it only spans on one line. 
```c
//I am a comment on a single line 
//I am also a comment on a single line
```
So, can you take a guess what we have done? <br>
If you guessed that we have created two comments, then you are correct.<br>
`//I am a comment on a single line`<br>
This creates a comment with the content `I am a comment on a single line` <br>
The next line: <br>
`//I am also a comment on a single line`<br>
Creates a comment called `I am also a comment on a single line`

### Creating a multi-line comment 
A multi-line comment is one which spans over several lines. It begins with `slash star` `(/*)` and ends with `star slash` `(*/)`. <br>
If we take the previous (single lined comments) and convert it into a multi-lined comment, it will look like this:
```c
/*I am a comment on a single line 
I am also a comment on a single line*/
```
Spot the difference?
I hope you can now see the two different types of comments work. <br>
Let's add comments to program 6.1 so you can understand what happened:

## Program 6.2
```c
#include <stdio.h>
/*We begin our first comment 
The #include <stdio.h> is a Preprocessor directive. It tells clang to include the file stdio.h from your sdk (in other words, $SDKROOT/usr/include/stdio.h - if you want to read the file, do cat $SDKROOT/usr/include/stdio.h 
the #include prevents us from manually copying and pasting the stdio file. Usually, the #include is placed at the top of our file
stdio stands for standa
