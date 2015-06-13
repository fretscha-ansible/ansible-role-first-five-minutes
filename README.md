First Five Minutes
========

[![Build Status](https://travis-ci.org/fretscha-ansible/ansible-role-first-five-minutes.svg?branch=master)](https://travis-ci.org/fretscha-ansible/ansible-role-first-five-minutes)

Bryan Kennedy's blog post [My First 5 Minutes On A Server; Or, Essential Security for Linux Servers][1] inspired me to write this role for ansible.

The goal of this role is a basic initial setup with minor security tweaks.

Requirements
------------

This role requires Ansible 1.6 or higher.

It has successfully been tested on following [Digital Ocean][2] images

* Ubuntu 14.04 (Trusty Tahr)

* Ubuntu 14.10 (Utopic Unicorn)

* Ubuntu 15.04 (Vivid Vervet)
  - needs the pre-installation of python -  by default only python 3 is installed on vivid, which is not supported by ansible <= 1.9.1 yet.

Older releases of Ubuntu (12.04 | 12.10 | 13.04 | 13.10) had been partially tested successfully.

Role Variables
--------------

Take a look at the roles/first_five_minutes/defaults/main.yml to see in detail how defaults are set.
You shall override all defaults in the host_vars or/and group_vars.

* `ffm_timzone`:
  - Description: system timezone
  - Default: `Etc/UTC`

* `ffm_upgrade`:
  - Description: upgrade policy: no, safe, full, dist
  - Default: `no`

* `ffm_root_password`:
  - Description: root_password hash for console login as root.
  - Default: `$6$flk7B1CUbp$ymzXEZ.TRlPWmJaDLI1Y4T56uzTl1N0.QSTS1pfkCDd6LLY3QzyyKVTU3ayVYV5pQgutIeFwSWQRQzsJzGmzR0`

* `ffm_deploy_user`:
  - Description: deploy user which will be used for ansible to deploy. Has sudo rights without password.
  - Default: `deploy`

* `ffm_deploy_group`:
  - Description: deploy group which will be used for ansible to deploy.
  - Default: `deploy`

* `ffm_deploy_password`:
  - Description: password hash for login as deploy.
  - Default: `$6$RUwI5ZvxW8U$Iq1e1JpZbOIKjpWKM9FZGVvsZyDCJa.cHVLD3wRcTbLFL6LmA9oBZzz5NXDrNEIPKUu.Jl.CfngwY528mHOay1` equivalent of `test`

* `ffm_postfix_mode`:
  - Description: type of postfix configuration.
  - Values: `internet | smarthost`
  - Default: `smarthost`

* `ffm_fqdn_hostname`:
  - Description: hostname, fully qualified domain name.
  - Default: `server.acme.tld`

* `ffm_fqdn_smtp_relay`:
  - Description: postfix smarthost only needed if `ffm_postfix_mode` equals 'smarthost'.
  - Default: `relay.acme.tld`

* `ffm_logwatch_email`:
  - Description: email address. Where to send `logwatch` notification.
  - Default: `monitor@acme.tld`

* `ffm_notify_login`:
  - Description: send a notification Email on each ssh `login`.
  - Default: `yes`

* `ffm_notify_login_email`:
  - Description: email address. Where to send `login` notification.
  - Default: `monitor@acme.tld`

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
 * simple ntp configuration


Author Information
------------------

Frederic Tschannen

[GitHub project page](https://github.com/fretscha-ansible/ansible-role-first-five-minutes)


  [1]: http://plusbryan.com/my-first-5-minutes-on-a-server-or-essential-security-for-linux-servers
  [2]: https://www.digitalocean.com/
