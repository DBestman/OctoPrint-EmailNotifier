OctoPrint-EmailNotifier
=======================

**UPDATE** *2020-Sep-30*: Version 0.2.0 updated **with python3 support**

-	Tested on OctoPrint `1.4.x`

For python2 support, see below for compatible `keyring` packages.

---

Recieve email notifications when OctoPrint jobs are STARTED, COMPLETED, FAILED or CANCELLED.

Forked from

-	`kotl/OctoPrint-EmailNotifier` which is forked from
	-	`ericli1018/OctoPrint-EmailNotifier` which is forked from
		-	`anov/OctoPrint-EmailNotifier`

![Settings tab and email screenshot](extras/emailnotifier.png)

Installation
------------

**IMPORTANT**: On python2-based versions of OctoPrint, including 1.3.x, before attempting to install this plugin, first install python2-compatible version of some modules:

```console
$ ~/oprint/bin/pip install keyring==18.0.1
$ ~/oprint/bin/pip install keyrings.alt==3.1.1
```

Install via the OctoPrint [Plugin Manager](https://github.com/foosel/OctoPrint/wiki/Plugin:-Plugin-Manager) or manually using this [archive URL](https://github.com/idcrook/OctoPrint-EmailNotifier/archive/python3.zip):

```
https://github.com/idcrook/OctoPrint-EmailNotifier/archive/python3.zip
```

Configuration
-------------

Your outgoing email account password is not stored with OctoPrint's settings. It is retrieved from your system [keyring](https://pypi.python.org/pypi/keyring#what-is-python-keyring-lib). Store your password from a Python prompt on your OctoPrint system using [`yagmail.register`](https://github.com/kootenpv/yagmail#username-and-password):

```
$ ~/oprint/bin/python
>>> import yagmail
>>> import keyring
>>> yagmail.register("SMTP username", "SMTP password")
```

For some accounts, your SMTP username may be your complete `username@domain.com` address.

To use yagmail (and thus OctoPrint-EmailNotifier) with Gmail, you may need to [allow less secure apps to access your account](https://support.google.com/accounts/answer/6010255?hl=en).

-	Server: `smtp.gmail.com`
-	Serverport: `587`
-	[X] Use TLS

Troubleshooting
---------------

If on Raspberry Pi, when you try to \[Send a test email\] and you encounter this error:

```
ImportError: libxslt.so.1: cannot open shared object file: No such file or directory
```

Install the system library:

```console
$ sudo apt install libxslt-dev
# on later systems, if that does not work # $ sudo apt install libxslt1-dev
```

Acknowledgements
----------------

Loosely based on [OctoPrint-Pushbullet](https://github.com/OctoPrint/OctoPrint-Pushbullet).

Uses [yagmail](https://github.com/kootenpv/yagmail) to send email.

License
-------

Licensed under the terms of the [AGPLv3](http://opensource.org/licenses/AGPL-3.0).
