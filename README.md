mPDF is a PHP class which generates PDF files from UTF-8 encoded HTML. It is based on [FPDF](http://www.fpdf.org/)
and [HTML2FPDF](http://html2fpdf.sourceforge.net/) (see [CREDITS](CREDITS.txt)), with a number of enhancements.
mPDF was written by Ian Back and is released under the [GNU GPL v2 licence](LICENSE.txt).

[![Build Status](https://travis-ci.org/mpdf/mpdf.svg?branch=development)](https://travis-ci.org/mpdf/mpdf)

Installation
============

Official installation method is via composer and its packagist package [mpdf/mpdf](https://packagist.org/packages/mpdf/mpdf).

```
$ composer require mpdf/mpdf
```

Usage
-----

The simplest usage of the library would be as follows:

```php
<?php

require __DIR__ . '/vendor/autoload.php';

$mpdf = new \Mpdf\Mpdf();
$mpdf->writeHTML('<h1>Hello world!</h1>')
$mpdf->Output();

```

This will output the HTML inluine to the browser.

Setup & Configuration
---------------------

All [configuration directives](https://mpdf.github.io/reference/mpdf-variables/overview.html) can be set by the last parameter of the constructor.

It is recommended to set one's own temporary directory for mPDF via `tempDir` and `fontTempDir` configuration variables. The directory must have write permissions (mode `775` is recommended).


```php
<?php

$mpdf = new \Mpdf\Mpdf('', 'A4', '', 15, 15, 16, 16, 9, 9, 'P', ['tempDir' => __DIR__ . '/tmp']);

```

By default, the temporary directory will be inside vendor directory and will have the permissions from post_install composer script.

For more information about custom temporary directory see the note on
[Folder for temporary files](https://mpdf.github.io/installation-setup/folders-for-temporary-files.html)
in the section on Installation & Setup in the [manual](https://mpdf.github.io/).

If you have problems, please read the section on [troubleshooting](https://mpdf.github.io/troubleshooting/known-issues.html) in the manual.

Online manual
=============

Online manual is available at https://mpdf.github.io/.

Unit Testing
============

Unit testing for mPDF is done using [PHPUnit](https://phpunit.de/).

To get started, run `composer install` from the command line while in the mPDF root directory
(you'll need [composer installed first](https://getcomposer.org/download/)).

To execute tests, run `vendor/bin/phpunit` from the command line while in the mPDF root directory.

Any assistance writing unit tests for mPDF is greatly appreciated. If you'd like to help, please
note that any PHP file located in the `/tests/` directory will be autoloaded when unit testing.
