# Section 5 - Control flow

## PHP if


```php
if (expression) 
    statement;
```

The following flowchart illustrates how the `if` statement works:

![if-php](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-if.png)


```php
$isLoggedin = true;

if ($isLoggedin) 
	echo 'Welcome to system!';				// Welcome to system!
```

### Curly braces


```php
if (expression) {
	statement1;
	statement2;
   // more statement
}
```

Example:

```php
$isLoggedin = true;
$username;

if ($isLoggedin) {
    echo 'Welcome to system!';				// Welcome to system!
    $username = 'sohrab';
}
```

### Nesting if statements

```php
if ( expression1 ) {
    // do something
    if( expression2 ) {
        // do other things
    }
}
```
Example:

```php
$isLoggedin = true;
$canPublished = true;

if ($isLoggedin) {
    echo 'Welcome to system!';
	if ($canPublished) {
		echo 'Please published the pending posts';
	}
}
```

### Embed if statement in HTML

```php
<?php if ( expession) : ?>

    // HTML code here 

<?php endif; ?>
```

Example:

```php
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>PHP if Statement Demo</title>
</head>
<body>

  <?php $isLoggedin = true; ?>
  <?php if ( $isLoggedin ) : ?>

    <a href="#">Edit</a>

  <?php endif; ?>

  <a href="#">View</a> 

</body>
</html>
```

## PHP if else


```php
if ( expression ) {
    // code block
} else {
    // another code block
}
```

The following flowchart illustrates how the PHP if-else statement works:

![php-if-else](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-if-else.png)


```php
$isLoggedin = false;

if ( $isLoggedin ) {
    echo 'Welcome to system!';
} else {
    echo 'You are not authorized to access this page.'
}
```

### PHP if…else statement in HTML


```php
<?php if ( expression ): ?>

    // Show HTML code when expression is true

<?php else: ?>

    // Show HTML code when expression is false

<?php endif ?>
```

Example:

```php
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>PHP if Statement Demo</title>
</head>
<body>

  <?php $isLoggedin = true; ?>
  <?php if ($isLoggedin) : ?>

    <a href="#">Logout</a>

  <?php else: ?>

    <a href="#">Login</a> 

  <?php endif ?>

</body>
</html>
```

## PHP if elseif

```php
if (expression1) {
	statement;
} elseif (expression2) {
	statement;
} elseif (expression3) {
	statement;
}
```

The following flowchart illustrates how the PHP if-elseif statement works:

![php-elseif](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-if-elseif.png)


```php

$x = 10;
$y = 20;

if ($x > $y) {
	$message = 'x is greater than y';
} elseif ($x < $y) {
	$message = 'x is less than y';
} else {
	$message = 'x is equal to y';
}

echo $message;
```

### PHP if…elseif…else statement in HTML


```php
if (expression):
	statement;
elseif (expression2):
	statement;
elseif (expression3):
	statement;
else:
    statement;
endif;
```

## PHP Ternary Operator

The ternary operator is a shorthand for the `if...else` statement. Instead of writing this:

```php
if (condition) {
	$result = value1;
} else {
	$result = value2;
}
```

you can use this:

```php
$result = condition ? value1 : value2;
```

Example:

```php
$isLoggedin = false;

if ($isLoggedin) {
	$title = 'Logout';
} else {
	$title = 'Login';
}

echo $title;
```

Above example with Ternary Operator:

```php
$isLoggedin = false;

$title = $isLoggedin ? 'Logout' : 'Login';

echo $title;
```

### The shorthand ternary operator

```php
$result = $initial ?: $default;
```

Example:

```php
$path = '/about';
$url = $path ?: '/';

echo $url;							// /about
```

## PHP switch

The following illustrates the syntax of the switch statement:

```php
switch (expression) {
	case value1:
		// code block 1
		break;
	case value2:
		// code block 2
		break;
	case value3:
		// code block 3
		break;
	default:
		// default code block
}
```

The following flowchart illustrates how the `switch` statement works:

