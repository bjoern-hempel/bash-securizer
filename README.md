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

## A. Authors

* **Björn Hempel** - *Initial work* - [Björn Hempel](https://github.com/bjoern-hempel)

## B. License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

## C. Closing words

Have fun! :)
