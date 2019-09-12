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

### Show all information collected next to the test

```bash
user$ bash-securizer ressourcenmangel.de --show-all --verbose

===============================================================
INFORMATIONS:
===============================================================
Check index:                                      93%
Check index degraded:                             93%
Label:                                            A-
Given address:                                    ressourcenmangel.de
Used address:                                     http://ressourcenmangel.de
Last redirect:                                    https://www.ressourcenmangel.de/startseite.html
Secure connection:                                yes
Valid days ssl certificate:                       56
Header size:                                      1041 Byte
Body size:                                        80923 Byte
Full domain:                                      www.ressourcenmangel.de
Domain:                                           ressourcenmangel.de
IP address:                                       87.230.85.104
nameserver:                                       ns1.hans.hosteurope.de
                                                  ns2.hans.hosteurope.de
provider:                                         Hosteurope GmbH
Successful tests:                                 16
Failed tests:                                     0
Total number of tests:                            16
Operating system:                                 mac
===============================================================


===============================================================
INSTALLED SOFTWARE:
===============================================================
awk:       [ installed ] → version: awk version 20070501
bc:        [ installed ] → version: bc 1.06
cat:       [ installed ]
curl:      [ installed ] → version: curl 7.65.2 (x86_64-apple-darwin13.4.0) libcurl/7.65.2 OpenSSL/1.1.1c zlib/1.2.11 libssh2/1.8.2
cut:       [ installed ]
grep:      [ installed ] → version: grep (BSD grep) 2.5.1-FreeBSD
head:      [ installed ]
host:      [ installed ]
openssl:   [ installed ] → version: OpenSSL 1.1.1c  28 May 2019
printf:    [ installed ]
rev:       [ installed ]
sed:       [ installed ]
sort:      [ installed ] → version: 2.3-Apple (99)
tail:      [ installed ]
tr:        [ installed ]
wc:        [ installed ]
whois:     [ installed ]
xargs:     [ installed ]
xmllint:   [ installed ] → version: xmllint: using libxml version 20909
===============================================================


===============================================================
DNS SETTINGS:
===============================================================
Trying "ressourcenmangel.de"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 60612
;; flags: qr rd ra; QUERY: 1, ANSWER: 8, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ressourcenmangel.de.		IN	ANY

;; ANSWER SECTION:
ressourcenmangel.de.	19072	IN	NS	ns1.hans.hosteurope.de.
ressourcenmangel.de.	19072	IN	NS	ns2.hans.hosteurope.de.
ressourcenmangel.de.	19072	IN	MX	1 ressourcenmangel-de.mail.protection.outlook.com.
ressourcenmangel.de.	19072	IN	TXT	"v=spf1 a include:spf.protection.outlook.com a:mailrelay.netways.de ~all"
ressourcenmangel.de.	19072	IN	TXT	"google-site-verification=mLLc8XJ7vSatpZ1MsGp585mBiVQu9UKT9N5SWLAzkls"
ressourcenmangel.de.	32	IN	SOA	ns1.hans.hosteurope.de. hostmaster.ressourcenmangel.de. 2019050217 16384 2048 1048576 2560
ressourcenmangel.de.	19072	IN	A	87.230.85.104
ressourcenmangel.de.	19072	IN	AAAA	2a01:488:66:1000:57e6:5568::1

Received 408 bytes from 8.8.8.8#53 in 35 ms
===============================================================


===============================================================
HEADER:
===============================================================
01 HTTP/1.1 200 Ok
02 Date: Thu, 12 Sep 2019 21:27:13 GMT
03 Server: Apache
04 Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
05 Feature-Policy: geolocation 'none'; midi 'none'; camera 'none'; usb 'none'; magnetometer 'none'; accelerometer 'none'; vr 'none'; speaker 'none'; ambient-light-sensor 'none'; gyroscope 'none'; microphone 'none'
06 Expires: Fri, 06 Jun 1975 15:10:00 GMT
07 Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
08 Pragma: no-cache
09 Vary: User-Agent,Accept-Encoding
10 Last-Modified: Thu, 12 Sep 2019 21:27:13 GMT
11 Set-Cookie: __HOST-PHPSESSID=vpgk5veesi2ubtrd11p7jehgm6; path=/; secure; HttpOnly; SameSite=Lax
12 Content-Security-Policy: script-src-elem 'self' https://code.jquery.com https://ajax.googleapis.com https://fonts.googleapis.com https://www.google-analytics.com https://connect.facebook.net 'unsafe-inline';
13 X-XSS-Protection: 1; mode=block
14 X-Content-Type-Options: nosniff
15 X-Frame-Options: SAMEORIGIN
16 Referrer-Policy: no-referrer-when-downgrade
17 Content-Type: text/html; charset=utf-8
===============================================================


===============================================================
TESTS:
===============================================================
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
===============================================================

```

## Some integration modes

The integration modes are intended to integrate this script into other test scripts. This allows tests to be carried out automatically and the test results to be read in easily. Successful tests show the exit code 0. Executions with at least one failed test return the exit code 1.

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
