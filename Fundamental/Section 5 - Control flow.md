# Section 5 - Control flow

## PHP if

### Introduction to the PHP if statement

The `if` statement allows you to execute a statement if an expression evaluates to `true`. The following shows the syntax of the `if` statement:

```php
if (expression) 
    statement;
```

In this syntax, PHP evaluates the `expression` first. If the `expression` evaluates to `true`, PHP executes the `statement`. In case the expression evaluates to `false`, PHP ignores the `statement`.

The following flowchart illustrates how the `if` statement works:

![if-php](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-if.png)

The following example uses the `if` statement to display a message `if` the `$is_admi`n variable sets to `true`:

```php
$is_admin = true;
if ($is_admin)
    echo 'Welcome, admin!';
```

Since `$is_admin` is `true`, the script outputs the following message:

```
Welcome, admin!
```

#### Curly braces

If you want to execute multiple statements in the `if` block, you can use curly braces to group multiple statements like this:

```php
if (expression) {
   statement1;
   statement2;
   // more statement
}
```

The following example uses the if statement that executes multiple statements:

```php
$can_edit= false;
$is_admin = true;

if ($is_admin) {
   echo 'Welcome, admin!';
   $can_edit = true;
}
```

In this example, the `if` statement displays a message and sets the `$can_edit` variable to `true` if the `$is_admin` variable is `true`.

It’s a good practice to always use curly braces with the `if` statement even though it has a single statement to execute like this:

```php
if ( expression ) {
   statement;
}
```

#### Nesting if statements

It’s possible to nest an `if` statement inside another `if` statement as follows:

```php
if ( expression1 ) {
    // do something
    if( expression2 ) {
        // do other things
    }
}
```

The following example shows how to nest an `if` statement in another `if` statement:

```php
$is_admin = true;
$can_approve = true;

if ($is_admin) {
	echo 'Welcome, admin!';
	if ($can_approve) {
		echo 'Please approve the pending items';
	}
}
```

#### Embed if statement in HTML

To embed an `if` statement in an HTML document, you can use the above syntax. However, PHP provides a better syntax that allows you to mix the if statement with HTML nicely:

```php
<?php if ( expession) : ?>

    // HTML code here 

<?php endif; ?>
```

The following example uses the `if` statement that shows the edit link if the `$is_admin` is `true`:

```php
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>PHP if Statement Demo</title>
</head>
<body>

  <?php $is_admin = true; ?>
  <?php if ( $is_admin ) : ?>

    <a href="#">Edit</a>

  <?php endif; ?>

  <a href="#">View</a> 

</body>
</html>
```

Since the `$is_admin` is `true`, the script shows the Edit link. If you change the value of the `$is_admin` to `false`, you won’t see the Edit link in the output.

## PHP if else

### Introduction to PHP if-else statement

Sometimes, you want to execute another code block if the `expression` is `false`. To do that, you add the `else` clause to the `if` statement:

```php
if ( expression ) {
    // code block
} else {
    // another code block
}
```

In this syntax, if the `expression` is `true`, PHP executes the code block that follows the if clause. If the `expression` is `false`, PHP executes the code block that follows the `else` keyword.

The following flowchart illustrates how the PHP if-else statement works:

![php-if-else](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-if-else.png)

The following example uses the `if...else` statement to show a message based on the value of the `$is_authenticated` variable:

```php
$is_authenticated = false;

if ( $is_authenticated ) {
    echo 'Welcome!';
} else {
    echo 'You are not authorized to access this page.'
}
```

In this example, the `$is_authenticated` is `false`. Therefore, the script executes the code block that follows the `else` clause. And you’ll see the following output:

```
You are not authorized to access this page.
```

#### PHP if…else statement in HTML

Like the `if` statement, you can mix the `if...else` statement with HTML nicely using the alternative syntax:

```php
<?php if ( expression ): ?>

    // Show HTML code when expression is true

<?php else: ?>

    // Show HTML code when expression is false

<?php endif ?>
```

Note that you don’t need to place a semicolon `(;)` after the `endif` keyword because the `endif` is the last statement in the PHP block. The enclosing tag `?>` automatically implies a semicolon.

The following example uses the `if...else statement` to show the logout link if `$is_authenticated` is `true`. If the `$is_authenticated` is `false`, the script shows the login link instead:

```php
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>PHP if Statement Demo</title>
</head>
<body>

  <?php $is_authenticated = true; ?>
  <?php if ($is_authenticated) : ?>

    <a href="#">Logout</a>

  <?php else: ?>

    <a href="#">Login</a> 

  <?php endif ?>

</body>
</html>
```

