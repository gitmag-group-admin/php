# Section 6 - Functions

## PHP Function


```php
function function_name(parameter_list) 
{
}
```
Define function:

```php
function sayHello()
{
	echo 'hello world';
}
```

Execute function:

```php
sayHello();
```

Define function with parameters:

```php
function sayHello($name, $family)
{
	echo "hello $name $family";
}

hello('sohrab', 'azinfar');     // hello sohrab azinfar
```

Return value from function:

```php
function hello($name, $family)
{
	return "hello $name $family";
}

$result = hello('sohrab', 'azinfar');
echo $result;                   // hello sohrab azinfar

// echo hello();                // hello sohrab azinfar
```


### Trailing comma (,)

PHP up to 7.0

```php
function hello($name, $family)
{
	return "hello $name $family";
}

$result = hello('sohrab ', 'azinfar',);
echo $result;                   // hello sohrab azinfar
```

PHP up to 8.0

```php
function hello($name, $family,)
{
	return "hello $name $family";
}

$result = hello('sohrab ', 'azinfar');
echo $result;                    // hello sohrab azinfar
```

### Passing arguments by values

```php

$counter = 1;
function increase($value)
{
	$value += 1;
	echo "value is: $value\n";  // value is: 2
}

// increase the counter
increase($counter);

echo "counter is: $counter\n";  // counter is: 1
```


### Passing arguments by reference

```php
$counter = 1;
function increase( &$value )
{
	$value += 1;
	echo "value is: $value\n"; // value is: 2
}

// increase the counter
increase($counter);

echo "counter is: $counter\n"; // counter is: 2
```



## PHP Default Parameters

```php
function fullname($name, $family, $delimiter)
{
    return $name . $delimiter . $family;
}

$fullname = fullname('sohrab', 'azinfar', ' ');

echo $fullname;
```

Function with default value parameter:

```php
function fullname($name, $family, $delimiter = ' ')
{
    return $name . $delimiter . $family;
}

$fullname1 = fullname('sohrab', 'azinfar');
echo $fullname1;                    // sohrab azinfar

// $fullname2 = fullname('hossein', 'mohammadi', '=');
// echo $fullname2;                    // hossein=mohammadi

// $fullname3 = fullname('alireza', 'bayani', ' / ');
// echo $fullname3;                    // alireza / bayani
```

The order of default parameters:


```php
function fullname($delimiter = ' ', $name, $family)
{
    return $name . $delimiter . $family;
}

$fullname1 = fullname('=', 'sohrab', 'azinfar');
echo $fullname1;                    // sohrab=azinfar

// $fullname2 = fullname('sohrab', 'azinfar');
// echo $fullname2;                    // PHP Fatal error         
```

## PHP Named Arguments

PHP up to 8.0

```php
function fullname($name, $family, $delimiter)
{
    return $name . $delimiter . $family;
}

$fullname1 = fullname(
    name: 'sohrab',
    family: 'azinfar',
    delimiter: ' = '
);
echo $fullname1;                 // sohrab = azinfar

// $fullname2 = fullname(
//     family: 'azinfar',
//     delimiter: ' = ',
//     name: 'sohrab',
// );
// echo $fullname2;                 // sohrab = azinfar
```

Skipping default arguments:

```php
function fullname($delimiter = ' ', $name, $family)
{
    return $name . $delimiter . $family;
}

$fullname = fullname(
    name: 'sohrab',
    family: 'azinfar',
);
echo $fullname;                 // PHP Fatal error
```

## PHP Variable Scopes

In PHP, variables have four types of scopes:

-   Local
-   Global
-   Static
-   Function parameters

### Local variables

```php
function sayHello()
{
	$message = "hello sohrab\n";
	echo $message;
}

sayHello();                        // hello shorab
echo $message;                     // PHP Warning
```

### Global variables

```php
$message = "hello sohrab\n";

function sayHello()
{
	$message = "hi sohrab\n";      // if comment: PHP Warning
	echo $message;
}

sayHello();                        // hi shorab
echo $message;                     // hello sohrab
```

