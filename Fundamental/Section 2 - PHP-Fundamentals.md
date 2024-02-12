# Section 2. PHP Fundamentals

## PHP Syntax
As a programming language, PHP has a set of rules that governs how you write programs.

### PHP code
Like HTML, you need to have the opening tag to start PHP code:

```php
<?php
```

If you mix PHP code with HTML, you need to have the enclosing tag:

```php
?>
```

For example:

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>PHP Syntax</title>
</head>
<body>
        <h1><?php echo 'PHP Syntax'; ?></h1>
</body>
</html>
```

However, if a file contains only PHP code, the enclosing tag is optional:

```php
<?php echo 'PHP Syntax';
```

### Case sensitivity

PHP is partially case-sensitive. Knowing what are case sensitive and what is not is very important to avoid syntax errors.

The following are case-insensitive in PHP:

-   PHP constructs such as *if*, *if-else*, *if-elseif*, *switch*, *while*, *do-while*, *etc*.
-   Keywords such as *true* and *false*.
-   *User-defined function* & *class names*.

On the other hand, variables are case-sensitive. e.g., ```$message``` and ```$MESSAGE``` are different variables.

### Statements

A PHP script typically consists of one or more statements. A statement is a code that does something, e.g., assigning a value to a variable and calling a function.

A statement always ends with a semicolon ```;```. The following shows a statement that assigns a literal string to the ```$message``` variable:

```php
$message = "Hello";
```

The above example is a simple statement. PHP also has a compound statement that consists of one or more simple statements. A compound statement uses curly braces to mark a block of code. For example:

```php
if( $is_new_user ) {
    send_welcome_email();
}
```

You don’t need to place the semicolon after the curly brace ```}```.

The closing tag of a PHP block ```?>``` automatically implies a semicolon ```;```. Therefore, you don’t need to place a semicolon in the last statement in a PHP block. For example:

```php
<?php echo $name ?>
```

In this example, the statement ```echo $name``` doesn’t need a semicolon. However, using a semicolon for the last statement in a block should work fine. For example:

```php
<?php echo $name; ?>
```

### Whitespace & line breaks

In most cases, whitespace and line breaks don’t have special meaning in PHP. Therefore, you can place a statement in one line or span it across multiple lines.

```php
<?php 
    echo $name; 
?>
```

## PHP Variables

### Define a variable

A variable stores a value of any type, e.g., a *string*, a *number*, an *array*, or an *object*.

A variable has a name and is associated with a value. To define a variable, you use the following syntax:

```php
$variable_name = value;
```

When defining a variable, you need to follow these rules:

-   The variable name must start with the dollar sign ```$```.
-   The first character after the dollar sign ```$``` must be a letter ```a-z``` or the underscore ```_```.
-   The remaining characters can be underscores, letters, or numbers.

PHP variables are case-sensitive. It means that ```$message``` and ```$Message``` variables are entirely different.

The following example defines a variable called ```$title```:

```php
<?php
$title = "PHP is awesome!";
```
To display the values of variables on a webpage, you’ll use the echo construct. For example:

```php
<?php
$title = "PHP is awesome!";
echo $title;
```

If you open the page, you’ll see the following message:

```bash
PHP is awesome!
```

Another shorter way to show the value of a variable on a page is to use the following syntax:

```php 

<?= $variable_name ?>
```
For example, the following shows the value of the ```$title``` variable in the heading:

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PHP Variables</title>
</head>
<body>
    <?php
		$title = 'PHP is awesome!';
	?>
    
    <h1><?= $title; ?></h1>
</body>
</html>
```

## PHP Constants

### Introduction to PHP constants

A constant is simply a name that holds a single value. As its name implies, the value of a constant cannot be changed during the execution of the PHP script.

To define a constant, you use the ```define()``` function. The  ```define()``` function takes the constant’s name as the first argument and the constant value as the second argument. For example:

```php
<?php 
define('WIDTH','1140px');
echo WIDTH
```
By convention, constant names are uppercase. Unlike a variable, the constant name doesn’t start with the dollar sign($).

By default, constant names are case-sensitive. It means that ```WIDTH``` and ```width``` are different constants.

### The const keyword
PHP provides you with another way to define a constant via the ```const``` keyword. Here’s the syntax:

```php
const CONSTANT_NAME = value;
```
In this syntax, you define the constant name after the ```const``` keyword. To assign a value to a constant, you use the assignment operator ```=``` and the constant value. The constant value can be scalar, e.g., a number, a string, or an array.

The following example uses the ```const``` keyword to define the ```SALES_TAX``` constant:

```php
<?php
const SALES_TAX = 1250;
echo $net_price;
```

## PHP Comments
Comments are important parts of the code. Comments provide useful information that will help you and other developers understand the meaning of the code more quickly later.

PHP supports two types of comments:

-   One-line comments
-   Multi-line comments

### One-line comments
The one-line comment is placed at the end of the line or at the current block.

A one-line comment starts with the pound ```#``` or double forward-slash ```//```. The rest of the text after the ```//``` is ignored by the PHP interpreter.

The following example uses the ```//``` for a one-line comment:

```php
<?php
$rate = 100;
$hours = 173;
$payout = $hours * $rate; // payout calculation
```

And the following example uses the ```#``` for a one-line comment:

```php
<?php
$title = 'PHP comment'; # set default title
```

### Multi-line comments
A Multi-line comment start with ```/*``` and end with ```*/```. For example:

```php
<?php
/*
   This is an example of a multi-line comment,
   which can span multiple lines.
*/
```
In practice, you use the multi-line comment when you need to span comments multiple lines.

## PHP var_dump
### Introduction to the PHP var_dump function

The ```var_dump()``` is a built-in function that allows you to dump the information about a variable. The ```var_dump()``` function accepts a variable and displays its type and value.

Suppose that you have a variable called ```$balance``` with a value of ```100```:

```php
<?php
$balance = 100;
```

To display the information of the ```$balance``` variable, you place it within parentheses that follow the ```var_dump``` function name like this:

```php
<?php
$balance = 100;
var_dump($balance);
```

If you open the page on the web browser, you’ll see the following output:

```bash
int(100)
```
The output shows the value of the variable ```100``` and its type ```int``` which stands for integer.

The following shows how to dump information about two variables $amount and $message:

```php
<?php

$balance = 100;
$message = 'Insufficient balance';

var_dump($balance);
var_dump($message);
```

Output:

```bash
int(100) string(20) "Insufficient balance"
```
