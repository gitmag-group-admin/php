# Section 4. Operators

## PHP Assignment Operators

### Introduction to the PHP assignment operator

PHP uses the `=` to represent the assignment operator. The following shows the syntax of the assignment operator:

```php
$variable_name = expression;
```
On the left side of the assignment operator `(=)` is a variable to which you want to assign a value. And on the right side of the assignment operator `(=)` is a value or an expression.

When evaluating the assignment operator `(=)`, PHP evaluates the expression on the right side first and assigns the result to the variable on the left side. For example:

```php
$x = 10;
$y = 20;
$total = $x + $y;
```

In this example, we assigned 10 to `$x`, 20 to `$y`, and the sum of $x and $y to $total.

It means that you can use multiple assignment operators in a single statement like this:

```php
$x = $y = 20;
```

The variable `$y` is 20.

## Arithmetic Operators

The arithmetic operators require numeric values. If you apply them to non-numeric values, they’ll convert them to numeric values before carrying the arithmetic operation.

The following are the list of arithmetic operators:

![Arithmetic Operators](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/0005.png)

The following example uses the arithmetic operators:

```php
$x = 20;
$y = 10;

// add, subtract, and multiplication operators demo
echo $x + $y . '<br/>';  // 30
echo $x - $y . '<br/>';  // 10
echo $x * $y . '<br/>';  // 200

// division operator demo
$z = $x / $y;
echo gettype($z)  . '<br/>'; //  integer

$z = $y / $x;
echo gettype($z)  . '<br/>'; // double

// modulus demo

$y = 15;
echo $x % $y . '<br/>'; // 5
```

### Incrementing/ Decrementing Operators

Increment `(++)`  and decrement `(–)` operators give you a quick way to increase and decrease the value of a variable by `1`.

The following table illustrates the increment and decrement operators:

![Incrementing/ Decrementing Operators](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/0006.png)

### Arithmetic assignment operators

Sometimes, you want to increase a variable by a specific value. For example:

```php
$counter = 1;
$counter = $counter + 1;
```

How it works.

-   First, `$counter` is set to 1.
-   Then, increase the `$counter` by 1 and assign the result to the `$counter`.

After the assignments, the value of $counter is 2.

PHP provides the arithmetic assignment operator `+=` that can do the same but with a shorter code. For example:

```php
$counter = 1;
$counter += 1;
```

Besides the `+=` operator, PHP provides other arithmetic assignment operators. The following table illustrates all the arithmetic assignment operators:

```php
$x += $y ==> $x = $x + $y
$x -= $y ==> $x = $x – $y
$x *= $y ==> $x = $x * $y
$x /= $y ==> $x = $x / $y
$x %= $y ==> $x = $x % $y
$z **= $y ==> $x = $x ** $y

```

## Concatenating Operator

Concatenating operator (.) allows you to combine two strings into one. It appends the second string to the first one and returns the combined string. For example:

```php
$str = 'PHP' . ' is ' . ' Awesome!';
echo $str;
```

### Concatenation assignment operator

PHP uses the concatenation operator (.) to concatenate two strings. For example:

```php
$greeting = 'Hello ';
$name = 'John';

$greeting = $greeting . $name;

echo $greeting;
```

Output:

```
Hello John
```

By using the concatenation assignment operator you can concatenate two strings and assigns the result string to a variable. For example:

```php
$greeting = 'Hello ';
$name = 'John';

$greeting .= $name;

echo $greeting;
```

## PHP Comparison Operators

### Introduction to PHP comparison operators

A comparison operator allows you to compare two values and returns `true` if the comparison is truthful and `false` otherwise.

The following table illustrates the comparison operators in PHP:

![operators](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/0001.png)

### Equality Operator (==)

The equality returns `true` if both values are equal; otherwise, it returns `false`. The following example returns true because 10 is equal 10:

```php
$x = 10;
$y = 10;
var_dump($x == $y); // bool(true)
```

The following example returns `false` because 10 is not equal 20:

```php
$x = 20;
$y = 10;
var_dump($x == $y); // bool(false)
```

The following example compares the number `20` with a string `'20'`, it also returns true.

```php
$x = '20';
$y = 20;
var_dump($x == $y); // bool(true)
```

### Identical operator (===)

The identical operator returns `true` if both values are equal and have the same type; otherwise returns `false`.

```php
$x = '20';
$y = 20;
var_dump($x === $y); // bool(false)
```

### Not equal to operator (!=, <>)

The not equal to `(!=, <>)` operator returns `true` if the lefthand value is not equal to the righthand value; otherwise, it returns `false`. For example:

```php
$x = 20;
$y = 10;

var_dump($x != $y); // bool(true)
```

### Not identical operator (!==)

The not identical operator (!==) returns `true` if the values are not equal or they do not have the same type; otherwise, it return `false`. For example:

```php

$x = 20;
$y = 10;

var_dump($x != $y); // bool(true)

$x = 20;
$y = '20';
var_dump($x != $y); // bool(false)
```

### Greater than (>)

The greater than return `true` if the lefthand value is greater than the righthand value; otherwise, it returns `false`:

