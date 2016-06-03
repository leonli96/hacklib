# hacklib
![MIT License](https://img.shields.io/github/license/mashape/apistatus.svg)
[![Python 2.6|2.7](https://img.shields.io/badge/python-2.6|2.7-yellow.svg)](https://www.python.org/)
##### Toolkit for hacking enthusiasts using Python.
hacklib is a Python module for hacking enthusiasts. It is currently in its barebones stages.

#### Examples of Usage
-
Multi-threaded Denial of Service (DOS) Stress-Testing:
```python
import hacklib

dos = hacklib.DOSer()
dos.launch('http://yourwebsite.com', duration=30, threads=50)
```
-
Port Scanning:
```python
from hacklib import *

ps = PortScanner()
ps.scan(getIP('yourwebsite.com'))
# By default scans the first 1024 ports with 1 second timeout. Use ps.scan(IP, port_range=n, timeout=i) to change default

# After a scan, open ports are saved within ps for reference
if ps.portOpen(80):
    # Establish a TCP stream and sends a message
    send(getIP('yourwebsite.com'), 80, message='GET HTTP/1.1 \r\n')
```
-
Universal Login for almost all HTTP/HTTPS form-based logins and HTTP Basic Authentication logins:

```python
import hacklib

ac = hacklib.AuthClient()
# AuthClient uses the mechanize module for form-based logins

# Attempts to login and return the HTML of the resulting page
# Returns False if resulting page has the same URL as the login page
# Returns False if login fails using HTTP Basic Authentication
htmldata = ac.login('http://yourwebsite.com/login', 'username', 'password')

# For form-based logins, returns HTML whether login works or not.
if 'incorrect' not in htmldata:
    print 'Login Success'
```
