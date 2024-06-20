# Section 15 - Working with Files

## PHP Open File

Before reading from or writing to a file, you need to open it. To open a file, you use the `fopen()` function as follows:

```php
fopen ( string $filename , string $mode , bool $use_include_path = false , resource $context = ? ) : resource
```
The fopen() returns the file pointer resource if it opens the file successfully or false if it fails to open the file.

The following table shows the type of access of the $mode parameter:

![file open mode](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/file.png)

To close a file, you pass the file pointer to the `fclose()` function:

```php
fclose ( resource $stream ) : bool
```

Example:

```php
$fileName = 'readme.txt';
$file = fopen($fileName, 'r');
if ($file) {
    // process the file
    // ...
    echo 'The file ' . $filename . ' is open';
    fclose($file);
}
```

## PHP File Exists

Check if a file exists using the `file_exists()` function:

```php
file_exists ( string $filename ) : bool
```

The `file_exists()` function accepts a filename and returns `true` if the file exists; otherwise it returns `false`.

Example:

```php
$fileName = 'readme.txt';

if (file_exists($fileName)) {
    $message = "The file $fileName exists";
} else {
    $message = "The file $fileName does not exist";
}
echo $message;
```

Check if a file exists using the is_file() function:

The `is_file()` function accepts a `$filename` and returns `true` if the `$filename` is a file and exists:

```php
is_file ( string $filename ) : bool
```

Example:

```php
$fileName = 'readme.txt';

if (is_file($fileName)) {
    $message = "The file $fileName exists";
} else {
    $message = "The file $fileName does not exist";
}
echo $message;
```

Check if a file exists and readable

To check if a file exists and is readable, you use the `is_readable()` function:

```php
is_readable ( string $filename ) : bool
```

The `is_readable()` function returns `true` if the `$filename` exists and readable, or `false` otherwise. Note that the `$filename` can be a directory.

```php
$fileName = 'readme.txt';

if (is_readable($fileName)) {
    $message = "The file $fileName exists";
} else {
    $message = "The file $fileName does not exist";
}
echo $message;
```
Check if a file exists and writable

Before writing to a file, you need to check the file exists and is writable. In this case, you can use the `is_writable()` function:

```php
is_writable ( string $filename ) : bool
```

The `is_writable()` function returns `true` if the `$filename` exists and writable, or `false` otherwise.

```php
$fileName = 'readme.txt';

if (is_writable($fileName)) {
    $message = "The file $fileName exists";
} else {
    $message = "The file $fileName does not exist";
}

echo $message;
```

## PHP Read File

Here’s the syntax of the `fread()` function:

```php
fread ( resource $stream , int $length ) : string|false
```

The `fread()` function returns the file contents or `false` if it fails to read.

To check if the file pointer is at end of file, you can pass it to the feof() function:

```php
feof ( resource $stream ) : bool
```

The `feof()` function returns `true` if the `$stream` is at the EOF or an error occurs. Otherwise, it returns `false`.

To read a file line by line, you use the `fgets()` function:

```php
fgets ( resource $handle , int $length = ? ) : string|false
```
Like the `fread()` function, the `fgets()` function accepts a file system pointer resource and up to a number of bytes to read. If you omit the `$length` argument, the `fread()` function will read the entire line.

```
New York	 New York	8,253,213
Los Angeles	 California	3,970,219
Chicago	 Illinois	2,677,643
Houston	 Texas	2,316,120
Phoenix	 Arizona	1,708,127
Philadelphia Pennsylvania	1,578,487
San Antonio	 Texas	1,567,118
San Diego	 California	1,422,420
Dallas	 Texas	1,343,266
San Jose	 California	1,013,616
```

Example:

Read the entire file into a string

```php
$fileName = './population.txt';
$file = fopen($fileName, 'r');

if ($file) {
    $contents = fread($file, filesize($fileName));
    fclose($file);
    echo nl2br($contents);
}
```

Example:

Read a file line by line

```php
$fileName = './population.txt';
$lines = [];

$file = fopen($fileName, 'r');

if (!$file) {
    return;
}

while (!feof($file)) {
    $lines[] = fgets($file);
}

print_r($lines);

fclose($file);
```

