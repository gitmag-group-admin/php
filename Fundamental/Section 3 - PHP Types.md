# Section 3. PHP Types

## PHP Data Types

### Introduction to PHP data types

A type specifies the amount of memory that allocates to a value associated with it. A type also determines the operations that you can perform on it.

PHP has ten primitive types including four scalar types, four compound types, and two special types:

![PHP](https://www.phptutorial.net/wp-content/uploads/2021/03/PHP-types.svg)

Scalar types
-   bool
-   int
-   float
-   string

Compound types
-   array
-   object
-   callable
-   iterable

Special types
-   resource
-   null

### Scalar types
A variable is a scalar when it holds a single value of the type `integer`, `float`, `string`, or `boolean`.


#### Integer
Integers are whole numbers defined in the set {…-3,-2-,-1,0,1,2,3…}.  The size of the integer depends on the platform where PHP runs.

The constant `PHP_INT_SIZE` specifies the size of the integer on a specific platform. PHP uses the int keyword to denote the integer type.

The following example illustrates some integers:

```php
<?php
$count = 0;
$max = 1000;
$page_size = 10;
```
##### The is_int() function
The `is_int()` built-in function returns `true` if a value (or a variable) is an integer. Otherwise, it returns `false`. For example:

```php
$amount = 100;
echo is_int($amount);
```

Output:

```bash
1
```

#### Float
Floats are floating-point numbers, which are also known as floats, doubles, or real numbers.

PHP uses the IEEE 754 double format to represent floats. Like other programming languages, floats have limited precision.

PHP uses the `float` keyword to represent the floating-point numbers. The following example illustrates the floating-point numbers in PHP:

```php
<?php
$price = 10.25;
$tax = 0.08;
```

##### Test a float value
To check if a value is a floating-point number, you use the `is_float()` or `is_real()` function. The `is_float()` returns `true` if its argument is a floating-point number; otherwise, it returns `false`. For example:

```php
<?php
echo is_float(0.5);
```

Output:

```bash
1
```

#### Boolean
Boolean represents a truth value that can be either `true` or `false`. PHP uses the `bool` keyword to represent the Boolean type.

The bool type has two values `true` and `false`. Since keywords are case-insensitive, you can use `true`, True, TRUE, `false`, False, and False to indicate boolean values.

The following example shows how to assign Boolean values to variables:

```php
<?php
$is_admin = true;
$is_user_logged_in = false;
```

When you use the values of other types in the boolean context, such as `if-else` and `switch-case` statements, PHP converts them to the boolean values.

PHP treats the following values as false:
-   The false keyword.
-   The integer 0 and -0 (zero).
-   The floats 0.0 and -0.0 (zero).
-   The empty string ("", '') and the string “0”.
-   The empty array (array() or []).
-   The null.

The values that are not one of these falsy values above are `true`.

To check if a value is a Boolean, you can use the built-in function `is_bool()`. For example:

```php
$is_email_valid = false;
echo is_bool($is_email_valid);
```
When you use the `echo` to show a boolean value, it’ll show `1` for `true` and nothing for false, which is not intuitive. To make it more obvious, you can use the `var_dump()` function. For example:

```php
<?php
$is_email_valid = false;
var_dump($is_email_valid);

$is_submitted = true;
var_dump($is_submitted);
```

Output:

```
bool(false)
bool(true) 
```

#### String
A string is a sequence of characters surrounded by single quotes `‘` or double quotes `“`. For example:

```php
<?php
$str = 'PHP scalar type';
$message = "PHP data types";
```

However, you cannot start a string with a single quote and ends it with a double quote and vice versa. The quotes must be consistent.

Single-quoted strings vs. double-quoted strings

Suppose you have a variable `$name`.

```php
<?php
$name = 'John';
```

To do it, you can use the concatenate operator `.` to concatenate two strings:

```php
<?php
$name = 'John';
echo 'Hello ' . $name;
```
And you want to show a message that displays the following:

```
Hello John
```

However, if you use a double-quoted string, you can place the `$name` variable inside the string as follows:

```php
<?php
$name = 'John';
echo "Hello $name";
```
And you want to show a message that displays the following:

```
Hello John
```

When evaluating a double-quoted string, PHP replaces the value of any variable that you place inside the string. This feature is called variable interpolation in PHP.

An alternative syntax is to wrap the variable in curly braces like this:

```php
<?php
$name = 'John';
echo "Hello {$name}";
```

The output is the same.

Note that PHP doesn’t substitute the value of variables in the single-quoted string, for example:

```php
<?php
$name = 'John';
echo 'Hello {$name}';
```

The output will be like this:

```php
Hello {$name}
```

Besides substituting the variables, the double-quoted strings also accept special characters, e.g., `\n`, `\r`, `\t` by escaping them.

It’s a good practice to use single-quoted strings when you don’t use variable interpolation because PHP doesn’t have to parse and evaluate them for double-quoted strings.

#### Accessing characters in a string

A string has a zero-based index. It means that the first character has an index of 0. The second character has an index of 1 and so on.

To access a single character in a string at a specific position, you use the following syntax:

```php
$str[index]
```

For example:

```php
<?php
$title = 'PHP string is awesome';
echo $title[0];
```

Output:

```bash
P
```

#### Getting the length of a string
To get the length of a string, you use a built-in function `strlen()`, for example:

```php
<?php
$title = 'PHP string is awesome';
echo strlen($title);
```

### Compound types
Compound data includes the values that contain more than one value. PHP has two compound types including array and object.

#### Array
An array is an ordered map that associates keys with values. For example, you can define a list of items in a shopping cart like this:

```php
<?php
$carts = [ 'laptop', 'mouse', 'keyboard' ];
```

The `$carts` array contains three string values. It maps the index `0`, `1`, and `2` to the values `'laptop'`, `'mouse'`, and `'keyboard'`. The $carts is called an indexed array because it uses numeric indexes as keys.

To access a value in an array, you use the square brackets:

```php
<?php
echo $carts[0]; // 'laptop'
echo $carts[1]; // 'mouse'
echo $carts[2]; // 'keyboard'
```

Besides numeric indexes, you can use strings as keys for the array elements. These arrays are known as associative arrays. For example:

```php
<?php
$prices = [
   'laptop' => 1000,
   'mouse' => 50,
   'keyboard' => 120
];
```

To access an element in an associative array, you specify the key in the square brackets. For example:

```php
<?php
echo $prices['laptop']; // 1000
echo $prices['mouse']; // 50
echo $prices['keyboard']; // 120
```

#### Object
An object is an instance of a class. It’s a central concept in object-oriented programming.

An object has properties. For example, a person object may have the first name, last name, and age properties.

An object also has behaviors, which are known as methods. For example, a person object can have a method called `getFullName()` that returns the full name.

To learn more about objects, check out the object tutorial.

### Special types
PHP has two special types: `null` and `resource`

#### Null
The `null` type has one value called null that represents a variable with no value.

A variable is null when you assign null to it like this:

```php
<?php
$email = null;
var_dump($email); // NULL
```

In addition, when you use the `unset()` function to unset a variable, the variable is also null. For example:

```php
<?php
$email = 'webmaster@phptutorial.net';
unset($email);

var_dump($email); // NULL
```

##### PHP NULL and case-sensitivity
PHP keywords are case-insensitive. Therefore, NULL is also case-insensitive. It means that you can use `null`, `Null`, or `NULL` to represent the `null` value. For example:

```php
<?php
$email = null;
$first_name = Null;
$last_name = NULL;
```

##### Testing for NULL
To check if a variable is `null` or not, you use the `is_null()` function. The `is_null()` function returns `true` if a variable is `null`; otherwise, it returns `false`. For example:

```php
<?php
$email = null;
var_dump(is_null($email)); // bool(true)

$home = 'phptutorial.net';
var_dump(is_null($home)); // bool(false)
```


#### Resource
The resource type holds a reference to an external resource, e.g. a filehandle or a database connection.

## PHP Type Casting

### Introduction to the PHP type casting
To cast a value to an integer, you use the `(int)` type casting operator.

The `(int)` operator casts a float to an integer. It’ll round the result towards zero. For example:

```php
<?php
echo (int)12.5 . '<br>'; // 12
echo (int)12.1 . '<br>'; // 12
echo (int)12.9 . '<br>'; // 12
echo (int)-12.9 . '<br>'; // -12
```
Suppose you have a string and want to cast it as an integer:

```php 
<?php 
$message = 'Hi';
$num = (int) $message;
echo $num; // 0
```

The result may not be what you expected.
If a string is numeric or leading numeric, then the `(int)` will cast it to the corresponding integer value. Otherwise, the `(int)` cast the string to zero. For example:

```php
<?php
$amount =  (int)'100 USD';
echo $amount; // 100
```

In this example, the `(int)` operator casts the string `'100 USD'` as an integer.

Note that the `(int)` operator casts null to zero `0`. For example:

```php
<?php
$qty = null;
echo (int)$qty; // 0
```

### Cast to a float
To cast a value to a float, you use the `(float)` operator. For example:

```php
<?php
$amount = (float)100;
echo $amount; // 100
```

### Cast to a string
To cast a value to a string, you use the `(string)` operator.

The following example uses the `(string)` operator to cast the number 100 to a string:

```php
<?php
$amount = 100;
echo (string)$amount . " USD"; // 100 USD
```

You don’t need to use the `(string)` operator in this case because PHP has a feature called type juggling that implicitly converts the integer to a string:

```php
<?php
$amount = 100;
echo $amount . ' USD'; // 100 USD
```

The `(string)` operator converts the true value to the string `"1"` and `false` value to the empty string `“”`. For example:

```php
<?php
$is_user_logged_in = true;
echo (string)$is_user_logged_in; // 1
```

Output:

```
1
```

The `(string)` operator casts `null` to an empty string.

The `(string)` cast an array to the `"Array"` string. For example:

```php
<?php
$numbers = [1,2,3];
$str = (string) $numbers;

echo $str; // Array
```

And you’ll get a warning that you’re attempting to convert an array to a string.

```
Warning: Array to string conversion in ...
```
