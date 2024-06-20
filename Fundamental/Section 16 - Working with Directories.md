# Section 16 - Working with Directories

## PHP Open dir

To get the directory handle of a directory, you pass the directory path to the 'opendir()' function as follows:

```php
$dh = opendir('./public');
```
If an error occurs while opening the directory, the `opendir()` function returns false.

When you’re done with the directory, you need to close the directory handle by using the `closedir()` function:

```php
closedir($dh);
```

Note that the `readdir()` function returns the directories and files of the current directory specified by the directory handle. It doesn’t recursively returns the files and directories of the subdirectories.

Example:

```php
$dh = opendir('./public');

if ($dh) {
	while ($e = readdir($dh)) {
		if ($e !== '.' && $e !== '..') {
			echo $e , PHP_EOL;
		}
	}
}

closedir($dh);
```

Get the current directory:

To get the current directory, you use the `getcwd()` function:

```php
echo getcwd();
```

To change the current directory to a new one, you use the `chdir()` function:

```php
chdir('./dev');
echo getcwd();
```

### Create a new directory

To create a directory, you use the `mkdir()` function by passing the directory path. The `mkdir()` function returns true if it created the directory successfully of false otherwise.

```php
$dir = './public/img';

if (mkdir($dir)) {
	echo ' The dir ', $dir, 'created successfully!';
}

$dir = './public/assets';
mkdir($dir, 0644);
```

### Delete a directory

To delete a directory, you use the `rmdir()` function. And you need to have sufficient permissions to remove the directory.

```php
rmdir('./public/assets');
```

### Check if a path is a directory

To check if a path is a directory, you use the `is_dir()` function:

```php
is_dir ( string $filename ) : bool
```

The `is_dir()` function returns `true` if the $filename exists and is a directory. For example:

```php
$path = './public';

if (is_dir($path)) {
	echo $path, ' is a directory.';
}
```

## PHP dirname

The `dirname()` function accepts a path and returns a parent directory’s path:

```php
dirname ( string $path , int $levels = 1 ) : string
```

Example:

```php
echo '1.' , dirname("/htdocs/public") , PHP_EOL;
echo '2.' , dirname("/htdocs/") , PHP_EOL;
echo '3.' , dirname(".") , PHP_EOL;
echo '4.' , dirname("C:\\") , PHP_EOL;
echo '5.' , dirname("/htdocs/public/css/dev", 2);
```

## PHP basename

The `basename()` function returns the trailing name component of path:

```php
basename ( string $path , string $suffix = "" ) : string
```

Example:

```php
echo "1) ".basename("/htdocs/index.php", ".php").PHP_EOL;
echo "2) ".basename("/htdocs/index.php").PHP_EOL;
echo "3) ".basename("/htdocs/public").PHP_EOL;
echo "4) ".basename("/htdocs/").PHP_EOL;
echo "5) ".basename(".").PHP_EOL;
echo "6) ".basename("/");
```

## PHP pathinfo

The PHP `pathinfo()` function accepts a file path and returns its components:

```php
pathinfo ( string $path , int $flags = PATHINFO_ALL ) : array|string
```

The following table shows the valid flag values:

![php pathinfo flags](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/pathinfo.png)

Using the `pathinfo()` function to get all components of a file path

```php
$path = 'htdocs/phptutorial/index.php';

$parts = pathinfo($path);

print_r($parts);
```

Using the `pathinfo()` function to get only a specific component of a file path

```php
$path = 'htdocs/phptutorial/index.php';

$basename = pathinfo($path, PATHINFO_BASENAME);

echo $basename;
```