## PHP file_get_contents

The `file_get_contents()` function reads the entire file into a string. Here’s the syntax of the `file_get_contents()` function:

```php
file_get_contents ( 
    string $filename , 
    bool $use_include_path = false , 
    resource $context = ? , 
    int $offset = 0 , 
    int $maxlen = ? 
) : string|false
```

The `file_get_contents()` returns the file contents on success or false on failure.

### Using the file_get_contents() function to download a webpage example

```php
$html = file_get_contents('https://www.php.net/');
echo $html;
```

### Using the `file_get_contents()` function to read an entire file into a string example

```php
$fileName = 'readme1.txt';

if (!is_readable($fileName)) {
    die('File does not exist or is not readable');
}

echo file_get_contents($fileName);
```

## PHP file() Function

The `file()` function reads an entire file specified by a `$fileName` into an array:

```php
file ( string $filename , int $flags = 0 , resource $context = ? ) : array
```

![file function flag](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/file_func.png)


```
New York	 New York	8,253,213
Los Angeles	 California	3,970,219
Chicago	 Illinois	2,677,643
Houston	 Texas	2,316,120
Phoenix	 Arizona	1,708,127
Philadelphia Pennsylvania	1,578,487
San Antonio	 Texas	1,567,118
San Diego	 California	1,422,420
Dallas	 Texas	1,343,266
San Jose	 California	1,013,616
```

Example:

```php
$fileName = './population.txt';

$lines = file(
    $fileName,
    FILE_SKIP_EMPTY_LINES | FILE_IGNORE_NEW_LINES
);

if ($lines) {
    foreach ($lines as $line) {
        echo $line . PHP_EOL;
    }
}
```

## PHP Copy File

To copy a file from one location to another, you use the `copy()` function:

```php
copy ( string $source , string $dest , resource $context = ? ) : bool
```

The `copy()` function returns `true` if the file is copied successfully or `false` in case there was an error during copying the file.

Example:

```php
$source = 'readme.txt';
$dest = 'readme.bak';

echo copy($source, $dest)
    ? "The file $source was copied to $dest  successfully!"
    : "Error copying the file $source";
```

```php
$source = 'readme.txt';
$dest = 'readme.bak';

!file_exists($source) && die("The file $source does not exist");

file_exists($dest) && die("The file $dest already exists");

echo copy($source, $dest)
    ? "The file $source was copied to $dest  successfully!"
    : "Error copying the file $source";
```

## PHP Delete File

To delete a file, you use the `unlink()` function:

```php
unlink ( string $filename , resource $context = ? ) : bool
```

The `unlink()` function returns true if it deletes the file successfully or false otherwise. If the `$filename` doesn’t exist, the `unlink()` function also issues a warning and returns `false`.

Example:

```php
$fileName = 'readme.txt';

if (unlink($fileName)) {
	echo 'The file ' . $fileName . ' was deleted successfully!';
} else {
	echo 'There was a error deleting the file ' . $fileName;
}
```

## PHP Rename File

To rename a file to the new one, you use the `rename()` function:

```php
rename ( string $oldname , string $newname , resource $context = ? ) : bool
```

If the `$oldname` file and `$newname` has a different directory, the `rename()` function will move the file from the current directory to the new one and rename the file.

Example:

```php
$oldname = 'readme.txt';
$newname = 'readme_v2.txt';

if(rename($oldname, $newname)) {
    $message = 'file was renamed';
} else {
    $message = 'file was not renamed';
}

echo $message;
```

Rename and move the file

```php
$oldname = 'readme.txt';
$newname = 'public/readme.txt';

if(rename($oldname, $newname)) {
    $message = 'file was moved';
} else {
    $message = 'file was not moved';
}

echo $message;
```

## PHP filesize

The `filesize()` function returns the size of a given file in bytes:

```php
filesize ( string $filename ) : int|false
```

The `filesize()` function returns the size of the file specified by the `$filename` in bytes. In case of an error, the function returns `false`.

Example:

```php
$filename = 'readme.txt';
echo $filename,': ', filesize($filename),' bytes';
```

