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
A char variable is one which holds any letter, or numbers between 1 to 9. For example, `char firstLetter = 'a';` 
This creates a **char** variable called **firstLetter** holding the value **a**
**note:** The **''** are **required** around the value 
  
the final type of variable in c is known as the bool; this is either `true or false. When a value is true, it holds the value 1, when a value is false, it holds the value 0. if we need to use bool, then we need to include the **stdbool.h** header `#include <stdbool.h>`
Take a look at program 7.1 - a program to show multiple variables:
## Program 7.1
```c
#include <stdio.h>
#include <stdbool.h>
int main (void)
{
int age = 31;
float height = 180.5;
bool isMale = true; /*Although this is here, there is nothing useful you could do with this until you know more c - it is only here for completeness and a simple example*/   
char firstNameLetter = 'd';
printf("you are %i years old, You have a height of %f,  the first letter of your name is %c %i  \n", age, height, firstNameLetter, isMale);
return 0;
}
```
Go ahead and compile this program, call it `program 7.1` - remove the comments if you wish. 
The output will be like this:
```
you are 31 years old, You have a height of 180.500000,  the first letter of your name is d 1  
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
We have different conversion characters which represent different things. `%i` represents a **int** value as well as a **bool** value. `%f` represents a **float** value. `%c` represents a **char** value.
Let's take a look at program 7.2, - the same program as program 7.1 but with comments
```c
#include <stdio.h>
//includes stdio, needed for printf
#include <stdbool.h>
//includes stdbool, needed for bool
int main (void)
/*realise the int for main, this means that it expects an int as a return value*/ 
{
int age = 31;
/*Create a variable of type int, with called age, with the value 31*/ 
float height = 180.5;
/*Create a variable of type float called height, holding the value 180.5 
bool isMale = true; /*Although this is here, there is nothing useful you could do with this until you know more c - it is only here for completeness and a simple example
Creates a variable of type bool called isMale with the value true*/  
char firstNameLetter = 'd';
/*Creates a variable called firstNameLetter holding the value 'd' 
remember, the '' around the letter are necessary*/ 
printf("You are %i years old, You have a height of %f,  the first letter of your name is %c %i  \n", age, height, firstNameLetter, isMale);
/*This is the printf function
 the first conversion character is %i (int). The variable age is typed after the ", - this means that age should be substituted for the first int value.
The next conversion character is %f (float), and it is substituted for the variable height.
The next conversion character is %c (char) and it is substituted for the variable firstNameLetter
The final conversion character is %i (int) and it is substituted for the variable isMale.
The final thing (which you might not understand) is the \n. This is an escape sequence. When we place a \n in printf, then it puts us on a new line. If you were to remove the \n, the output wouldn't look all too appeasing. The puts function automatically places the \n for us*/ 
 
return 0;
//gives 0 back to main indicating success
}
```
remember how I said the value of variables can change? Program 7.1 didn't show this, but program 7.3 will:
## program 7.3
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
The output will be like this:
```
When a baby is born, it is 0 years old 
After one year, the baby is 1 years old 
After one more year, the baby is 2 years old 
```
as you can see, we can change the value of a variable to anything we like. 
This time, our printf function only has one %i conversion character as it only needs to substitute in the value for age once.
We can also perform calculations using printf - absorb program 7.4:
## Program 7.4:
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
The output will be something like this:
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
## program 7.5:
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
### Constants 
A constant is something which does not change. For example, the amount of planets in our solar system (there are 8 **please don't say that there are 9**). The amount of grams in a kilogram is constant (it is always 1000). 
In our program, it may be useful to create a constant - this prevents any accidental manipulation by you or someone else. For example, the maximum amount of levels in a game can't change - the amount of levels is constant. 
In c, we can declare a constant by simply placing a **const** in front of any value that is otherwise would be a variable. For example,
`const planetsInOurSolarSystem = 8;
 