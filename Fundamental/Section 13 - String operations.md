# Section 13 - String operations

## PHP strlen()

The `strlen()` function returns the length of a specified string. Here’s the syntax of the `strlen()` function:

```php
strlen ( string $string ) : int
```

Example:

```php
echo strlen('gitmag');                  // 6
```

## PHP substr()

The `substr()` function accepts a string and returns a substring from the string.

```php
substr ( string $string , int $offset , int|null $length = null ) : string
```

Example:

```php
$str = 'PHP substring';

$result = substr($str, 0, 3);
echo $result;                           // PHP

// $result = substr($str, 3, 3); 
// echo $result;                           // sub

// $result = substr($str, -6);
// echo $result;                           // string
```

## PHP strpos()

The PHP `strpos()` function returns the index of the first occurrence of a substring within a string.

```php
strpos ( string $haystack , string $needle , int $offset = 0 ) : int|false
```

Example:

```php
$str = 'To do or not to do';

$position = strpos($str, 'do');
echo $position;                         // 3

// $position = strpos($str, 'do', 4);
// echo $position;                         // 16

// $position = strpos($str, 'dooooo', 4);
// var_dump($position);                         // false

// $position = strpos($str, 'To');
// echo $position;                         // 0
```

## PHP str_replace()

The PHP `str_replace()` function returns a new string with all occurrences of a substring replaced with another string.

```php
str_replace ( 
    array|string $search , 
    array|string $replace , 
    string|array $subject , 
    int &$count = null 
) : string|array
```

Example:

```php
$str = 'Hello there';
$new_str = str_replace('Hello', 'Hi', $str);

echo $new_str . "\n";                       // Hi there
echo $str . "\n";                           // Hello there
```


```php
$str = 'Hi, hi, hi';
$new_str = str_replace('hi', 'bye', $str, $count);

echo $count;                                // 2
```

```php
$str = 'The quick brown fox jumps over the lazy dog';
$animals = ['fox', 'dog'];
$new_animals = ['wolf', 'cat'];

$new_str = str_replace($animals, $new_animals, $str);

echo $new_str;                              // The quick brown wolf jumps over the lazy cat
```

## PHP str_ireplace()

To search for a string case-insensitively and replace it with a replacement string, you use the `str_ireplace()` function. For example:

```php
$str = 'Hi, hi, hi';
$new_str = str_ireplace('hi', 'bye', $str, $count);

echo $new_str; // bye, bye, bye
```

## PHP implode()

The PHP `implode()` function allows you to join an array of strings by a separator. Here’s the syntax of the `implode()` function:

```php
implode ( string $separator , array $array ) : string
```

Example:

```php
$columns = ['first_name', 'last_name', 'email'];
$str = implode(',', $columns);

echo $str;                                  // first_name,last_name,email
```

## PHP explode()

The PHP `explode()` function returns an array of strings by splitting a string by a separator. The following shows the syntax of the `explode()` function:

```php
explode ( string $separator , string $string , int $limit = PHP_INT_MAX ) : array
```

Example:

```php
$str = 'first_name,last_name,email,phone';
$columns = explode(',', $str);

print_r($columns);
```

```php
$str = 'first_name,last_name,email,phone';
$columns = explode(',', $str, 3);

print_r($columns);
```

## PHP trim()

The `trim()` function removes the whitespaces or other characters from the beginning and end of a string.

```php
trim ( string $string , string $characters = " \n\r\t\v\0" ) : string
```

Example:

```php
$str = ' PHP  ';
$new_str = trim($str);

var_dump($new_str);
```

```php
$uri = '/api/v1/posts/';

echo trim($uri, '/');
```

## PHP ltrim

The PHP `ltrim()` function removes the whitespace characters or other characters from the beginning of a string.

```php
ltrim ( string $string , string $characters = " \n\r\t\v\0" ) : string
```

Example:

```php
$title = '  PHP tutorial';
$clean_title = ltrim($title);

var_dump($clean_title);
```

## PHP rtrim

To remove the whitespace characters or other characters from the end of a string, you use the PHP `rtrim()` function.

```php
rtrim ( string $string , string $characters = " \n\r\t\v\0" ) : string
```

Example:

```php
$title = 'PHP tutorial   ';
$clean_title = rtrim($title);

var_dump($clean_title);
```

## PHP str_contains()

The PHP `str_contains()` function checks if a string contains a substring. Here’s the syntax of the `str_contains()` function:

```php
str_contains ( string $haystack , string $needle ) : bool
```

Example:

```php
$haystack = 'PHP is cool.';

$result = str_contains($haystack, 'PHP');
var_dump($result);
```

## PHP strtolower()

The `strtolower()` function accepts a string and returns a new string with all alphabetic characters converted to lowercase.

```php
strtolower ( string $string ) : string
```

Example:

```php
echo strtolower('PHP');
```

## PHP strtoupper()

The `strtoupper()` function accepts a string and returns a new string with all alphabetic characters converted to uppercase.

```php
strtoupper ( string $string ) : string
```

Example:

```php
echo strtoupper('php');
```

## PHP ucfirst()

The `ucfirst()` function accepts a string and returns a new string with the first character converted to uppercase if that character is alphabetic.

```php
ucfirst ( string $string ) : string
```

Example:

```php
$first_name = 'sohrab';
$last_name = 'azinfar';

echo ucfirst($first_name) . ' ' . ucfirst($last_name); 
```

## PHP ucwords()

The `ucwords()` function accepts a string and returns a new string with the first character of each word converted to uppercase:

```php
ucwords ( string $string , string $separators = " \t\r\n\f\v" ) : string
```

Example:

```php
$name = 'sohrab azinfar';
echo ucwords($name);

$name = 'SOHRAB AZINFAR';
echo ucwords($name);

$name = "reza al'mahdi";
echo ucwords($name);

$name = "reza al'mahdi";
echo ucwords($name, " \t\r\n\f\v'");
```
