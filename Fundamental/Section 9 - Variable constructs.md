# Section 9 - Variable constructs

## PHP isset

PHP `isset()` returns true if a variable is set and not null.

```php
isset(mixed $var): bool
```

Example:

```php
$name = 'sohrab';
$family = 'azinfar';
$age = 33;
$education = NULL;

var_dump(isset($name));
// var_dump(isset($family));
// var_dump(isset($age));
// var_dump(isset($education));
// var_dump(isset($skill));

// unset($age);
// var_dump(isset($age));
```

Other example:

```php
$person = [
	'name' => 'sohrab',
	'family' => 'azinfar',
	'age' => 33,
	'education' => null,
];

var_dump(isset($person['name']));
// var_dump(isset($person['family']));
// var_dump(isset($person['age']));
// var_dump(isset($person['education']));
// var_dump(isset($person['skill']));

// unset($person['age']);
// print_r($person);
// var_dump(isset($person['age']));
```

## PHP empty

The `empty()` construct accepts a variable and returns `true` if the variable is empty. Otherwise, it returns `false`.

```php
empty(mixed $v): bool
```

Example:

```php
$name = 'sohrab';
$family = '';
$age = 33;
$education = NULL;
$inClass = true;

var_dump(empty($name));
// var_dump(empty($family));
// var_dump(empty($age));
// var_dump(empty($education));
// var_dump(empty($inClass));
// var_dump(empty($skill));
```

falsy values: `false` , `0`, `0.0`, `"0"`, `''`, `null`, `[]`

## PHP is_null

PHP `is_null()` accepts a variable and returns `true` if that variable is null. Otherwise, it returns `false`.

```php
is_null(mixed $v): bool
```

Example:

```php
$name = 'sohrab';
$family = '';
$age = 33;
$education = NULL;
$inClass = true;

var_dump(is_null($name));
// var_dump(is_null($family));
// var_dump(is_null($age));
// var_dump(is_null($education));
// var_dump(is_null($inClass));
// var_dump(is_null($skill));
```

Similar functions to `is_null`, such as: `is_int`, `is_string`, `is_array`, `is_float`, ...