## PHP if elseif

### Introduction to the PHP if elseif statement

The `if` statement can have one or more optional `elseif` clauses. The `elseif` is a combination of `if` and `else`:

```php
if (expression1) {
	statement;
} elseif (expression2) {
	statement;
} elseif (expression3) {
	statement;
}
```

PHP evaluates the `expression1` and execute the code block in the if clause if the `expression1` is `true`.

If the `expression1` is `false`, the PHP evaluates the `expression2` in the next `elseif` clause. If the result is `true`, then PHP executes the statement in that `elseif` block. Otherwise, PHP evaluates the `expression3`.

If the `expression3` is `true`, PHP executes the block that follows the `elseif` clause. Otherwise, PHP ignores it.

![php-elseif](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-if-elseif.png)

The following example uses the` if elseif` statement to display whether the variable `$x` is greater than `$y`:

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

Output:

```
x is less than y
```

#### PHP if elseif alternative syntax

PHP also supports an alternative syntax for the `elseif` without using curly braces like the following:

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

### Introduction to the PHP ternary operator

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

How it works.

-   First. PHP evaluates the `condition`. If it’s `true`, the right-hand expression returns the `value1`; otherwise, it returns the `value2`.
-   Second, PHP assigns the result of the right-hand expression to the `$result` variable.

PHP ternary operator example

```php
$is_user_logged_in = false;

if ($is_user_logged_in) {
	$title = 'Logout';
} else {
	$title = 'Login';
}
```

In this example, the `$title` will be `'Login'` because the `$is_user_logged_in` is set to `false`. The code is quite lengthy. And you can make it shorter by using the ternary operator as follows:

```php
$is_user_logged_in = false;

$title = $is_user_logged_in ? 'Logout' : 'Login';
```

#### The shorthand ternary operator

```php
$result = $initial ?: $default;
```

In this syntax, PHP evaluates `$initial` in the boolean context. If `$initial` is `true`, PHP assigns the value of the `$initial` to the `$result` variable. Otherwise, it assigns the `$default` to the `$result` variable.

```php
$path = '/about';
$url = $path ?: '/';

echo $url; // /about
```

Output:

```
/about
```

## PHP switch

### Introduction to the PHP switch statement

When the value of a single variable determines the number of different choices, you can use the `if...elseif` statement.

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

The `switch` statement compares an `expression` with the value in each case.

If the expression equals a value in a case, e.g., `value1`, PHP executes the code block in the matching case until it encounters the first `break` statement.

If there’s no match and the `default` is available, PHP executes all statements following the `default` keyword.

In case the `default` is not specified, and there’s no match, the control is passed to the statement that follows the `switch` statement.

The following flowchart illustrates how the `switch` statement works:

![php switch](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-switch.png)

Suppose that you’re building a website whose users have many roles like admin, editor, author, and subscriber.

The following example uses an `if elseif` statement to display a different message based on the role of the user:

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

echo $message;
```

Output:

```
Welcome! Check out some new articles.
```

When the value of a single variable specifies the number of different choices, it’s much cleaner to use the `switch` statement like this:

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

#### Combining cases

Since PHP executes the `switch` statement from the matching case label till it encounters the `break` statement, you can combine several cases in one.

The following example uses the switch statement and combines the cases of `'editor'` and `'author'`:

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
Output:

```
Welcome! Do you want to create a new article?
```

In this example, if the `role` is `editor` or `author`, it’ll show the same message.

#### PHP switch statement’s alternative syntax

PHP also supports the alternative syntax for the `switch` statement as follows:

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

### Introduction to PHP for statement

The `for` statement allows you to execute a code block repeatedly. The syntax of the `for` statement is as follows:

```php
for (start; condition; increment) {
	statement;
}
```

How it works.

-   The `start` is evaluated once when the loop starts.
-   The `condition` is evaluated once in each iteration. If the `condition` is `true`, the `statement` in the body is executed. Otherwise, the loop ends.
-   The `increment` expression is evaluated once after each iteration.

PHP allows you to specify multiple expressions in the `start`, `condition`, and `increment` of the `for` statement.

In addition, you can leave the `start`, `condition`, and `increment` empty, indicating that PHP should do nothing for that phase.

The following flowchart illustrates how the `for` statement works:

![php-for](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-for.png)

#### PHP for statement example

The following shows a simple example that adds numbers from 1 to 10:

```php
$total = 0;

for ($i = 1; $i <= 10; $i++) {
	$total += $i;
}

