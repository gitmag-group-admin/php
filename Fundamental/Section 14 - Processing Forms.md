# Section 14 - Processing Forms

## PHP Form

To create a form, you use the `<form>` element as follows:

```html
<form action="form.php" method="post">

</form>
```

### HTTP POST method

If a form uses the POST method, the web browser will include the form data in the HTTP request’s body. After submitting the form, you can access the form data via the associative array `$_POST` in PHP.

`index.html` file

```html
<form action="form.php" method="post">
    <div>
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" />
    </div>
    <button type="submit">Submit</button>
</form>
```

`form.php` file

```php
if (isset($_POST['name'])) {
	var_dump($_POST['name']);
}
```

### HTTP GET method

When you submit a form using the GET method, you can access the form data in PHP via the associative array `$_GET`.

```
http://localhost/form.php?name=sohrab
```

`index.html` file

```html
<form action="form.php" method="get">
    <div>
        <label for="name">Name:</label>
        <input type="name" id="name" name="name" />
    </div>
    <button type="submit">Submit</button>
</form>
```

`index.php` file

```php
if (isset($_GET['name'])) {
	var_dump($_GET['name']);
}
```

## PHP filter_has_var

The `filter_has_var()` function checks if a variable of a specified type exists. Here’s the syntax of the `filter_has_var()` function:

```php
filter_has_var ( int $input_type , string $var_name ) : bool
```

Example:

```php
if (filter_has_var(INPUT_POST, 'name')) {
	echo 'The name variable exists:' . $_POST['name'];
} else {
	echo 'The name is required!';
}
```

## PHP filter_var

PHP has the `filter_var()` function that supports you to both sanitize and validate data. Here’s the syntax of the `filter_var()` function:

```php
filter_var ( mixed $value , int $filter = FILTER_DEFAULT , array|int $options = 0 ) : mixed
```

```
http://localhost:8080/index.php?id=10
```

Example:

```php
if (filter_has_var(INPUT_GET, 'id')) {
	// sanitize id
	$id = filter_var($_GET['id'], FILTER_SANITIZE_NUMBER_INT);
	// show the id
	var_dump($id);
} else {
	echo 'id is required.';
}
```

```php
if (filter_has_var(INPUT_POST, 'email')) {
	// sanitize email
	$email = filter_var($_POST['email'], FILTER_VALIDATE_EMAIL);
	// show the email
	var_dump($email);
} else {
	echo 'email is required.';
}
```

## PHP Checkbox

A checkbox allows you to select a single value for submission in a form. To create a checkbox, you use the `input` element with the type `checkbox` as follows:

```html
<input type="checkbox" name="checkbox_name" value="checkox_value">
```

```php
echo $_POST['checkbox_name']; // 'checkbox_value'

// if (isset($_POST['checkbox_name']) ) {
//     echo 'checkbox was seted';
// }

// if(filter_has_var(INPUT_POST,'checkbox_name')) {
//     echo 'checkbox was seted';
// }
```

## PHP Multiple Checkboxes

The following example shows a form that consists of three checkboxes with the same name `(colors[])` with different values `"red"`, `"green"`, and `"blue"`.

```html
<form action="index.php" method="post">
	<input type="checkbox" name="colors[]" value="red" id="color_red" />
	<label for="color_red">Red</label>

	<input type="checkbox" name="colors[]" value="green" id="color_green" />
	<label for="color_red">Green</label>

	<input type="checkbox" name="colors[]" value="blue" id="color_blue" />
	<label for="color_red">Blue</label>
        <input type="submit" value="Submit">
</form>
```

`index.php` file

```php
if (isset($_POST['colors'])) {
    print_r($_POST['colors']);
}

// if (filter_has_var(INPUT_POST, 'colors')) {
//     print_r($_POST['colors']);
// }
```

## PHP Radio Button

To create a radio button, you use the `<input>` element with the type `radio`. For example:

```html
<input type="radio" name="contact" id="contact_email" value="email" />
<label for="contact_email">Email</label>

<input type="radio" name="contact" id="contact_phone" value="phone" />
<label for="contact_phone">Phone</label>
```

```php
echo $_POST['contact']; // 'radio_value'

// if (isset($_POST['contact']) ) {
//     echo $_POST['contact'];
// }

// if(filter_has_var(INPUT_POST,'contact')) {
//     echo $_POST['contact'];
// }
```

## PHP Select Option

The `<select>` is an HTML element that provides a list of options. The following shows how to define a `<select>` element in HTML:

```html
<label for="color">Background Color:</label>
<select name="color" id="color">
	<option value="">--- Choose a color ---</option>
	<option value="red">Red</option>
	<option value="green">Green</option>
	<option value="blue">Blue</option>
</select>
```

`index.php` file

```php
if (isset($_POST['color'])) {
    echo $_POST['color'];
}

if(filter_has_var(INPUT_POST,'color')) {
    echo $_POST['color'];
}
```
