# Chapter 6 - Your first c program 
We've spent the last five chapters getting to the point where we actually code! Finally, we're here... Please take a seat!

## Let's get started 
1. Use your terminal app to ssh into your iDevice as the **mobile** user
2. Type `cd /tmp` (this will place you in the temporary folder)
3. Type `nano program-6.1.c` (this will create the file `program-6.1.c`) <br>
Note the `.c`, this is very important. The suffix of a file is known as an extension. Different files have different extensions. For example, a text file may have the ending `.txt`, a photo file may have the ending `.png` and a website file may have the ending `.html` <br>
The `.c` of the `my-first-program` tells the operating system that we want our file to be a c file. This is especially vital for our compiler (clang) as it will treat different extensions differently.
4. **Type** the following code. **Do not copy and paste**. This is because by copying and pasting, you do not actively learn. <br>

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

5. Once you're done typing, save your changes by pressing `ctrl` + `x`, then `y` and `enter`
6. Type the following: <br>
`clang program-6.1.c -o program-6.1`
7. If there is no output from your screen, that means you were successful. Otherwise, you have typed something wrong. Look again at program 6.1 and determine what you have done wrong.
8. Finally, type `./program-6.1`. This will give you the output <br>
`Hello World!` <br>
So, you have just **compiled** your first program (remember that word). You first use **nano** to create the file (nano is your editor), you then typed your program, saved it, and compiled it. Remember that when you compile, you take the human readable code and turn it into machine code (the language the computer understands). To view this machine code, do: <br> 
`cat ./program-6.1`
The output may be something like this (however, it may be different): <br>
```
����
    �� H__PAGEZERO�__TEXT� __text__TEXT@8@�__stubs__TEXTx
                                                         �
�__unwind_info__TEXT�H��__DATA_CONST�@�@__got__DATA_CONST��__DATA�@�@__la_symbol_ptr__DATA�__data__DA�H__LINKEDIT@�"? 00?h�D
                                                                                                                            P� 
                                                                                                                               /usr/lib/dyld?�H��-0
`��F�dG12 *(�?@,?@@
                   8?<
                      /usr/lib/libSystem.B.dylib&)h�����{��C�R�����>��
                                                                      ���
                                                                         @���{A�����_� �0X�1 ��G�� �pX�P?���Hello World!@44y4
                                                                                                                             �#Q@dyld_stub_binderQr
�s@_puts�__mh_execute_header!main%�� �@" __mh_execute_header_main_putsdyld_stub_binder__dyld_private��
                                                                                                      ��,?����
                                                                                                              ��4
                                                                                                                 a�Qm�=���P�ߜ�:��t5m��ʸ�������׷5���
R�7�9���&�^{Ao'��=�S�kO�͕�{���=�S�kO�͕�{���=�S�kO�͕�{���=�            S�kO�͕�{���=�S�kO�͕�{��
P�]�Q�%��5���=�S�kO�͕�{���=�S�kO�͕�{���=�S�kO�͕�{���=�S�kO�͕�{���sL�}�hj�K�}qf7թ��=�S�kO�͕�{���=�S�kO�͕�{���=�S�kO�͕�{�ÎY�>    OZ<,�3l6�!����
                                                                                                                                      x��
                                                                                                                                         da
subject.CN
*�H��cd��qqA<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
        <key>platform-application</key>
        <true/>
        <key>com.apple.private.security.no-container</key>
        <true/>
        <key>com.apple.private.skip-library-validation</key>
        <true/>
</dict>
</plist>
��
  ��4 
�}��&uf���Xo��f����kOX�|�|z�ڽ�H�,����Xo��f����kOX�|�|z�ڽ�H�,����Xo��f����kOX�|�|z�ڽ�H�,����Xo��f����kOX�|�|z�ڽ�H�,����Xo��f����kOX�|�|z�ڽ�H�,����Xo
��f����kOX�|�|z�ڽ�H�,�#}��0Xd/"o���+67aI��F��Ci����Xo��f����kOX�|�|z�ڽ�H�,����Xo��f����kOX�|�|z�ڽ�H�,����Xo��f����kOX�|�|z�ڽ�H�,����Xo��f����kOX�|�
|z�ڽ�H�,�>y'�"�*N>�Ioh
                      v���Y�ۥ�2��_�ݭ��Xo��f����kOX�|�|z�ڽ�H�,����Xo��f����kOX�|�|z�ڽ�H�,����Xo��f����kOX�|�|z�ڽ�H�,�FW�փc�
y�g�\�W��{# �,�����%                                                                                                                               
```
As you can see, that would be extremely hard to learn and it would take forever to type. The **clang** compiler has taken our c code and converted it into that machine code! <br>
Whenever you are told to compile your code, make sure to first use nano to type it and then clang to compile it with the command: <br>
`clang program_name.c -o program_name`<br>
The first part tels clang the name of the file to compile (our c file), the second command after the `-o` tells clang what the name of the compiled program should be. If `-o` is not specified, then the program is called `a.out`

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
stdio stands for standard input output - it provides us with many ways to get input and output.
*/

int main(void)
/*This creates a function called main which returns an int value. 
an int is a hole number, for example, 1, 77, -95
9.9 is not an example of an int as it holds a dev mail decimal value.
A function holds lots of statements in it. You can think of it as bread - which holds the spread. Anything inside of the {} are part of the function - they belong to it. A statement is anything which has a ; at its end - think of a ; as a full stop in English - they tel you where the next sentence begins. .
The main function is where any c program begins. It tells the program to begin executing (running) from this function. Large programs may consist of hundreds of functions however, the program will only run from the main function. 
The (void) part tells the main function that we do not want to pass it any parameter. Normally, we would pass parameters (which are values) between the () however, we are not going to in this example as they're not needed.*/
{
	/*This is where the main function begins; anything between the {} are part of the main function.*/
	puts("Hello World!");
	/*This is another function. The puts function (put string) places characters onto the screen. Anything placed within the "" will be placed on the screen. it is also a statement - it has a ; at the end of it.*/
	return 0;
/*This returns the value 0 to the main function. Normally, the value 0 indicates success. Any other value indicates failure.*/
}
//This ends the main function 
```
Go ahead and compile program 6.2! The output will be just the same as program 6.1. **Can** you try to write your own comments? Explaining what is happening on each line?     
Another thing to note is that a single line comment can be written like this:
```c
puts("Hello World!"); // This is a function
```
Over this:
```c
puts("Hello World!");
// This is a function
```
Comments can even be useful if we need to figure out what is wrong with a program, for example, they allow us to prevent certain statements from running, for example: <br>
```c
//puts("Hello World!");
```
  this will prevent the `puts` statement from running - if you compiled a program with `puts` commented out (a comment before puts began), then you would not get any output.                
## Changing the output of our program 
Program 6.1 prints `Hello World!` to the console. It would not be very practical if every program printed the same thing to the screen. <br>
Take a look at program 6.3.

## Program 6.3:
```c
#include <stdio.h>
int main(void)
{
	puts("Goodbye Cruel World!");
/*As you can see, we've changed what is inside of the "" - this will cause the output of the program to change*/
	return 0;
	}
```
The output will be: <br>
`Goodbye Cruel World!`

## Writing multiple lines of output 
It may also be useful to place multiple lines of output on the screen. To do this, take a look at program 6.4.

## Program 6.4:
```c
#include <stdio.h>
int main(void)
{
	puts("I am a line");
	puts("I am also a line");
	return 0;
}
```

The output of this program will be:
```
I am a line
I am also a line
```

You should now understand what the extension is for a c program, what and how to use comments, what a Preprocessor directive is, what an int is, what a function is, what a statement is, what `puts` is and how it works and what return does.

## Exercises
1. What is the file extension for a c file?
2. What is a function? - can you think of an analogy to describe it?
3. What function do all c programmes start from?
4. What is an int?
5. True or false: 1.5 is an int.
6. What is the function of puts?
7. What return value indicates success?
8. Summarise what a comment is and how it works in no more than 100 words.
9. Try to code program 6.1 without looking - memorise how to write it off by heart.
10. Write program 6.1, inserting your own comments to explain what is happening on each line.
11. Write a program which shows your name, the date and the time. The output should look like this:
```
My name is demhademha
Today it is Sunday
The time right now is 13:00
```