If you want to access to Global variable:

```php
$message = "hello sohrab\n";

function sayHello()
{
	global $message;
	echo $message;
}

sayHello();                        // hello sohrab
echo $message;                     // hello sohrab  
```
### Static variables

A static variable retains its value between function calls. Also, a static variable is only accessible inside the function. To define a static variable, you use the `static` keyword. For example:

```php
function getCounter() {
    static $counter = 1;
    return $counter++;
}

echo getCounter() .  "\n";          // 1
echo getCounter() .  "\n";          // 2
echo getCounter() .  "\n";          // 3
```

## PHP Type Hints

```php
function sum($x, $y)
{
    return $x + $y;
}

$result1 = sum(1, 2);
echo $result1 .  "\n";               // 3

// $result2 = sum(1.0, 2.5);
// echo $result2 .  "\n";               // 3.5

// $result3 = sum('sohrab','azinfar');  // Fatal error
// echo $result3;
```

In PHP 5, you can use `array`, `callable`, and class for type hints. In PHP 7+, you can also use scalar types such as `bool`, `float`, `int`, and `string`.

```php
function myFunction(type $param1, type param2, ...) {
   // ...
}
```
Example:

```php
function add(int $x, int $y)
{
    return $x + $y;
}

$result = sum(1, 2);
echo $result;                       // 3

// $result = sum(1, 2.5);
// echo $result;                       // 3
```

### PHP type hints for function’s return value

```php
function myFunction(type $param1, type $param2, ...) : type 
{
    // ..
}
```
Example:

```php
function sum(int $x, int $y): int
{
    return $x + $y;
}

echo sum(10, 20);                   // 30
```

Starting from PHP 7.0, if a function doesn’t return a value, you use the `void` type. For example:

```php
function test($data): void
{
    var_dump($data);
}
```

### The union type

PHP up to 8.0, 

```php
function sum($x, $y): int | float
{
    return $x + $y;
}

echo sum(10, 20);                   // 30 (int) 
// echo sum(1.2, 2.5);                 // 3.7 (float)
```

In this example, the `add()` function returns an integer or a floating-point number, depending on the types of arguments.

#### The mixed type

```php
object|resource|array|string|int|float|bool|null

mixed
```

#### The nullable type


```php
function sayHello(string $name): string
{
    return "hello $name";
}

$str = null;
echo sayHello($str);                    // Fatal error
```

To fix this:

```php
function sayHello(?string $name): string
{
    return "hello $name";
}

$str = null;
echo sayHello($str);
```

returned value is null: 

```php
function sayHello(?string $name): ?string   // null | string
{
    if( is_null($name)) {
        return null;
    }

    return "hello $name";
}

$str = null;
echo sayHello($str);
```

## PHP Variadic Functions

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
echo sum(10, 20) . "\n";                // 30
// echo sum(10, 20, 30) . "\n";            // 60
```

PHP 5.6 introduced the `...` operator. 
```php
function sum(...$numbers)
{
    $total = 0;
    for ($i = 0; $i < count($numbers); $i++) {
        $total += $numbers[$i];
    }

    return $total;
}
echo sum(10, 20) . "\n";                // 30
// echo sum(10, 20, 30) . "\n";            // 60
```

PHP 7 allows you to declare types for variadic arguments:

```php
function sum(int ...$numbers): int
{
    $total = 0;
    for ($i = 0; $i < count($numbers); $i++) {
        $total += $numbers[$i];
    }

    return $total;
}

echo sum(10, 20) . "\n";                // 30
echo sum(10, 20, 'test') . "\n";        // PHP Fatal error
```

If a function has multiple parameters, only the last parameter can be variadic:

```php
function myFunction($a, $b, ...$params) {
    // ...
}
```

```php
function sum($str, int ...$numbers): string
{
    $total = 0;
    for ($i = 0; $i < count($numbers); $i++) {
        $total += $numbers[$i];
    }

    return $str . $total;
}

echo sum('total is: ', 10, 20) . "\n";    //total is:  30
```
