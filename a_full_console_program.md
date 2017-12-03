# A full console program

## Contents

### Analyze and define the features of the dictionary

Before we start our project, we need know what to do, what features of the dictionary should have.

> Here are the features of the dictionary for the first version:

1. Add or update a vocabulary
2. List vocabularies from the dictionary.
3. Find a vocabulary by its headword in the dictionary.
4. Remove a vocabulary by its headword out of the dictionary.

### Analyze and design the overall architecture of the program.

> Here are the main steps for the program:

1. Run the program
2. Display main menu which lists the actions as below
    1. Add or update a vocabulary
    2. List vocabularies
    3. Find a vocabulary by its headword
    4. Remove a vocabulary by its headword
    5. Quit the program
3. Input the leading number to execute the action
	* Execute 1-4 actions, when it's finished and it returns to main menu
	* Execute the 5th action, quit the program

> Try to use enough helpful information to guide users.

Since we run this first version program on the console, there's no UI. We need think about how to interact with the console.


### Use comments to describe the main procedure of the program

Let's start our proejct.

```
mkdir dictionary
cd dictionary
touch app.php
```
Before we write codes, it's a good habit to describe the steps which we will go.

```php
<?php
//app.php

//display the main menu 

//get the keyboard input

//according to the input, execute the action
    //input 1 to add or update action
    
    //input 2 to list action
    
    //input 3 to find action
    
    //input 4 to remove action
    
    //input 5 to exit the program
    
    //if the input does not equal the above, give an invalid operation alert
```
Not much work, but it's a small task we finished. Do a commit for this small task using git.

```git
git init
git add app.php
git commit -m "Describe the main procedure of the program"
```

### Organize the overall control structure and define the functions

Follow the steps, start writing codes.

1. If the step is easy to implement, write logics directly.
2. If the step is complex or needs lots of coding, define a function to be implemented later.

```php
<?php


//display the main menu 
display_main_menu();

//get the keyboard input
$input = intval(get_input());


//according to the input, execute the action
switch(intval($input))
{
    //input 1 to add or update action
    case 1:
        add_action();
        break;

    //input 2 to list action
    case 2:
        list_action();
        break;

    //input 3 to find action
    case 3:
        find_action();
        break;

    //input 4 to remove action
    case 4:
        remove_action();
        break;

    //input 5 to exit the program
    case 5:
        quit();
        break;

    //if the input does not equal the above, give an invalid operation alert
    default:
        alert();
        
}

```

> switch statement

The switch statement is similar to a series of IF statements on the expression. In many occasions, you want to compare the same varialbe (or expression) with many different values, and execute a different piece of code depending on which value it equals to. This is what exactly the switch statement if for.

> intval function

Get the integer value of a variable.

As we can see, we need a loop for the whole procedure.

```php

//loop until the experssion of WHILE is not true
while(true)
{
	//display the main menu 
	display_main_menu();

	//get the keyboard input
	$input = intval(get_input());


	//according to the input, execute the action
	switch(intval($input))
	{
		....
	}
}

```

> while statement 

The meaning of a while statement is simple. It tells PHP to execute the nested statement(s) repeatedly, as long as the while expression evaluates to TRUE. 

> infinite loop

If the program is running into the infinite loop without exit logic, you can press Ctrl+c break out. Anyway, you should prevent this situation happens.

Yeah, we have achieved another small goal, let's do a commit.

```git
git add app.php
git commit -m "Organize the overall control structure"
```
### Declare functions of the overall program

It's a good habit to write documentation in programming.


```php
<?php
...

/**
 * Display main menu for selecting one action to execute
 * 
 */
function display_main_menu()
{

}

...

/**
 * Listen and get keyboard input
 * 
 * @return string a single line string terimated with "\n"
 */
function get_input()
{

}

...

```

> PHP standard

For coding standard, check The PHP Standard Recommendation (PSR) which is a PHP specification published by the PHP Framework Interop Group.

As a newbie, you can start following the [PSR-1](http://www.php-fig.org/psr/psr-1/) which is for Basic Coding Standard.

For documentation standard, check [PHPDOC](https://www.phpdoc.org/)

Let's finish this small step.

```git
git add app.php
git commit -m "Declare functions of the overall program"
```

### Impelment displaying menu and exiting the program

Functions are still blank, we need write implementation for these functions.

```php
...

/**
 * Display main menn for selecting one action to execute
 * 
 */
function display_main_menu()
{
    //define an array for holding action descriptions
    $actions = [
        "Add or update a vocabulary",
        "List vocabularies",
        "Find the vocabulary by headword",
        "Remove the vocabulary by headword",
        "Quit the program"
    ];

    echo "This is my own dictionary\n";

    echo "Enter the indicator in [?] to execute the action\n\n";

    //iterate $actions to display the action description
    for($i=0; $i<count($actions); $i++)
    {
        echo sprintf("[%s]%s\n", $i+1, $actions[$i]);
    }

    echo "\n";
}

...

/**
 * Exit the program
 */
function quit()
{

    echo "Thanks to use my dictionary. Good bye.\n";

    //exit the program
    exit(0);


}

/**
 * Alert when enter the wrong action indictor
 *
 */
function alert()
{

    //strtoupper will convert characters in the string to uppercase
    //vice versa, use strtolower to get lowercase
    echo strtoupper("Please enter the right number for the action you want\n\n");


}

/**
 * Listen and get keyboard input
 *
 * @return string a single line string terimated with "\n"
 */
function get_input()
{

    //open the stream for listening keyboard input
    $handle = fopen("php://stdin", "r");
    //wait and get the input when enter the return
    $input = fgets($handle);
    //close the stream
    fclose($handle);


    return $input;


}

...

```

> array data type

An array in PHP is actually an ordered map. A map is a type that associates values to keys.

Create an array using [] or array().

```
$fruits = array("apple", "banana", "orange");
```

Get the number of elements in an array using `count` function

Access the element in an array using index or associated key, for example $fruits[0]. Default, index is start from 0.

> [sprintf](http://php.net/manual/en/function.sprintf.php) function

Get a formatted string. %s means a string placeholder for the arguments which are starting form second position.

> build-in functions

If we wish the program can do more, we need learn more functions which PHP already prepares for you.

```git
git add app.php
git commit -m "Display main menu, quit the program and invalid operation alert done"
```