echo $total;
```

Output:

```
55
```

#### Alternative syntax of the for statement

The for statement has the alternative syntax as follows:

```php
for (start; condition; increment):
   statement;
endfor;
```

The following script uses the alternative syntax to calculate the sum of 10 numbers from 1 to 10:

```php
$total = 0;

for ($i = 1; $i <= 10; $i++):
	$total += $i;
endfor;

echo $total;
```

Output:

```
55
```

## PHP while

### Introduction to the PHP while statement

The `while` statement executes a code block as long as an `expression` is `true`. The syntax of the `while` statement is as follows:

```php
while (expression) {
	statement;
}
```

How it works.

-   First, PHP evaluates the `expression`. If the result is `true`, PHP executes the `statement`.
-   Then, PHP re-evaluates the `expression` again. If it’s still `true`, PHP executes the statement again. However, if the `expression` is `false`, the loop ends.

If the `expression` evaluates to `false` before the first iteration starts, the loop ends immediately.

Since PHP evaluates the `expression` before each iteration, the `while` loop is also known as a pretest loop.

The following flowchart illustrates how the while statement works:

![php-while](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-while.png)

#### PHP while loop example

The following example uses a `while` loop to add whole numbers from 1 to 10:

```php
$total = 0;
$number = 1;

while ($number <= 10) {
	$total += $number;
	$number++;
}

echo $total;
```

Output:

```
55
```

#### The alternative syntax for the PHP while loop

The alternative syntax for the while statement is as follows:

```php
while (expression):
	statement;
endwhile;
```

The following uses the alternative syntax of the `while` statement to sum the whole numbers from 1 to 10.

```php
$total = 0;
$number = 1;

while ($number <= 10) :
	$total += $number;
	$number++;
endwhile;

echo $total;
```

Output:

```
55
```

## PHP do…while

### Introduction to PHP do…while loop statement

The PHP `do...while` statement allows you to execute a code block repeatedly based on a Boolean expression. Here’s the syntax of the PHP `do-while` statement:

```php
do {
	statement;
} while (expression);
```

Unlike the `while` statement, PHP evaluates the `expression` at the end of each iteration. It means that the loop always executes at least once, even the `expression` is `false` before the loop enters.

The following flowchart illustrates how the `do...while` statement works:

![php-do-while](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-do-while.png)

The differences between the `do...while` and `while` statements are:

-   PHP executes the statement in `do...while` at least once, whereas it won’t execute the statement in the `while` statement if the `expression` is false.
-   PHP evaluates the `expression` in the `do...while` statement at the end of each iteration. Conversely, PHP evaluates the `expression` in the `while` statement at the beginning of each iteration.

#### PHP do…while loop statement example

In the following example, the code block inside the `do...while` loop statement executes precisely one time.

```php
$i = 0;
do {
 echo $i;
} while ($i > 0);
```

The code inside the loop body executes first to display the variable `$i`. Because the value of the `$i` is 0, the condition is met, the loop stops.

In the following example, the code block inside the `do...while` loop executes ten times:

```php

$i = 10;

do {
    echo $i  . "\n";
    $i--;
} while ($i > 0);
```

## PHP break

### Introduction to the PHP break statement.

The `break` statement terminates the execution of the current `for`, `do...while`, `while`, or `switch` statement. This tutorial focuses on how to use the break statement with the loops.

Typically, you use the `break` statement with the `if` statement that specifies the condition for the terminating loop.

The `break` statement accepts an optional number that specifies the number of nested enclosing structures to be broken out of.

If you don’t specify the optional number, it defaults to `1`. In this case, the `break` statement only terminates the immediate enclosing structure.

#### Using PHP break statement in a for loop

The following example illustrates how to use the `break` statement in a `for` loop:

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

### Introduction to the PHP continue statement

The `continue` statement is used within a loop structure such as `for`, `do...while`, and `while` loop. The `continue` statement allows you to immediately skip all the statements that follow it and start the next iteration from the beginning.

Like the `break` statement, the `continue` statement also accepts an optional number that specifies the number of levels of enclosing loops it will skip.

If you don’t specify the number that follows the `continue` keyword, it defaults to 1. In this case, the `continue` statement only skips to the end of the current iteration.

Typically, you use the `continue` statement with the `if` statement that specifies the condition for skipping the current iteration.

PHP continue example

The following example illustrates how to use the continue statement inside a for loop:

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

How it works.

-   First, use a for loop to iterate from 0 to 9.
-   Second, skip the current echo statement if `$i` is an even number. The `$i` is an even number when the `$i % 2` returns 0. As a result, the output shows only the odd numbers.
