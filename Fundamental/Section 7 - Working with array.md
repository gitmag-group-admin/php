# Section 7 - Working with array

## Arrays

### Creating arrays

In PHP, you can use the `array()` construct or `[]` syntax to define an array.

```php
$empty_array1 = array();
$empty_array2 = [];
```

Example:

```php
$scores1 = array(1, 2, 3);
$scores2 = [1, 2, 3];
```

### Displaying arrays

```php
$scores = [1, 2, 3];
var_dump($scores);
```

```php
$scores = [1, 2, 3];
print_r($scores);
```

### Accessing array elements


```php
$array_name[index]
```

Example:

```php
$scores = [1, 2, 3];
echo $scores[0];                    // 1
```

### Adding an element to the array

```php
$array_name[] = new_element;
```

Example:

```php
$scores = [1, 2, 3];
$scores[] = 4;
var_dump($scores);
```

```php
$scores = [1, 2, 3];
$scores[3] = 4;
var_dump($scores);
```

### Changing array elements

```php
$array_name[index] = $new_element;
```
Example:

```php
$scores = [1, 2, 3];
$scores[0] = 0;
var_dump($scores);
```

### Removing array elements

```php
$scores = [1, 2, 3];
unset($scores[1]);
var_dump($scores);
```

### Getting the size of an array

```php
$scores = [1, 2, 3, 4, 5];

echo count($scores);                        // 5
```

## PHP Associative Arrays

```php
$html = []

$html['title'] = 'PHP Associative Arrays';
$html['description'] = 'Learn how to use associative arrays in PHP';

var_dump($html);
```

Output:

```
Array
(
    [title] => PHP Associative Arrays
    [description] => Learn how to use associative arrays in PHP
)
```

Accessing elements in an associative array


```php
$html['title'] = 'PHP Associative Arrays';
$html['description'] = 'Learn how to use associative arrays in PHP';

echo $html['title'];                        // PHP Associative Arrays
```

## PHP foreach

The following flowchart illustrates how the `foreach` statement works:

![foreach](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-foreach.png)

### PHP foreach with indexed arrays


```php
foreach ($array_name as $element) {
    // process element here
}
```
Example:

```php
$colors = ['red', 'green', 'blue'];

foreach ($colors as $color) {
	echo $color . "\n";
}
```

Output:

```
red
green
blue
```

### PHP foreach with an associative array

```php
foreach ($array_name as $key => $value) {
   //process element here;
}
```
Example:

```php
$capitals = [
	'Iran' => 'Tehran',
	'Japan' => 'Tokyo',
	'France' => 'Paris',
	'Germany' => 'Berlin',
	'United Kingdom' => 'London',
	'United States' => 'Washington D.C.'
];

foreach ($capitals as $country => $capital) {
	echo "The capital city of {$country} is $capital" . "\n";
}
```

## PHP Multidimensional Array

```php
$tasks = [
    ['Learn PHP programming', 2],
    ['Practice PHP', 2],
    ['Work', 8],
    ['Do exercise' 1],
];

var_dump($tasks);
```

## Array functions

### PHP array_unshift()

To prepend one or more elements to an array, you use the `array_unshift()` function:

```php
array_unshift ( array &$array , mixed ...$values ) : int
```

In this syntax:

-   `$array` is the input array
-   `$values` is the values to prepend

Example:

```php
$cities = [
	'Tehran',
	'Qom',
	'Esfehan'
];

array_unshift($cities, 'Mashhad');

var_dump($cities);
```

```php
$cities = [
	'Tehran',
	'Qom',
	'Esfehan'
];

array_unshift($cities, 'Mashhad', 'Tabriz', 'Ahvaz');

var_dump($cities);
```

Prepending an element to the beginning of an associative array:

```php

$colors = [
	'red' => '#ff000',
	'green' => '#00ff00',
	'blue' => '#0000ff',
];

$colors = ['black' => '#000000'] + $colors;

var_dump($colors);
```

### PHP array_push()

The `array_push()` function adds one or more elements to the end of an array. The syntax of the `array_push()` function is as follows:

```php
array_push ( array &$array , mixed ...$values ) : int
```

In this syntax:

-   `$array` is the input array.
-   `$values` is one or more elements to push onto the end of the input array.

```php
$array[] = $value;
```

Example:

```php
$numbers = [1, 2, 3];

array_push($numbers, 4, 5);

var_dump($numbers);
```

Push an element to the end of an associative array:

```php
$countries = [
	'Iran' => 'Tehran',
	'Iraq' => 'Baghdad'
];

$countries['Syria'] = 'Damascus';

var_dump($countries);
```

### PHP array_pop()

The `array_pop()` function removes an element from the end of an array and returns that element.

```php
array_pop ( array &$array ) : mixed
```

Example:

```php
$numbers = [1, 2, 3];

$last_number = array_pop($numbers);

echo $last_number;                          // 3
var_dump($numbers);
```

### PHP array_shift()

The array_shift() function removes the first element from an array and returns it.

```php
array_shift(array &$array): mixed
```

Example:

```php
$numbers = [1, 2, 3];
$first_number = array_shift($numbers);

echo $first_number;
var_dump($numbers)
```

