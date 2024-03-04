# Section 6 - Functions

## PHP Function Parameters

### Introduction to the PHP function parameters

A `function` can have zero or more parameters:

```php
function function_name(parameter_list) 
{
}
```

When a function has multiple parameters, you need to separate them using a comma (`,`).

The following example defines the `concat()` function that concatenates two strings into one:

```php
function concat($str1, $str2)
{
	return $str1 . $str2;
}
```

The `concat()` function has two parameters `$str1` and `$str2`.

When you call the `concat()` function, you need to pass two arguments that correspond to the parameters. For example:

```php
function concat($str1, $str2)
{
	return $str1 . $str2;
}

$greeting = concat('Welcome ', 'Admin');
echo $greeting;
```

In this example, the `$str1` will take the first argument `'Welcome '`, and the `$str2` will take the second argument `'Admin'`.

PHP will raise an error if the number of arguments you pass to the function is less than the number of parameters. For example:

```php
function concat($str1, $str2)
{
	return $str1 . $str2;
}


$greeting = concat('Welcome');
echo $greeting;
```

When you pass multiple arguments to a function, you can break the list the arguments vertically to make the code more readable like this:

```php
function concat($str1, $str2)
{
	return $str1 . $str2;
}

$greeting = concat(
	'Welcome ',
	'Home'
);

echo $greeting;
```

#### Trailing comma (,)

From PHP 7.0, the argument list may contain a trailing comma (,) which the PHP interpreter will ignore. For example:

```php
$greeting = concat(
	'Welcome ',
	'Home',
);
```

Starting from PHP 8.0, you can place the trailing comma (,) in the parameter list like this:

```php
function concat(
	$str1,
	$str2,
) {
	return $str1 . $str2;
}
```

#### Passing arguments by values

Consider the following example:

```php

$counter = 1;
function increase($value)
{
	$value+= 1;
	echo "$value\n"; // 2
}

// increase the counter
increase($counter);

echo "$counter\n"; // 1
```

Output:

```
2
1
```

How it works.

-   First, define the `$counter` variable and initialize its value to one.
-   Second, define the `increase()` function that increases the argument by one and displays it.
-   Third, call the `increase()` function and pass the `$counter` variable into the function.
-   Finally, display the `$counter` variable.

When you pass the `$counter` variable to the `increase()` function, the function increases its value by one. Therefore, when you display the value of the `$counter` inside the function, you’ll get two.

However, after the function call, the value of the counter is still one. It means that the `increase()` function doesn’t increase the `$counter` variable outside the function.

What happens is that when you pass the $counter to the `increase()` function, the function copies the `$counter` variable and modifies the copy. It doesn’t change the original variable. The `$counter` variable doesn’t change.

When the value of an argument within the function is changed and doesn’t get changed outside the function, it is passed by value.

By default, arguments are passed by values in PHP. If you want a function to change its arguments, you need to pass the arguments by reference.

#### Passing arguments by reference

To pass an argument by reference, you prepend the operator `(&)` to the parameter name in the function definition like this:

```php
$counter = 1;
function increase( &$value )
{
	$value += 1;
	echo "$value\n"; // 2
}

// increase the counter
increase($counter);

echo "$counter\n"; // 
```

Output:

```
2
2
```

## PHP Default Parameters

### Introduction to the PHP default parameters

The following defines the `concat()` function that concatenates two strings with a delimiter:

```php
function concat($str1, $str2, $delimiter)
{
    return $str1 . $delimiter . $str2;
}
```

When you call the `concat()` function, you need to pass exactly three arguments. For example:

```php
function concat($str1, $str2, $delimiter)
{
    return $str1 . $delimiter . $str2;
}

$message = concat('Hi', 'there!', ' ');

echo $message;
```

However, you’ll find that you often use the space ‘ ‘ as the delimiter. And it’s repetitive to pass the space whenever you call the function.

This is why default parameters come into play.

PHP allows you to specify a default argument for a parameter. For example:

```php
function concat($str1, $str2, $delimiter = ' ')
{
    return $str1 . $delimiter . $str2;
}
```

In this example, the `$delimiter` parameter takes the space as the default argument.

When you call the `concat()` function and don’t pass the delimiter argument, the function will use the space for the `$delimiter` like this:

```php
function concat($str1, $str2, $delimiter = ' ')
{
    return $str1 . $delimiter . $str2;
}

$message = concat('Hi', 'there!');

echo $message;
```

