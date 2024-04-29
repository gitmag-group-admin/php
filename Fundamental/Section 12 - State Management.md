# Section 12 - State Management

## PHP Cookies

The web works based on the HTTP protocol. The HTTP protocol is stateless.

When the web browser requests a page from a web server, the webserver responds with the page content. Later, the same web browser requests the same page again, and the webserver has no information that the request is from the same web browser.

Cookies solve this stateless challenge.

A cookie is a piece of data that a web server sends to the web browser. The web browser may store it and send it back in the subsequent requests to the same web server. The web server knows that two requests come from the same web browser by using the same cookie.

Cookies are also known as web cookies, HTTP cookies, or browser cookies. We’ll use the cookies to make it short.

The following flow chart illustrates how cookies work:

![Cookies](https://raw.githubusercontent.com/gitmag-group-admin/php/main/images/php-cookies.png)

### Setting a cookie in PHP

PHP makes it easy to work with cookies using the `setcookie()` function.

```php
setcookie ( 
    string $name , 
    string $value = "" , 
    int $expires = 0 , 
    string $path = "" , 
    string $domain = "" , 
    bool $secure = false , 
    bool $httponly = false 
): bool
```
As of PHP 7.3.0, you can use the same setcookie() function with an alternative signature:

```php
setcookie ( 
    string $name , 
    string $value = "" , 
    array $options = [] 
) : bool
```
The $options argument is an array that has one or more keys, such as `expires`, `path`, `domain`, `secure`, `httponly`.

### $_COOKIE

The `$_COOKIE` an associative array that stores the HTTP cookies.

```php
$_COOKIE['cookie_name']
```

To check if a cookie is set, you use the `isset()` function:

```php
if(isset($_COOKIE['cookie_name'])) {

}
```

### Deleting a cookie

```php
unset($_COOKIE['cookie_name']);
setcookie('cookie_name', null, time()-3600); 
```

## PHP Session

Sessions allow you to store data on the web server associated with a session id. Once you create a session, PHP sends a cookie that contains the session id to the web browser. In the subsequent requests, the web browser sends the session id cookie back to the web server so that PHP can retrieve the data based on the session id.

### Creating a new session

To create a new session, you call the `session_start()` function:

```php
session_start();
```

When the session_start() runs at the first time, PHP generates a unique session id and passes it to the web browser in the form of a cookie named `PHPSESSID`.

```php
$_SESSION['session_name'] = 'value'; 
```

### Accessing session data

```php
if(isset($_SESSION['session_name'])) {

}
```

### Deleting the session data

Whenever you close the web browser, PHP automatically deletes the session. Sometimes, you want to explicitly delete a session, e.g., when you click the logout link. In this case, you can use the `session_destroy()` function

```php
session_destroy();
```****