### PHP array_keys

The PHP array_keys() function accepts an array and returns all the keys or a subset of the keys of the array.

```php
array_keys ( array $array , mixed $search_value , bool $strict = false ) : array
```

In this syntax:

-   `$array` is the input array.
-   `$search_value` specifies the value of the keys to search for.
-   `$strict` if it sets to true, the `array_keys()` function uses the identical operator `(===)` for matching the search_value with the array keys. Otherwise, the function uses the equal opeartor `(==)` for matching.

Example:

```php
$numbers = [10, 20, 30];
$keys = array_keys($numbers);

var_dump($keys);
```

```php
$numbers = [10, 20, 30];
$keys = array_keys($numbers, 20);

var_dump($keys);
```

```php
$user = [
	'username' => 'admin',
	'email' => 'admin@phptutorial.net',
	'is_active' => '1'
];
$properties = array_keys($user);

var_dump($properties);
```

```php
$user = [
	'username' => 'admin',
	'email' => 'admin@phptutorial.net',
	'is_active' => '1'
];
$properties = array_keys($user, 1);

var_dump($properties);
```

```php
$user = [
	'username' => 'admin',
	'email' => 'admin@phptutorial.net',
	'is_active' => '1'
];
$properties = array_keys($user, 1, true);

var_dump($properties);
```

### PHP array_key_exists()

The PHP array_key_exists() function checks if a key exists in an array. Here’s the syntax of the array_key_exists() function:

```php
array_key_exists ( string|int $key , array $array ) : bool
```

In this syntax:

-   `$key` is the key to check.
-   `$array` is an array with keys to check.

```php
$countries = [
	'Iran' => 'Tehran',
	'Iraq' => 'Baghdad',
    'Syria' => 'Damascus'
];

$result = array_key_exists('Iraq', $countries);

var_dump($result);                      // bool(true)
```

### PHP in_array()

The in_array() function returns true if a value exists in an array. Here’s the syntax of the in_array() function:

```php
in_array ( mixed $needle , array $haystack , bool $strict = false ) : bool
```

In this syntax:

-   `$needle` is the searched value.
-   `$haystack` is the array to search.
-   `$strict` if the `$strict` sets to true, the `in_array()` function will use the `strict` comparison.

```php
$cities = [
	'Tehran',
	'Qom',
	'Esfehan',
    'Mashhad'
];

$result1 = in_array('Qom', $cities);
var_dump($result1);                         // bool(true)

// $result2 = in_array('Tabriz', $cities);
// var_dump($result2);                         // bool(false)

// $result3 = in_array('qom', $cities);
// var_dump($result3);                         // bool(false)
```

```php
$ids = [10, '15', '20', 30];
$result = in_array(15, $ids);

var_dump($result);                          //  bool(true)
```

```php
$ids = [10, '15', '20', 30];
$result = in_array(15, $ids, true);

var_dump($result);                          //  bool(false)
```

```php
$colors = [
	'red',
    'green',
    'blue',
    'yellow'
];

if (in_array('green', $colors)) {
	echo 'color found';
} else {
	echo 'color are not found';
}
```

### PHP array_reverse()

The array_reverse() function accepts an array and returns a new array with the order of elements in the input array reversed.

```php
array_reverse ( array $array , bool $preserve_keys = false ) : array
```

The `array_reverse()` function has two parameters:

-   `$array` is the input array
-   `$preserve_keys` determines if the numeric keys should be preserved. If `$preserve_keys` is true, the numeric key of elements in the new array will be preserved. The `$preserve_keys` doesn’t affect the `non-numeric` keys.


```php
$numbers = [10, 20, 30];
$reversed = array_reverse($numbers);

var_dump($reversed);
var_dump($numbers);
```

```php
$book = [
	'PHP Awesome',
	999,
	['Programming', 'Web development'],
];

$unpreserved = array_reverse($book);
var_dump($unpreserved);

$preserved = array_reverse($book, true);
var_dump($preserved);
```

### PHP array_merge()

To merge one or more arrays into an array, you use the `array_merge()` function:

```php
array_merge ( array ...$arrays ) : array
```

Example:

```php
$server_side = ['PHP'];
$client_side = ['JavaScript', 'CSS', 'HTML'];

$full_stack = array_merge($server_side, $client_side);

var_dump($full_stack);
```

```php
$before = [
	'PHP' => 2,
	'JavaScript' => 4,
	'HTML' => 4,
	'CSS' => 3
];

$after = [
	'PHP' => 5,
	'JavaScript' => 5,
	'MySQL' => 4,
];

$skills = array_merge($before, $after);

var_dump($skills);
```

## PHP Spread Operator

PHP 7.4 introduced the spread operator to the `array` expression. PHP uses the three dots (...) to denote the spread operator.

```php
...array_var
```

Example:

```php
$numbers = [4, 5];

$scores1 = [1, 2, 3, ...$numbers];
var_dump($scores1);

$scores2 = [...$numbers, 3, 4];
var_dump($scores2);
```

```php
$even = [2, 4, 6];
$odd = [1, 2, 3];
$all = [...$odd, ...$even];

var_dump($all);
```