```php
$x = 10;
$y = 20;

var_dump($x > $y); // bool(false)
var_dump($y > $x); // bool(true)
```

### Greater than or equal to (>=)

The greater than or equal to operator returns true if the lefthand value is greater than or equal to the righthand value; otherwise, it returns false. For example:

```php
$x = 20;
$y = 20;

var_dump($x >= $y); // bool(true)
var_dump($y >= $x); // bool(true)
```

### Less than (<)

The less than operator returns true if the lefthand value is less than the righthand value; otherwise, it returns false. For example:

```php
$x = 20;
$y = 10;

var_dump($x < $y); // bool(false)
var_dump($y < $x); // bool(true)
```

### Less than or equal to (<=)

If the lefthand value is less than or equal to the righthand value, the less than or equal to operator returns true; otherwise, it returns false. For example:

```php
$x = 20;
$y = 20;

var_dump($x <= $y); // bool(true)
var_dump($y <= $x); // bool(true
```

## PHP AND Operator

### Introduction to the PHP AND operator

The logical AND operator accepts two operands and returns `true` if both operands are `true`; otherwise, it returns `false`.

PHP uses the `and` keyword to represent the logical AND operator:

```php
expression1 and expression2
```

The following table illustrates the result of the and operator:

![Logical Operator](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/0002.png)

Since PHP keywords are case-insensitive, the `AND` and `and` operators are the same:

```php
expression1 AND expression2
```

In addition to using the `and` keyword, PHP uses `&&` as the logical AND operator:

```php
expression1 && expression2
```

The `&&` and `and` operators return the same result. The only difference between the `&&` and `and` operators are their precedences.

### PHP AND operator examples

Suppose that you want to offer discounts to customers who buy more than three items with a price of more than 99. To determine whether customers can get a discount or not, you can use the AND operator as follows:

```php
$price = 100;
$qty = 5;

$discounted = $qty > 3 && $price > 99;

var_dump($discounted);
```

Output:

```
bool(true)
```

If you change the `$qty` to `2`, the `$discounted` will be `false` like this:

```php
$price = 100;
$qty = 2;

$discounted = $qty > 3 && $price > 99;

var_dump($discounted);
```

### Short-circuiting

When the value of the first operand is `false`, the logical AND operator knows that the result must be also `false`. In this case, it doesn’t evaluate the second operand. This process is called short-circuiting.

```php
$debug = false;
$debug && print('PHP and operator demo!');
```

How it works.

-   First, define the variable `$debug` and initialize it to `false`.
-   Second, use the logical AND operator to combine the `$debug` and `print()`. Since `$debug` is `false`, PHP doesn’t evaluate the call to the `print()` function.

If you change the $debug to `true`, you’ll see a message in the output:

```php
$debug = true;
$debug && print('PHP and operator demo!');
```

Output:

```
PHP and operator demo!
```

## PHP OR Operator

### Introduction to the PHP OR operator

The logical `OR` operator accepts two operands and returns `true` if either operand is `true`; otherwise, it returns `false`. In other words, the logical OR operator returns `false` if both operands are `false`.

To represent the logical `OR` operator, PHP uses either the `or` keyword or the `||` as follows:

```php
expression1 or expression2
```

Or

```php
expression1 || expression2
```

The following table illustrates the result of the `or` operator:

![Logical Operator](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/0003.png)

Note that the `or`, `Or`, and `OR` are the same because PHP keywords are case-insensitive.

The `||` and `or` operators return the same result. The only difference between the `||` and `or` operators are their precedences. The `or` operator has higher precedence than the `||` operator.

### PHP OR operator examples

Suppose that you need to clear the cache of the website if the flag `$exprired` or `$purge` is set to `true`. To do that, you can use the logical OR operator as follows:

```php
$expired = true;
$purged = false;

$clear_cache = $expired || $purged;

var_dump($clear_cache);
```

Output:

```
bool(true)
```

However, if you change the `$expired` to `false`, the result will be `false` as shown in the following example:

```php
$expired = false;
$purged = false;

$clear_cache = $expired || $purged;

var_dump($clear_cache);
```

### Short-circuiting

When the first operand is `true`, the logical OR operator knows that the result must be also `true`. In this case, it doesn’t evaluate the second operand. This process is called short-circuiting.

```php
$purged = false;
$purged || die('Cannot connect to the database')
```

output:

```
Cannot connect to the database
```

## PHP NOT operator

### Introduction to the PHP NOT operator

In other words, the logical NOT operator returns `true` if the operand is `false` and returns `false` if the operand is `true`.

PHP uses the both `not` keyword and `(!)` to represent the logical NOT operator.

```php
not expression
```

Or

```php
! expression
```

The following table illustrates the result of the logical NOT operator:

![Not Operator](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/0004.png)

### PHP NOT operator examples

The following example illustrates how to use the logical not operator `(!)`:

```php
$priority = 5;
var_dump( ! $priority < 5 );
```

Output:

```
bool(true)
```

In this example, PHP evaluate the expression `! $priority < 5` in the following order:

-   First, `$priority < 5` evaluates to `false`.
-   Second, `! false` evaluates to `true`.

