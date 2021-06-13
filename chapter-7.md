# Chapter 7 - variables and comments
## What is a variable
A variable is something which can change, for example, the time of day, the amount of money in your bank, or the quantity of sweets in your pocket! <br>
In computing, variables are essential. They keep a track of the amount of unread notifications, the distance you've traveled and the amount of storage you have. <br>
In `C`, there are several different types of variables, which all hold a specific value.
### declaring a variable
A variable is declared like this:
```c
variable_type variable_name value;
```
A variable's name may consist of upper case letters (A-Z), lower case letters (a-z), numbers (0-9) and the underscore (_). <br>
A variable **cannot** begin with a number, `2cats` would not be a valid variable name. <br>
A variable should have a descriptive name: naming a variable `a` will not be useful as it will be difficult to determine what it does. <br>
Naming a variable `councilTaxToStillPay` will let you (as well as any other programmer know exactly what the variable's function is). <br>
As I already said, there are several different variable types, these will be covered in a moment, but each type is able to hold a specific value. <br>     
  
### int 
An int (integer), is a `whole number`, for example, `-9, 9, 99 and 999` <br>
The range of an int, on a 64bit device, is from `-2,147,483,648 to 2,147,483,647` these are the maximum and minimum values an int can hold. <br>
Don't worry, you don't  need to remember these values exactly. <br>
You could declare an int variable like this: <br>
```c
int age = 31; //create an int variable called age, holding the value 31
int moneyInMyBank = -50; //create an int variable called moneyInMyBank, holding a value of -50
```
You should now be able to create an int variable and assign it a variable
###char
A char (character), `, holds a letter, or a very small int value.  for example, `a, A, 9 and -o` <br>
The range of an char, on a 64bit device, is from `-128 to 127 ` these are the maximum and minimum values a char can hold. <br>
Don't worry, you don't  need to remember these values exactly. <br>
You could declare an char variable like this: <br>
```c
char age = 31; //create a char variable called age, holding the value 31
char moneyInMyBank = -50; //create an char variable called moneyInMyBank, holding a value of -50
char firstLetter = 'd'; //create an char variable called firstLetter, holding a value of 'd'
char lastLetter = 'a'; //create an char variable called lastLetter, holding a value of a
```
As you can see, we can also write an int variable as a char, but the way they are stored internally differs. Where a char variable holds 1 bite, an int variable holds 4. This means that a char variable uses less memory and therefore, it may be more desirable to use a char over an int in some circumstances. <br>
When holding a letter in a char variable, it is mandatory to use the `''` around the value. <br>
You should now be able to create a char variable and assign it a variable
###float and double 
A float (floating point), `, holds a decimal value, for example, `5.0, 11.1, -99.9 and 0.00001` <br>
The range of a float, on a 64bit device, is from `1.2E-38 to 3.4E+38` these are the maximum and minimum values a float can hold. <br>
  the `E` means how many times to the power the number is. For example, `1E4` is (10 times 10 times 10 times 10 times 10), which is `10000` <br>
a double (has a higher accuracy than a float), it has an accuracy of        15 decimal points, where a float will only have an accuracy of 7 decimal points. <br> <br>
The range of a double is 2.3E-308 to 1.7E+308 <br>
Don't worry, you don't  need to remember these values exactly. <br>
You could declare a  float and a double  variable like this: <br>
```c
float  age = 31.1; //create a float variable called age, holding the value 31.1
float moneyInMyBank = -50.00001; //create an float variable called moneyInMyBank, holding a value of -50.00001
double sizeOfAnAtom = 0.000000001; //create a double variable called sizeOfAnAtom, holding a value of 0.000000001
double smallDouble = 5.01; //create a double variable called smallDouble, holding a value of 5.01
```
You should now be able to create a float variable as well as a double variable and assign them a variable
###bool
A bool (Boolean), either holds 0 (for false) and 1 (for true).   <br>
You could declare a bool variable like this: <br>
```c
_Bool usesProcursus = 1; //creates a _Bool variable called usesProcursus and sets the value to 1 (true)  
_Bool male = 1; //creates a _Bool variable called isMale and sets the value to 1 (true)  
```
However, the `C99 standard` introduced the bool variable. To use this instead, use, 
```c
#include <stdbool.h> //this is required to use the `Bool variable  ` type
bool usesProcursus = 1; //creates a bool variable called usesProcursus and sets the value to 1 (true)  
bool male = 1; //creates a bool variable called isMale and sets the value to 1 (true)  
```
The same code above can also be written in a more easier form: <br>
```c
   #include <stdbool.h> //this is required to use the `Bool variable  ` type
bool usesProcursus = true; //creates a bool variable called usesProcursus and sets the value to 1 (true)  
bool male = true; //creates a bool variable called isMale and sets the value to 1 (true)  
```

You should now be able to create a bool variable and assign it a value.
###constants 
A constant variable is one which cannot be changed. In order to do this, simply place the `const` keyword before the program. For example <br>
```c
const int password = 123456; //creates a constant     int variable called password holding the value 123456
```
Now if we try to change the password, its not possible as there will be a compiler error. Using a const variable is useful as it ensures that we don't accidentally change a value. <br>
 Program 7.1 demonstrates this: <br>
```c
#include <stdio.h>
int main(void)
{
	const int password = 123456;
	password = 1234567;
	return 0;
}
```
I get the following output when trying to compile: <br>
```
program-7.1.c:5:11: error: cannot assign to variable 'password' with const-qualified type 'const int'
        password = 1234567;
        ~~~~~~~~ ^
program-7.1.c:4:12: note: variable 'password' declared const here
        const int password = 123456;
        ~~~~~~~~~~^~~~~~~~~~~~~~~~~
1 error generated
```
As you can see, by declaring the variable as a const, we lose the ability to change it. <br>
Although there are ways of defeating this, we won't be covering this just yet (as it defeats the purpose of declaring the variable as a constant). 
 
###the preprocessor 
The preprocessor reads the file and searches for the `#` symbol. When it finds it, it carries out a specific function. Note that a preprocessor directive is for the compiler, it is not part of the `C` source  code. For example: <br> 
```c
#include <stdio.h>
```
Tells the preprocessor to include the `stdio.h` header file, before begining compilation.
###The #define statement
We can use `#define in order to replace values. The way #deifne works is that when it finds a reference to that name, it replaces it with the actual value. For example: <br>
```c
#define PI 3.142
```
Now wherever there is a reference to `PI`, the compiler will replace that value with `3.142` <br>
When using #define, the compiler does not check for the correctness of the variable. 

###printing out variables 
consider program 7.2: 
```c
#include <stdio.h>
#include <stdbool.h>
int main(void)
{
	bool isMale = true;
	char firstLetter = 'A';
	int year = 2021;
	float distance  = 0.1; //in km 
	double particleSize = 0.0000000000001;
	printf("The bool value is %i \n The first letter is %c \n The year is %i \n The size of an atom is %f and the size of a particle is %f \n", isMale, firstLetter, year, distance, particleSize);
	return 0;
}
```
compiling this gives the following output: <br>
```
The bool value is 1 
 The first letter is A 
 The year is 2021 
 The size of an atom is 0.100000 and the size of a particle is 0.000000 

```

###program 7.3 - the same as program 7.2 but with comments
```c
#include <stdio.h> //stdio is needed for input and output (printf)
#include <stdbool.h> //needed for the bool variable type 
int main(void) /*the begining of the main fucntion. The program will begin execution from this. The int keyword specifies that the main function will return a whole number. The void keyword means that main (in our case) does not accept any arguments.*/    
{ //begining of main function 
	bool isMale = true; //creates a bool variable called isMale and assigns the value true (1)
	char firstLetter = 'A'; //creates a char variable called firstLetter and assigns the value A 
	int year = 2021; //creates an int variable called year, assigning  the value 2021     
	float distance  = 0.1; //in km /*creates a float variable called distance assigning it the value 0.1*/      
	double particleSize = 0.0000000000001; /*creates a variable called particleSize assigning it the value 0.0000000000001*/
	printf("The bool value is %i \n The first letter is %c \n The year is %i \n The size of an atom is %f and the size of a particle is %f \n", isMale, firstLetter, year, distance, particleSize);
/*This is another function. The printf() fucntion (print format), produces formatted output on the screen.
the symbol % followed by a letter is known as a conversion character. It tells the printf function that we're going to give it a variable of a specific format. 
 %i = int 
%c = char 
%i = bool 
%f = double and float
so, when printf sees the first %i, it replaces it with the first  value after the closing ". So, it replaces %i with the value of the variable  isMale
the \n is an example of an escape sequence Escape sequences carry out specific things, which would otherwise alter the code. The \n escape sequence tells the printf statement to place a new line.     .             
*/
	return 0; //give 0 back to the operating system, indicating success 
}
```
