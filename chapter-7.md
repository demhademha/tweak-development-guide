# Chapter 7 - variables and constants 

## What is a variable 
A variable is something which can change. For example, a science experiment may require you to change the amount of solution used (the amount of solution is varied). The amount of food I eat is varied - it changes every day. <br>
In programs, values change all the time -  your score in a game may increase, or you may receive five new notifications. <br>
In c, variables are declared like this: 
```c
 variable_type variable_name value;
```
For example, <br>
```c
int age = 31;
```
Remember the int from chapter 6 (insert link to chapter 6 here), it holds int values (values which are hole numbers). For example, 9, 99 and -99. 9.9 is not an int as it contains a decimal (.) in it. <br>
The example above has created a variable of type **int** with the name  **age**, holding a value of **31**. <br>
**floats** are another type of variable. These variables can hold decimals, for example, `9.9, 9.99 and 9.999` 9 would not be a float - it would be a int.
The floats big brother **double** is able to hold a double accuracy compared to float (around 15 digits after the decimal number). 
An example of the double is this:
```c
double lengthOfAnAtom=0.00000000000001 //probably wrong here
```
A char variable is one which holds any letter, or numbers between 1 to 9. For example, `char firstLetter = 'a';` 
This creates a **char** variable called **firstLetter** holding the value **a**
**note:** The **''** are **required** around the value 
  
the final type of variable in c is known as the bool; this is either `true or false. When a value is true, it holds the value 1, when a value is false, it holds the value 0. if we need to use bool, then we need to include the **stdbool.h** header `#include <stdbool.h>`
There are several rules for variables. A variable may not start with a number, nor may it have special characters such as `&`. A variable may have the `_` (underscore) in it, for example, `number_of_files`. You may also use any letter in any order for example, `AGE`, `age` and `Age` - but you can do `age9` 
Variables should have descriptive names - allowing them to be easily identified.        
Take a look at program 7.1 - a program to show multiple variables:
## Program 7.1 - a program to show multiple variables 
```c
#include <stdio.h>
#include <stdbool.h>
int main (void)
{
int age = 31;
float height = 180.5;
double mass = 76.00000054;
bool isMale = true; /*Although this is here, there is nothing useful you could do with this until you know more c - it is only here for completeness and a simple example*/   
char firstNameLetter = 'd';
printf("you are %i years old, You have a height of %f, you have a mass of %f, the first letter of your name is %c %i  \n", age, height, mass, firstNameLetter, isMale);
return 0;
}
```
Go ahead and compile this program, call it `program 7.1` - remove the comments if you wish. 
The output will be like this:
```
you are 31 years old, You have a height of 180.500000, you have a mass of 76.000001, the first letter of your name is d 1  
```

