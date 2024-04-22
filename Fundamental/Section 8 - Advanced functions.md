# Section 8 - Advanced functions

## PHP Anonymous Functions

define function in php:

```php
function multiply($x, $y)
{
	return $x * $y;
}

multiply(10, 20);					// 200
```

example defines an anonymous function:

```php
function ($x, $y) {
	return $x * $y;
};
```

how to use the anonymous function:

```php
$multiply = function ($x, $y) {
	return $x * $y;
};


echo $multiply(10, 20);				// 200

var_dump($multiply);
```

### Passing an anonymous function to another function

PHP has many built-in functions that accept a `callback function`, for example, the `array_map()` function.

```php
$numbers = [30, 25, 19, 16,];

$func = function ($item) {
    return $item * 10;
};

$result = array_map($func, $numbers);

print_r($result);
```

or 

```php
$numbers = [30, 25, 19, 16,];

$result = array_map(function ($item) {
     return $item * 10;
}, $numbers);

print_r($result);
```

## PHP Arrow Functions 

PHP 7.4 introduced the arrow functions that provide a more concise syntax for the anonymous functions.

```php
fn (arguments) => expression;
```

or 

```php
function(arguments) { return expression; }
```

Example:

```php
$multiply = fn ($x, $y) => $x * $y;

echo $multiply(10, 20);						// 200
```

```php
$numbers = [30, 25, 19, 16,];

$result = array_map(fn ($item) => $item * 10, $numbers);

print_r($result);
```