Output:

```
Hi there
```

However, if you pass an argument for the `$delimiter`, the function will use that argument instead:

```php
function concat($str1, $str2, $delimiter = ' ')
{
    return $str1 . $delimiter . $str2;
}

$message = concat('Hi', 'there!', ',');

echo $message;
```

Output:

```
Hi,there!
```

In this example, we passed a comma to the $delimiter. The `concat()` function used the comma `(,)` instead of the default argument.

When you specify a default argument for a parameter, the parameter becomes optional. It means that you can pass a value or skip it.

#### Default arguments

The default arguments must be constant expressions. They cannot be variables or function calls.

PHP allows you to use a scalar value, an array, and null as the default arguments.

#### The order of default parameters

When you use default parameters, it’s a good practice to place them after the parameters that don’t have default values. Otherwise, you will get unexpected behavior. For example:

```php
function concat($delimiter = ' ', $str1, $str2)
{
	return $str1 . $delimiter . $str2;
}

$message = concat('Hi', 'there!', ',');

echo $message;
```

Output:

```
there!Hi,
```

## PHP Named Arguments

### Introduction to the PHP named arguments

Since PHP 8.0, you can use named arguments for functions. The named arguments allow you to pass arguments to a function based on the parameter names rather than the parameter positions.

The following example defines a function that finds the position of the first occurrence of a substring in a string:

```php
function find($needle, $haystack)
{
    return strpos($haystack, $needle);
}    
```

To call the `find()` function, you pass the arguments based on the parameter positions like this:

```php
find('awesome', 'PHP is awesome!');
```

In this case, `$needle` is `'awesome'` and `$haystack` is `'PHP is awesome!'`.

However, the function call is not apparent. For example, you don’t know which argument is the needle and which argument is the haystack.

Sometimes, you may accidentally make a mistake by passing the arguments in the wrong order. For example:

```php
find ( 
    'PHP is awesome!',
    'awesome'
);
```

The comment makes the code more clear. However, it’s not robust.

To improve this, PHP 8.0 introduced the named arguments that allow you to specify the parameter names when passing arguments:

```php
find (
    $needle : 'awesome',
    $haystack : 'PHP is awesome!'
);
```

Since you are using the parameter names, the positions are not necessary. For example, you can swap the parameters like this:

```php
find(
    $haystack :'PHP is awesome!',
    $needle : 'awesome'
);
```

#### Skipping default arguments

The following defines a function that creates an anchor element `(<a>)` from text, href, title, and target:

```php
function create_anchor(
    $text,
    $href = '#',
    $title = '',
    $target = '_self'
)
{
    $href = $href ? sprintf('href="%s"', $href) : '';
    $title = $title ? sprintf('title="%s"', $title) : '';
    $target = $target ? sprintf('target="%s"', $target) : '';

    return "<a $href $title $target>$text</a>";
}
```

To create a link with the target is _blank, you must specify all the default arguments until the one you want to change. For example:

```php
$link = create_anchor(
    'PHP Tutorial', 
    'https://www.phptutorial.net/',
    '',
    '_blank'
);

echo $link;
```

Output:

```php
<a href="https://www.phptutorial.net/"  target="_blank">PHP Tutorial</a>
```

In this example, you need to pass the space (”) to the third argument. If you use the named arguments, you don’t have to specify all the defaults. For example:

```php
 $link = create_anchor(
    text : 'PHP Tutorial', 
    href : 'https://www.phptutorial.net/',
    target: '_blank'
);
```
#### Mixing named arguments with positional arguments

PHP allows you to call a function by using both positional arguments and named arguments. And you need to place the named arguments after positional arguments. For example:

```php
$link = create_anchor(
    'PHP Tutorial', 
    'https://www.phptutorial.net/',
     target: '_blank'
);
```

In this example:

-   The `text` is `'PHP Tutorial'`.
-   The `href` is `'https://www.phptutorial.net/'`.
-   And the ta`r`get is `'_blank'`.

If you place the named arguments before the positional arguments, you’ll get an error. For example:

```php
create_anchor(
    target : '_blank',
    'PHP Tutorial', 
    'https://www.phptutorial.net/'
);
```

Error:

```
Cannot use positional argument after named argument
```

## PHP Variable Scopes

### Introduction to PHP variable scopes

The scope of a variable determines which part of the code can access it. The locations where the variable can be accessible determine the scope of the variable.

