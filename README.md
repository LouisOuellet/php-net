![GitHub repo logo](/dist/img/logo.png)

# phpNet
![License](https://img.shields.io/github/license/LouisOuellet/php-net?style=for-the-badge)
![GitHub repo size](https://img.shields.io/github/repo-size/LouisOuellet/php-net?style=for-the-badge&logo=github)
![GitHub top language](https://img.shields.io/github/languages/top/LouisOuellet/php-net?style=for-the-badge)
![Version](https://img.shields.io/github/v/release/LouisOuellet/php-net?label=Version&style=for-the-badge)

## Description
The phpNet library provides functionality to perform network-related tasks such as scanning a port, sending a ping, and performing a DNS lookup.

## Features
 - Allows for scanning a specified port on a specified IP address or domain name
 - Provides a method for sending a ping request to a specified IP address or domain name and returns the latency on success or false on failure
 - Allows for performing DNS lookups for a specified hostname and record type (A, AAAA, CNAME, MX, NS, PTR, SOA, TXT)
 - Uses the phpLogger library to log information, errors, and successes
 - Can be configured with options like logging level to control the amount of output produced by the library

## Why you might need it?
You might need it if you're developing a web application or network monitoring tool that requires such functionality. For example, you may need to check if a particular port is open on a server, or monitor the availability of a website by sending a ping request. Additionally, the phpNet library can be used to automate tasks like network reconnaissance and penetration testing.

## Can I use this?
Sure!

## License
This software is distributed under the [GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.en.html) license. Please read [LICENSE](LICENSE) for information on the software availability and distribution.

## Requirements
PHP >= 7.0

## Security
Please disclose any vulnerabilities found responsibly – report security issues to the maintainers privately.

## Installation
Using Composer:
```sh
composer require laswitchtech/php-net
```

## How do I use it?
In this documentations, we will use a table called users for our examples.

### Initialize
```php

// Import phpNet class into the global namespace
// These must be at the top of your script, not inside a function
use LaswitchTech\phpNet\phpNet;

// Load Composer's autoloader
require 'vendor/autoload.php';

// Initialize phpNet
$phpNet = new phpNet();
```
### Methods
#### config($option, $value)
Configures the library with the specified `option` and `value`. The only supported option is `level` which specifies the logging level.
```php
// Configure phpNet Log Level to Debug
$phpNet->config("level",5);
```

#### scan($ip, $port, $timeout)
Scans a network port on the specified IP address. Returns `true` if the port is open, and `false` otherwise.
```php
// Scan a Port
$phpNet->scan("google.com","HTTPS");
$phpNet->scan("google.com",443);
```

#### ping($ip)
Sends a ping to the specified IP address and returns the latency on success or `false` on failure.
```php
// Ping an IP
$phpNet->ping("127.0.0.1");
$phpNet->ping("::1");
$phpNet->ping("google.com");
```

#### lookup($hostname, $type)
Performs a DNS lookup for the specified hostname and returns an array of IP addresses on success, or `false` on failure.
```php
// Lookup a Domain
$phpNet->lookup("google.com");
$phpNet->lookup("google.gov.us");
```