![php switch](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-switch.png)


```php
$role = 'subscriber';
$message = '';

if ('admin' === $role) {
	$message = 'Welcome, admin!';
} elseif ('editor' === $role) {
	$message = 'Welcome! You have some pending articles to edit';
} elseif ('author' === $role) {
	$message = 'Welcome! Do you want to publish the draft article?';
} elseif ('subscriber' === $role) {
	$message = 'Welcome! Check out some new articles.';
} else {
	$message = 'Sorry! You are not authorized to access this page';
}

echo $message;					// Welcome! Check out some new articles.
```

Above example with switch:

```php
$role = 'admin';
$message = '';

switch ($role) {
	case 'admin':
		$message = 'Welcome, admin!';
		break;
	case 'editor':
		$message = 'Welcome! You have some pending articles to edit';
		break;
	case 'author':
		$message = 'Welcome! Do you want to publish the draft article?';
		break;
	case 'subscriber':
		$message = 'Welcome! Check out some new articles.';
		break;
	default:
		$message = 'You are not authorized to access this page';
}

echo $message;
```

### Combining cases

```php
$message = '';
$role = 'author';

switch ($role) {
	case 'admin':
		$message = 'Welcome, admin!';
		break;
	case 'editor':
	case 'author':
		$message = 'Welcome! Do you want to create a new article?';
		break;
	case 'subscriber':
		$message = 'Welcome! Check out some new articles.';
		break;
	default:
		$message = 'You are not authorized to access this page';
}

echo $message;
```

### PHP switch statement’s alternative syntax


```php
switch (expression):
	case value1:
		// code block 1
		break;
	case value2:
		// code block 2
		break;

	default:
		// default code block
		break;
endswitch;
```

## PHP for

```php
for (start; condition; increment) {
	statement;
}
```

The following flowchart illustrates how the `for` statement works:

![php-for](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-for.png)

### PHP for statement example


```php
$total = 0;

for ($i = 1; $i <= 10; $i++) {
	$total += $i;
}

echo $total;							// 55
```

### Alternative syntax of the for statement

```php
for (start; condition; increment):
   statement;
endfor;
```

Example:

```php
$total = 0;

for ($i = 1; $i <= 10; $i++):
	$total += $i;
endfor;

echo $total;							// 55
```

## PHP while

```php
while (expression) {
	statement;
}
```

The following flowchart illustrates how the while statement works:

![php-while](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-while.png)


```php
$total = 0;
$number = 1;

while ($number <= 10) {
	$total += $number;
	$number++;
}

echo $total;							// 55
```

### The alternative syntax for the PHP while loop

```php
while (expression):
	statement;
endwhile;
```

Example:

```php
$total = 0;
$number = 1;

while ($number <= 10) :
	$total += $number;
	$number++;
endwhile;

echo $total;							// 55
```

## PHP do…while

```php
do {
	statement;
} while (expression);
```

The following flowchart illustrates how the `do...while` statement works:

![php-do-while](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-do-while.png)


### PHP do…while loop statement example


```php
$i = 0;
do {
 echo $i;
} while ($i > 0);
```
Other example:

```php

$i = 10;

do {
    echo $i  . "\n";
    $i--;
} while ($i > 0);
```

## PHP break

The `break` statement terminates the execution of the current `for`, `do...while`, `while`, or `switch` statement. This tutorial focuses on how to use the break statement with the loops.


### Using PHP break statement in a for loop

```php
for ($i = 0; $i < 10; $i++) {
	if ($i === 5) {
		break;
	}
	echo "$i\n";
}
```

Output:

```
0
1
2
3
4
```

## PHP continue

The `continue` statement is used within a loop structure such as `for`, `do...while`, and `while` loop. The `continue` statement allows you to immediately skip all the statements that follow it and start the next iteration from the beginning.

```php
for ($i = 0; $i < 10; $i++) {
	if ($i % 2 === 0) {
		continue;
	}
	echo "$i\n";
}
```

Output:

```
1
3
5
7
9
```