In PHP, variables have four types of scopes:

-   Local
-   Global
-   Static
-   Function parameters

#### Local variables

When you define a variable inside a function, you can only access that variable within the function. And it’s said that the variable is local to the function.

The following example defines the `say()` function that displays the `'Hi'` message:

```php
function say()
{
	$message = 'Hi';
	echo $message;
}
```

Inside the `say()` function, we define the `$message` variable. The `$message` variable is a local variable. And you cannot access it from the outside of the `say()` function.

Also, the `$message` variable only exists during the execution of the `say()` function. Once the `say()` function ends, the `$mesage` variable won’t exist anymore.

#### Global variables

When you declare a variable outside of a function, the variable is global. It means that you can access the variable anywhere within the script except inside a function. For example:

```php
$message = 'Hello';

function say()
{
	$message = 'Hi';
	echo $message;
}

echo $message; // Hello
```

In this script, we have two variables with the same name `$message`.

The first variable is the global variable because we define it outside of a function. The `$message` variable that we define inside the function is the local variable. Even though these variables have the same name, they’re two different variables.

PHP allows you to access a global variable within a function by using the `global` keyword. For example:

```php
$message = 'Hello';

function say()
{
	global $message;
	echo $message; // Hello
}

say();
```

How it works.

-   First, define a global variable called `$message`.
-   Second, reference the global variable `$message` inside the `say()` function.

It’s important to note that it’s not a good practice to use global variables.

### Superglobal variables

PHP has a list of built-in variables, which are known as superglobal variables. The superglobal variables provide information about the PHP script’s environment.

The superglobal variables are always available in all parts of the script. The following table shows the list of  PHP superglobal variables:

![superglobals](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/superglobal.png)

### Static variables

A static variable retains its value between function calls. Also, a static variable is only accessible inside the function. To define a static variable, you use the `static` keyword. For example:

```php
function get_counter() {
    static $counter = 1;
    return $counter++;
}

echo get_counter() .  "\n"; // 1
echo get_counter() .  "\n"; // 2
echo get_counter() .  "\n"; // 3
```

Output:

```
1
2
3
```

How it works.

-   First, define the get_counter() function with a static variable named $counter. 
-   Second, call the set_counter() function three times. As you notice that the value of the $counter variable is increased by one after each function call.


## PHP Type Hints

### Introduction to PHP type hints

PHP is a dynamically typed language. When you define a function, you don’t need to declare types for parameters. For example:

```php
function add($x, $y)
{
    return $x + $y;
}

$result = add(1,2);
echo $result; // 3
```

The `add()` function accepts two arguments and returns the sum of them. In this example, we pass two integers into the `add()` function and get the result as an integer.

If you pass two floating-point numbers into the `add()` function, you’ll get the sum of the floats, which is a floating-point number:


```php
function add($x, $y)
{
    return $x + $y;
}

$result = add(1.0,2.5);
echo $result; // 3.5
```

In this case, the `add()` function implicitly coerces the numeric string '2' into the integer 2 because of the + operator. If PHP fails to coerce the string argument into an integer, it’ll issue an error. For example:

```php
function add($x, $y)
{
    return $x + $y;
}

$result = add('Hi','There');
echo $result;
```

Error:

```
Fatal error: Uncaught TypeError: Unsupported operand types: string + string in ...
```

To enforce the types for function parameters and return value, you can use type hints.

#### PHP type hints for function parameters

The type hints ensure that PHP will check the type of a value at the call time and throw a `TypeError` if there is a mismatch.

To add a type hint to a parameter, you place a type in front of it like this:

```php
function my_function(type $param1, type param2, ...) {
   // ...
}
```

In PHP 5, you can use `array`, `callable`, and class for type hints. In PHP 7+, you can also use scalar types such as `bool`, `float`, `int`, and `string`.

The following defines the `add()` function that accepts two integers:

```php
function add(int $x, int $y)
{
    return $x + $y;
}

$result = add(1,2);
echo $result;  // 3
```

However, if you pass two floats, you’ll get the result as an integer:

```php
function add(int $x, int $y)
{
    return $x + $y;
}

$result = add(1,2.5);
echo $result; // 3
```

In this case, PHP implicitly coerces 2.5 into an integer (2) before calculating the sum. Therefore, the result is an integer.

#### PHP type hints for function’s return value

