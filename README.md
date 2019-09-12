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

## A. Authors

* **Björn Hempel** - *Initial work* - [Björn Hempel](https://github.com/bjoern-hempel)

## B. License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

## C. Closing words

Have fun! :)
