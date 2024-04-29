# Section 10 - Advanced Array Operations

## PHP array_map

Suppose that you have an `array` that holds the lengths of squares:

```php
array_map ( callable $callback , array $array ) : array
```

Example:

```php
$numbers = [10, 20, 30, 40, 50];

$newArray = array_map(fn ($item) => $item * 10 , $numbers);

print_r($newArray);
```

## PHP array_walk()

The `array_walk()` function runs each array element in a user-defined function

```php
array_walk ( array $array, callable $callback) : bool
```

Example:

```php
$people = ['ali', 'reza', 'mohammad', 'hossein'];

$result = array_walk($people , function ($value, $key) {
	echo "index: {$key} is {$value}\n";
});

var_dump($result);

// foreach($people as $key => $value) {
// 	echo "index: {$key} is {$value}\n";
// }
```

## PHP array_filter()

When you want to filter elements of an `array`, you often `iterate over the elements` and check whether the result array should include each element.

```php
 array_filter(array $array, callback $callback, flag)
```

Example:

```php
$info = [
	'first' => 'Shorab',
	'last' => 'Azinfar',
	'password' => 'secret',
	'email' => 'sohrab-az@gamil.com'
];

$filtered = array_filter(
	$info,
	fn ($value) => $value !== 'secret'
);

print_r($filtered);
```

```php
$info = [
	'first' => 'Shorab',
	'last' => 'Azinfar',
	'password' => 'secret',
	'email' => 'sohrab-az@gamil.com'
];

$filtered = array_filter(
	$info,
	fn ($key) => $key !== 'password',
	ARRAY_FILTER_USE_KEY
);

print_r($filtered);
```

```php
$info = [
	'first' => 'Shorab',
	'last' => 'Azinfar',
	'password' => 'secret',
	'email' => 'sohrab-az@gamil.com'
];

$filtered = array_filter(
	$info,
	fn ($value, $key) => $key !== 'password' and $value !== 'sohrab-az@gamil.com',
	ARRAY_FILTER_USE_BOTH
);

print_r($filtered);
```

## PHP array_diff()

The `array_diff()` function compares the values of two (or more) arrays, and returns the differences.

```php
array_diff ( ... array $array): array
```

Example:

```php
$array1 = ["a" => "red", "b" => "green", "c" => "blue", "d" => "yellow"];
$array2 = ["e" => "red", "f" => "green", "g" => "blue"];

$result = array_diff($array1, $array2);
print_r($result);
```

## PHP array_slice()

The `array_slice()` function returns selected parts of an array.

```php
array_slice ( array $array, int $start, int $length, bool $preserve = false): array
```

Example:

```php
$colors = ["red", "green", "blue", "yellow", "brown"];

$newArray1 = array_slice($colors, 2);
print_r($newArray1);

// $newArray2 = array_slice($colors, 1, 2);
// print_r($newArray2);

// $newArray3 = array_slice($colors, 1, 2, true);
// print_r($newArray3);
```

Other example:

```php
$info = [
    'name' => 'ali',
    'family' => 'sadeghi',
    'age' => 30,
    'city' => 'tehran'
];

$newArray1 = array_slice($info, 1, 2, false);
print_r($newArray1);

// $newArray2 = array_slice($info, 1, 2, true);
// print_r($newArray2);
```
