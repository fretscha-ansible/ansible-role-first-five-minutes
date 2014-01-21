First Five Minutes (ffm)
========

Bryan Kennedy's blog post [My First 5 Minutes On A Server; Or, Essential Security for Linux Servers][1] inspired me to write this role for ansible.

The goal of this role is an basic initial setup with little security tweaks.

Requirements
------------

This role requires Ansible 1.4 or higher.

It has successfully been tested on following Digital Ocean images
* Ubuntu 12.04 (Precise Pangolin)
* Ubuntu 12.10 (Quantal Quetzal)
* Ubuntu 13.04 (Raring Ringtail)
* Ubuntu 13.10 (Saucy Salamander)

Accelarated mod is disabled by default. Enabling the accelerated mode requires the `python-keyczar`package installed.


Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

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
