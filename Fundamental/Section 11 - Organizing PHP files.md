# Section 11 - Organizing PHP files

## PHP Include

The `include` construct allows you to load the code from another file into a file. Here’s the syntax of the include construct:

```php
include 'path_to_file';
```

Example

```php
include 'functions.php';
```

PHP include example

```
.
├── index.php
├── functions.php
├── inc
│   ├── footer.php
│   └── header.php
└── public
    ├── css
    │   └── style.css
    └── js
        └── app.js
```

function.php file

```php
function showTitle()
{
	return 'Gitmag Website';
}

function showContent()
{
	return 'Website content';
}

```

index.php file

```php
<?php include 'functions.php'; ?>

<?php include 'inc/header.php'; ?>

	<h1><?= showTitle(); ?></h1>
	<p><?= showContent(); ?></p>

<?php include 'inc/footer.php'; ?>
```

header.php file

```php
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<link rel="stylesheet" href="public/css/style.css">
		<title>Gitmag test</title>
	</head>
	<body>
```

footer.php file

```php
	<script src="js/app.js"></script>
</body>
</html>
```

## PHP include_once

In the `include` tutorial, you learned how to load the code from another file using the `include` construct.

```php
include_once 'path_to_file';
```

index.php file

```php
<?php include_once 'functions.php'; ?>

<?php include_once 'inc/header.php'; ?>

	<h1><?= showTitle(); ?></h1>
	<p><?= showContent(); ?></p>

<?php include_once 'inc/footer.php'; ?>
```

## PHP require 

PHP `require` construct loads the code from an file into a script and executes that code. The following shows the syntax of the `require` construct:

```php
require 'path_to_file';
```

function.php file

```php
function showTitle()
{
	return 'Gitmag Website';
}

function showContent()
{
	return 'Website content';
}

```

index.php file

```php
require 'functions.php';

echo showTitle();
```
