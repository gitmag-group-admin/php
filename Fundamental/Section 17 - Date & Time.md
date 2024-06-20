# Section 17 - Date and time

## PHP time

Computers store a date and time as a `UNIX` timestamp or a timestamp in short.

### Getting the current time

To get the current time, you use the `time()` function:

```php
function time(): int
```

The `time()` function returns the current UNIX timestamp since Epoch (January 1 1970 00:00:00 GMT). For example:

```php
echo time(); // 1626752728
```

The return value is a big integer that represents the number of seconds since Epoch. To make the time human-readable, you use the `date()` function. For example:

```php
$current_time = time();
echo date('Y-m-d g:ia', $current_time) . "\n";
```

The `date()` function has two parameters.

### Adding to / subtracting from a timestamp

```php
$current_time = time();
// 7 days later
$one_week_later =  $current_time + 7 * 24 * 60 * 60;

echo date('Y-m-d g:ia',$one_week_later);
```

### timezone

By default, the `time()` function returns the current time in the timezone specified in the PHP configuration file (php.ini).

To get the current timezone, you can use the `date_default_timezone_get()` function:

```php
echo echo date_default_timezone_get(); 
```

The following shows how to use the `date_default_timezone_set()` function to set the current timezone to the UTC timezone:

```php
date_default_timezone_set('UTC');
```

### Making a Unix timestamp

To make a Unix timestamp, you use the `mktime()` function:

```php
mktime(
    int $hour,
    int|null $minute = null,
    int|null $second = null,
    int|null $month = null,
    int|null $day = null,
    int|null $year = null
): int|false
```

Example:

```php
echo 'July 13, 2021 is on a ' . date('l', mktime(0, 0, 0, 7, 13, 2021));
```

## PHP date

The `date()` function formats a timestamp using a specified format:

```php
date(string $format, int|null $timestamp = null): string
```

[PHP date format parameters](https://www.w3schools.com/php/func_date_date.asp)

Example:

Using the PHP `date()` function to show the current year example

```php
echo date('Y');
echo date("Y-m-d H:i:s");
```

