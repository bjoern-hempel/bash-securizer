# Bash Webapplication Securizer

A tool to check the security of web applications.

## Installation

```bash
user$ sudo mkdir /opt/bash-securizer
user$ sudo chown $(id -un):$(id -gn) /opt/bash-securizer && chmod 775 /opt/bash-securizer
user$ git clone git@github.com:bjoern-hempel/bash-securizer.git /opt/bash-securizer/.
user$ sudo ln -s /opt/bash-securizer/bin/check /usr/local/bin/bash-securizer
user$ bash-securizer --help
```

## Uninstalling

```bash
user$ sudo rm /usr/local/bin/bash-securizer
user$ sudo rm -r /opt/bash-securizer
```

## Basics

```bash
user$ bash-securizer --help
Usage: bash-securizer [OPTIONS] url

  This script checks a given url for security.

Options
         --show-informations       Show all informations next to the test.
         --show-dns                Show the dns settings next to the test.
         --show-header             Show all headers next to the test.
         --show-software           Show the software installation next to the test.
         --show-all                Show all informations.

  -b,    --bash                    Returns the result in bash text format.
  -j,    --json                    Returns the result in JSON format.
  -m,    --markdown                Returns the result in MARKDOWN format.

         --show-test-count         Only shows the test count results
         --show-test-percent       Only shows the percent value of test result
         --show-test-label         Only shows the test label

         --verbose                 Switch this script into verbose mode.
  -h,    --help                    Shows this help.
  -v,    --version                 Shows the version number.

```

### Simply run the tool

```bash
user$ bash-securizer ressourcenmangel.de

[http status]  HTTP status code 200:               Test passed.
[ssl]          HTTPS check:                        Test passed.
[ssl]          SSL certificate check:              Test passed.
[header]       X-Powered-By:                       Test passed.
[header]       X-Generator:                        Test passed.
[header]       Cookie Security:                    Test passed.
[header]       HTTP Strict Transport Security:     Test passed.
[header]       Content-Security-Policy:            Test passed.
[header]       X-XSS-Protection Header:            Test passed.
[header]       X-Content-Type-Options:             Test passed.
[header]       X-Frame-Options:                    Test passed.
[header]       Referrer-Policy:                    Test passed.
[header]       Feature-Policy:                     Test passed.
[header]       Server-Header:                      Test passed.
[html]         Secure-Links:                       Test passed.
[html]         Metadata:                           Test passed.
---------------------------------------------------------------
[summary]      State:                              Test passed.
```

### Show some more informations and hints

```bash
user$ bash-securizer ressourcenmangel.de --verbose

[http status]  HTTP status code 200:               Test passed.
[ssl]          HTTPS check:                        Test passed.
[ssl]          SSL certificate check:              Test passed.
                                                   → 56 days left
[header]       X-Powered-By:                       Test passed.
[header]       X-Generator:                        Test passed.
[header]       Cookie Security:                    Test passed.
[header]       HTTP Strict Transport Security:     Test passed.
[header]       Content-Security-Policy:            Test passed. (But check the following warnings)
                                                   → It is not recommend to use the setting "unsafe-inline".
[header]       X-XSS-Protection Header:            Test passed.
[header]       X-Content-Type-Options:             Test passed.
[header]       X-Frame-Options:                    Test passed.
[header]       Referrer-Policy:                    Test passed.
[header]       Feature-Policy:                     Test passed.
[header]       Server-Header:                      Test passed. (But check the following warnings)
                                                   → If possible, disable the following content: "Apache"
[html]         Secure-Links:                       Test passed.
[html]         Metadata:                           Test passed.
---------------------------------------------------------------
[summary]      State:                              Test passed.
                                                   → 16/16 tests passed.
```

## Some integration modes

### Show the number of passed tests

```bash
user$ bash-securizer ressourcenmangel.de --show-test-count
16/16
```

### Show the percentage of passed tests

```bash
user$ bash-securizer ressourcenmangel.de --show-test-percent
93%
```

### Show the test label

```bash
user$ bash-securizer ressourcenmangel.de --show-test-label
A-
```

### Combine the outputs

```bash
user$ bash-securizer ressourcenmangel.de --show-test-count --show-test-percent --show-test-label
16/16 93% A-
```

## A. Authors

* **Björn Hempel** - *Initial work* - [Björn Hempel](https://github.com/bjoern-hempel)

## B. License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

## C. Closing words

Have fun! :)