To specify a return value’s type for a function, you add the type after the function header like this:

```php
function my_function(type $param1, type $param2, ...) : type 
{
    // ..
}
```

The following example defines the `add()` function that accepts two integers and returns an integer:

```php
function add(int $x, int $y): int
{
    return $x + $y;
}

echo add(10, 20);
```

Starting from PHP 7.0, if a function doesn’t return a value, you use the `void` type. For example:

```php
function dd($data):void
{
    var_dump($data);
    die;
}
```

### The union type

Starting from PHP 8.0, if a function returns a value of several types, you can declare it as a union type. For example:

```php
function add($x, $y): int | float
{
    return $x * $y;
}

echo add(10, 20); // 200 (int) 
echo add(1.5, 2.5); // 3.75 (float)
```

In this example, the `add()` function returns an integer or a floating-point number, depending on the types of arguments.

#### The mixed type

If a function returns a value of many types, you can use the mixed type. The mixed type means one of several types. The mixed type. It’s equivalent to the following union type:

```php
object|resource|array|string|int|float|bool|null
```

#### The nullable type

The following defines a function that accepts a string and returns the uppercase of that string:

```php
function upper(string $str): string
{
    return strtoupper($str);
}
```

If you pass an argument with null, you’ll get an error:

```php
function upper(string $str): string
{
    return strtoupper($str);
}

$str = null;
echo upper($str);
```

Error:

```
Fatal error: Uncaught TypeError: Argument 1 passed to upper() must be of the type string, null given
```

To fix this, you can make the $str parameter nullable like this:

```php
function upper(?string $str): string
{
    return strtoupper($str);
}

$str = null;
echo upper($str);
```

The nullable type was introduced in PHP 7.1.

PHP allows you to mark the type declarations and returns values as nullable by prefixing the type name with a question mark (?).

In the above example, we add the ? to the string type of the $str parameter. The ?string allows you to pass a string argument or null.

Note that the mixed type already includes the null type. Therefore, you don’t need to include nullable mixed like this:

```
? mixed
```

## PHP Variadic Functions

Introduction to the PHP variadic functions

The following example defines a function called `sum()` that returns the sum of two integers:


```php
function sum(int $x, int $y)
{
    return $x + $y;
}

echo sum(10, 20); // 30
```

To allow the `sum()` function to accept a variable of arguments, you need to use `func_get_args()` function. The `func_num_args()` function returns an array that contains all function arguments. For example:

```php
function sum()
{
    $numbers = func_get_args();
    $total = 0;
    for ($i = 0; $i < count($numbers); $i++) {
        $total += $numbers[$i];
    }

    return $total;
}
echo sum(10, 20) . "\n"; // 30
echo sum(10, 20, 30) . "\n"; // 60
```

In this example, we don’t specify any parameter for the `sum()` function. When calling the `sum()` function, we can pass any number of arguments into it.

Inside the function, the `func_get_args()` returns an array that contains all the arguments. To sum up all the arguments, we use a `for` loop.

PHP 5.6 introduced the `...` operator. When you place the `...` operator in front of a function parameter, the function will accept a variable number of arguments, and the parameter will become an array inside the function. For example:

```php
function sum(...$numbers)
{
    $total = 0;
    for ($i = 0; $i < count($numbers); $i++) {
        $total += $numbers[$i];
    }

    return $total;
}
echo sum(10, 20) . "\n"; // 30
echo sum(10, 20, 30) . "\n"; // 60
```

In this example, we place the `...` operator in front of the `$numbers` argument. The `sum()` function now accepts a variable of number arguments.

PHP 7 allows you to declare types for variadic arguments. For example:

```php
function sum(int ...$numbers): int
{
    $total = 0;
    for ($i = 0; $i < count($numbers); $i++) {
        $total += $numbers[$i];
    }

    return $total;
}
```

In this example, the `sum()` function will accept only integers and return the sum of integers.

If a function has multiple parameters, only the last parameter can be variadic. For example:

```php
function my_func($a, $b, ...$params) {
    // ...
}
```

If you place the variadic parameter before a regular one, you’ll get an error:

```
Fatal error: Only the last parameter can be variadic in...
```

And a function only has one variadic parameter.

Note that you can use the `array_sum()` to calculate the sum of all elements of an array. So you can simplify the `sum()` function like this:

```php
function sum(int ...$numbers): int
{
    return array_sum($numbers);
}
```
