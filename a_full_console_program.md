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

Yeah, we have achieved another small goal, let's do a commit.

```git
git add app.php
git commit -m "Organize the overall control structure"
```
