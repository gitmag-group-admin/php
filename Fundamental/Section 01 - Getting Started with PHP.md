# Section 1. Getting Started with PHP

## What is PHP

### Introduction to PHP
PHP is a server-side and general-purpose scripting language that is especially suited for web development.

PHP originally stood for Personal Home Page. However, now, it stands for Hypertext Preprocessor.

PHP was created by Rasmus Lerdorf in 1994. It’s currently maintained by the PHP Development Team.

When you open a website on your web browser, for example, https://www.phptutorial.net. The web browser sends an HTTP request to a web server where phptutorial.net locates. The web server receives the request and responds with an HTML document. In this example, the web browser is a client while the web server is the server. The client requests for a page, and the server serves the request. PHP runs on the web server, processes the request, and returns the HTML document.

You can use PHP with all leading web servers such as Nginx, OpenBSD, and Apache. Some cloud environments also support PHP like Microsoft Azure and Amazon AWS.

PHP is quite flexible. It’s not just limited to processing HTML. PHP has built-in support for generating PDF, GIF, JPEG, and PNG images.

One notable feature of PHP is that it supports many databases, including MySQL, PostgreSQL, MS SQL, db2, Oracle Database, and MongoDB.

### What can PHP do
PHP has two main applications:

-   Server-side scripting – PHP is well-suited for developing dynamic websites and web applications.

-   Command-line scripting – like Python and Perl, you can run PHP script from the command line to perform administrative tasks like sending emails and generating PDF files.


### How PHP Works
The following illustrates how PHP works:

![How PHP Works](https://www.phptutorial.net/wp-content/uploads/2021/03/What-is-PHP-How-PHP-works.png)

-   First, the web browser sends an HTTP request to the web server, e.g., index.php.
-   Second, the PHP preprocessor that locates on the web server processes PHP code to generate the HTML document.
-   Third, the web server sends the HTML document back to the web browser.

### Advantages of PHP
Since PHP is designed for the web in the first place, it brings many advantages to web development:

-   Simple – PHP is quite easy to learn and get started.
-   Fast – PHP websites typically run very fast.
-   Stable – PHP is stable since it has been in existence for a long time.
-   Open-source and free – PHP is open source and free. It means that you don’t have to pay a license fee to use PHP to develop software products.
-   Community support – PHP has an active online community that helps you whenever you face an issue.

## Install PHP
Installing PHP on your computer allows you to safely develop and test a web application without affecting the live system.

To work with PHP locally, you need to have the following software:
-   **[PHP](https://www.php.net/)**
-   A web server that supports PHP. We’ll use the **[Apache Webserver](https://httpd.apache.org/)**.
-   A database server. We’ll use the **[MySQL database server](https://www.mysql.com/)**.

Therefore, it’s easier to find an all-in-one software package that includes PHP, a web server, and a database server. One of the most popular PHP development environments is **XAMPP**.

XAMPP is an easy install Apache distribution that contains PHP, MariaDB, and Apache webserver. XAMPP supports Windows, Linux, and macOS.

### Download XAMPP
To install XAMPP on windows, you can go to the **[XAMPP official website](https://www.apachefriends.org/index.html)** and download the suitable version for your platform.

## PHP Hello World

### PHP Hello World on the web browser
First, open the folder ```htdocs``` under the ```xampp``` folder. Typically, it locates at ```C:\xampp\htdocs```.

Second, create a new folder called ```helloworld```.

Third, create a new file called ```index.php``` under the ```helloworld``` folder and place the following code in the file:

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PHP - Hello, World!</title>
</head>
<body>
        <h1><?php echo 'Hello, World!'; ?></h1>
</body>
</html>
```

The code in the index.php file looks like a regular HTML document except the part ```<?php and ?>```.

The code between the opening tag ```<?php and closing tag ?>``` is PHP:

```php
<?php echo 'Hello, World!'; ?>
```

This PHP code prints out the ```Hello, World``` message inside the ```h1``` tag using the ```echo``` statement:

When PHP executes the ```index.php``` file, it evaluates the code and returns the ```Hello, World!``` message.

Fourth, launch a web browser and open the URL:

```url
http://localhost:8080/helloworld/
```
If you see the following on the web browser, then you’ve successfully executed the first PHP script:

![PHP hello world](https://www.phptutorial.net/wp-content/uploads/2021/03/PHP-Hello-World.png)

If you view the soure code of the page, you’ll see the following HTML code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PHP - Hello, World!</title>
</head>
<body>
        <h1>Hello, World!</h1>
</body>
</html>
```

### PHP Hello World on the command line

First, open the Command Prompt on Windows or Terminal on macOS or Linux.

Second, navigate to the folder c:\xampp\htdocs\helloworld\.

Third, type the following command to execute the index.php file:

```bash
c:\xampp\htdocs\helloworld>php index.php
```

You’ll see the HTML output:

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>PHP - Hello, World!</title>
</head>
<body>
        <h1>Hello, World!</h1>
</body>
</html>
```

Since the terminal doesn’t know how to render HTML to web, it just shows the pure HTML code.

To simplify the output, you can use the following code in the ```index.php```:

```php
<?php

echo 'Hello, World!';
```

If you execute the script again:

```bash
c:\xampp\htdocs\helloworld>php index.php
```

and you’ll see the following output:

```
Hello, World!
```

When you embed PHP code with HTML, you need to have the opening tag ```<?php``` and closing tag ```?>```. However, if the file contains only PHP code, you don’t need to the closing tag ```?>``` like the ```index.php``` above.