As you can see, this program puts various things on the screen, but it uses **printf** not puts**.
printf(Print with format), allows us to put format on our screen - this includes variables and escape sequences (special combinations of letters and symbols  which means certain things).
in the printf function, when we type in `%` followed by a letter, we're telling printf to place a conversion character. At the end of our function, we substitute the conversion characters for their actual value. 
Consider this algebraic question - I promise it's not hard:
```
What is a*b when a=10 and b=5?
```
So when you first read the equation `a*b`, you don't know the values for these - however, you expect them to have something attached to them. When you read further on, you learn that a = 10 and b = 5. Only then, can you do a*b (5*10). This allows you to find he answer to the problem to be 50. 
Printf works like this in a way; it first reads the conversion characters, but it is unsure what they do, once it reaches the end of the statement, it can determine what each conversion character holds, substituting in the value. 
We have different conversion characters which represent different things. `%i` represents a **int** value as well as a **bool** value. `%f` represents a **float** value as well as a **double**. `%c` represents a **char** value.
Let's take a look at program 7.2, - the same program as program 7.1 but with comments
## program 7.2 -  - a program to show multiple variables but with comments  
```c
#include <stdio.h>
//includes stdio, needed for printf
#include <stdbool.h>
//includes stdbool, needed for bool
int main (void)
realise the int for main, this means that it expects an int as a return value
{
int age = 31;
/*Create a variable of type int, with called age, with the value 31*/ 
float height = 180.5;
/*Create a variable of type float called height, holding the value 180.5
double mass = 76.00000054;
/*Create a double variable called mass with the value 76.00000054
bool isMale = true; /*Although this is here, there is nothing useful you could do with this until you know more c - it is only here for completeness and a simple example
Creates a variable of type bool called isMale with the value true*/  
char firstNameLetter = 'd';
/*Creates a variable called firstNameLetter holding the value 'd' 
remember, the '' around the letter are necessary*/ 
printf("You are %i years old, You have a height of %f, you have a mass of %f, the first letter of your name is %c %i  \n", age, height, mass, firstNameLetter, isMale);
/*This is the printf function
 the first conversion character is %i (int). The variable age is typed after the ", - this means that age should be substituted for the first int value.
The next conversion character is %f (float), and it is substituted for the variable height.
The next conversion character is %f (double) and it is substituted for the variable mass
The next conversion character is %c (char) and it is substituted for the variable firstNameLetter
The final conversion character is %i (int) and it is substituted for the variable isMale.
The final thing (which you might not understand) is the \n. This is an escape sequence. When we place a \n in printf, then it puts us on a new line. If you were to remove the \n, the output wouldn't look all too appeasing. The puts function automatically places the \n for us*/ 
 
return 0;
//gives 0 back to main indicating success
}
```
remember how I said the value of variables can change? Program 7.1 didn't show this, but program 7.3 will:
## program 7.3 - changing variables 
```c
#include <stdio.h>
int main (void) 
{
int age = 0;
printf("When a baby is born, it is %i years old \n", age);
age = 1;
printf("After one year, the baby is %i years old \n", age);
age=2;
printf("After one more year, the baby is %i years old \n", age);
return 0;
}
```
Go ahead and compile this program - the output will be like this:
```
When a baby is born, it is 0 years old 
After one year, the baby is 1 years old 
After one more year, the baby is 2 years old 
```
as you can see, we can change the value of a variable to anything we like. 
This time, our printf function only has one %i conversion character as it only needs to substitute in the value for age once.
We can also perform calculations using printf - absorb program 7.4:
## Program 7.4 - calculations using printf
```c
#include <stdio.h>
int main (void) 
{
printf("1 + 2 is %i \n", 1 + 2);
printf("1 - 2 is %i \n", 1 - 2);
printf("1 / 2 is %i \n", 1 / 2);
//observe what happens to this line
printf("1 / 2 is %f \n", 1.0 / 2.0);
printf("1 * 2 is %i \n", 1 * 2);
return 0;
}
```
Can you guess the output? 
Go ahead and compile this program - the output will be something like this:
```
1 + 2 is 3 
1 - 2 is -1 
1 / 2 is 0 
1 / 2 is 0.500000 
1 * 2 is 2
```
As you can see, we can use the printf statement to hold the result of expressions. For example, 
`printf("1 * 2 is %i \n", 1 * 2);
This substitutes the equation (1*2) for the %i value.
Now you might be wondering, why the line 
`printf("1 / 2 is %i \n", 1 / 2);
Gives the output:
`1 / 2 is 0`
well, we know that `1/2` is not an int, it is a float (in case you didn't know, the result is 0.5). As a consequence, c converts our float (0.5) to an int (0)) - it has removed anything after the decimal.
Now, Imagine if I asked you to change the numbers to **5 and 10** - you could change each value individually, or you could use variables to do so. 
examine program 7.5 - make sure to compile it by typing, not **copying and pasting**
## program 7.5 - calculations using variables 
```c
#include <stdio.h>
int main (void) 
{
int numberOne = 1;
int numberTwo = 2;
printf("%i + %i is %i \n", numberOne, numberTwo, numberOne + numberTwo);
printf("%i - %i is %i \n", numberOne, numberTwo, numberOne  - 2);
printf("%i / %i is %i \n", numberOne, numberTwo, numberOne / numberTwo);
printf("%i * %i is %i \n", numberOne, numberTwo, numberOne * numberTwo);
return 0;
}
```
Although this program may look overwhelming, it actually simplifies what we were doing previously . Rather than defining each value on each line, we have defined two variables `numberOne` and `numberTwo` near the top of our program. This means that if we changed `numberOne` to `5` and `numberTwo` to `10` then we wouldn't have to change each line. - give it a go!
We can also declare variables like this:
```c
int a, b, c;
```
This creates 3 variables with type int - the first one is called a, the second is called b and the final is called c
We can also write variables like this:
```c
int a;
a = 10;
```
As you can see in this example, we declare the variable, but we don't give it a value (this is perfectly valid)
## Constants 
A constant is something which does not change. For example, the amount of planets in our solar system (there are 8 **please don't say that there are 9**). The amount of grams in a kilogram is constant (it is always 1000). 
In our program, it may be useful to create a constant - this prevents any accidental manipulation by you or someone else. For example, the maximum amount of levels in a game can't change - the amount of levels is constant. We may also use a constant to restrict an individual to only entering a certain amount of passcodes before being logged out of an account.
In c, we can declare a constant by simply placing a **const** in front of any value that   otherwise would be a variable. For example,
`const int PLANETSINOURSOLARSYSTEM = 8;`
This creates a const, with the type int, with the name `PLANETSINOURSOLARSYSTEM`. Note how the entire variable is capitalised? This helps us identify that this value is a const rather than a variable. Remember, you can name your variable however you want, as long as it is consistent and follows the rules above.     
If we try to change a const, the program will fail: peruse program 7.6:
## Program 7.6 - using const 
```c
#include <stdio.h>
int main (void) 
{
const int PLANETSINOURSOLARSYSTEM = 8;
//let's change this value 
PLANETSINOURSOLARSYSTEM = 9; //well not really 
printf("There are %i in our solar systen \n", PLANETSINOURSOLARSYSTEM);
return 0;
}
```
When you compile this program, you should be met with something like this:
program7.6.c:6:25: error: cannot assign to variable 'PLANETSINOURSOLARSYSTEM' with const-qualified type 'const int'
PLANETSINOURSOLARSYSTEM = 9; //well not really 
~~~~~~~~~~~~~~~~~~~~~~~ ^
program7.6.c:4:11: note: variable 'PLANETSINOURSOLARSYSTEM' declared const here
const int PLANETSINOURSOLARSYSTEM = 8;
~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
1 error generated.
```
as you can see, when using const, we are unable to change the value; we get an error if we do so. The clang compiler indicates which line we were trying to change, as well as the initial line in which the const value was set. 
### Settting consts with #define 
We may also set a constant value using the **#define** preprocessor directive. The #define is similar to the #include - they both tell the compiler (clang) to carry out a specific thing. In the case of #include it tells clang to fetch  the specified file before compiling the source code provided by you. The #define tells the compiler that it should expand (substitute) the provided values before compiling the program. Here's what a #define may look like:
```c
#define PLANETSINOURSOLARSYSTEM 9
```
we first write `#define` this creates the preprocessor directive. The word `PLANETSINOURSOLARSYSTEM` is now the name of our const every time `PLANETSINOURSOLARSYSTEM` is found by the compiler, it will be substituted for the next value `9`. 
To ensure you understand this, take a look at program 7.7 
### program 7.7 - about the planets of the solar system 
#include <stdio.h>
#define PLANETSINOURSOLARSYSTEM 9
int main (void)
{
printf("Once upon a time, there were %i planets in our solar system \n", PLANETSINOURSOLARSYSTEM);
printf("But then, one day, the evil scientists decided that the %ith isn't a planet; no - it is a dwarf planet - a tiny, tiny worthless ball \n", PLANETSINOURSOLARSYSTEM);
printf("There are now only %i planets in our solar system \n", PLANETSINOURSOLARSYSTEM - 1);
return 0;
} 
```
Go ahead and compile this program - the output should be as follows:
```
Once upon a time, there were 9 planets in our solar system 
But then, one day, the evil scientists decided that the 9th isn't a planet; no - it is a dwarf planet - a tiny, tiny worthless ball 
There are now only 8 planets in our solar system 
```
As you can see, the #define has substituted `PLANETSINOURSOLARSYSTEM` for the value 9; the last printf statement goes ahead and carries out `9-1=8`
Another thing to note is that #define doesn't belong in a function - it is usually placed at the top of a file, just after the #include statements.
## exercises
1. Fill in the following sentences - you will need to think of the words yourself. Once your done, the paragraph should make complete sense:
```
A variable is something which can ___(your response here). In c, there are ___(your response here) types of variables. Each variable is able to hold a specific ___(your response here). We first create a variable by declaring its ___(your response here). We then have to give our variable a unique ___(your response here) - we finally give our variable a ___(your response here). The symbol we use at the end of the variable is called a ___(your response here). 
In contrary, a const ___(your response here) changes. To create a const, we append the ___(your response here) keyword when we try to change the value of a const, the compilation ___(your response here). Consts are useful as they prevent ___(your response here) from the user or the programmer - one such example would be ___(your response here)   
We can also create variables using the ___(your response here). When we use the preprocessor directive, it causes the compiler in our case ___(your response here) to ___(your response here). When using this method, the values should be placed outside of any ___(your response here), preferably at the ___(your response here) of the program, just after the ___(your response here) preprocessor directives. When we use a const value, it is a usually a good idea to capitalise the names, this allows the values to be easily ___(your response here) from other values such as variables.
2. Write a program which uses any two numbers (such as 10 and 19), to calculate the values of their sum (number1+number2), their subtraction (number1-number2), a program to find the modulus (number1%number2), the division (number1/number2), the product (number1*number2). Use the printf statement to create a nice output 
3. Write a story using numbers, (such as program 7.7)
4. Which of these are correct variables: `__age`, `1age` `AGE` `a_ge`
