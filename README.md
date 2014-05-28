First Five Minutes
========

Bryan Kennedy's blog post [My First 5 Minutes On A Server; Or, Essential Security for Linux Servers][1] inspired me to write this role for ansible.

The goal of this role is a basic initial setup with minor security tweaks.

Requirements
------------

This role requires Ansible 1.6 or higher.

It has successfully been tested on following Digital Ocean images
* Ubuntu 14.04 (trusty tahr)
 

Accelarated mode is disabled by default. Enabling the accelerated mode requires the `python-keyczar`package installed.


Role Variables
--------------

Take a look at the roles/first_five_minutes/defaults/main.yml to see in detail how defaults are set.
You shall override all defaults in the host_vars or/and group_vars.

* `ffm_root_password`:
  - Description: root_password hash for console login as root.
  - Default: `$6$flk7B1CUbp$ymzXEZ.TRlPWmJaDLI1Y4T56uzTl1N0.QSTS1pfkCDd6LLY3QzyyKVTU3ayVYV5pQgutIeFwSWQRQzsJzGmzR0`

* `ffm_deploy_user`:
  - Description: deploy user which will be used for ansible to deploy. Has sudo rights without password.
  - Default: `default`

* `ffm_deploy_password`:
  - Description: password hash for login as deploy.
  - Default: `$6$RUwI5ZvxW8U$Iq1e1JpZbOIKjpWKM9FZGVvsZyDCJa.cHVLD3wRcTbLFL6LmA9oBZzz5NXDrNEIPKUu.Jl.CfngwY528mHOay1` equivalent of `test`

* `ffm_postfix_mode`:
  - Description: Type of postfix configuration.
  - Values: `internet | smarthost`
  - Default: `smarthost`

* `ffm_fqdn_hostname`:
  - Description: Hostname,  fully qualified domain name.
  - Default: `server.acme.tld`

* `ffm_fqdn_smtp_relay`:
  - Description: postfix smarthost only needed if `ffm_postfix_mode` equals 'smarthost'.
  - Default: `relay.acme.tld`

* `ffm_logwatch_email`:
  - Description: Email address. Where to send `logwatch` notification.
  - Default: ` monitor@acme.tld`


To create a password hash from your plaintext_password run the following line in linux python console (does not work on osx) :
```python
    python -c "import crypt, getpass, random, string; \
    print crypt.crypt(getpass.getpass(), '\$6\$%s\$' % \"\".join(random.sample(string.letters+string.digits, 8)))"
```

Dependencies
------------

no dependencies

License
-------
The MIT License (MIT)

Copyright (c) 2013-14 Frederic Tschannen

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

Todo's
-----
 * test on Debian 7.0 (wheezy) -> bootstrap with python, aptitude, etc.


Author Information
------------------




  [1]: http://plusbryan.com/my-first-5-minutes-on-a-server-or-essential-security-for-linux-servers
