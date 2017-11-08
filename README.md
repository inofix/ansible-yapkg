[![Travis CI](https://img.shields.io/travis/inofix/ansible-yapkg.svg?style=flat)](http://travis-ci.org/inofix/ansible-yapkg)


YAPKG
=====

This is Yet-Another-PacKaGe-installer role for ansible.

Why we do not use one of the existing roles?

* For the first reason read the section "Promise" below. We need something reliable.
* This role will be used by [maestro](https://github.com/inofix/maestro) and must follow the logic used there. (Of course, the role can be used without maestro..)

A note on the only mandatory variable: You need to tell what packages you want to get installed.
The variable is 'yapkg\_\_names' and takes a list of package names.


State
-----

UNSTABLE! We are just migrating from zwischenloesung.yapkg.


Promise
-------

Sure this role may change in the future, but we will only expand features to not break backwards compatibility.

If radical changes should become necessary, a new role will be created, probably with an 'ng' or version suffix...


Idea
----

In the inventory you can group the hosts based on certain applications and distros. The playbook will have to map the hosts in the groups to the actual name of the package to be installed and pass it on to this role. The role will then install the package(s).


Installation
------------

 # ansible-galaxy install inofix.yapkg

Requirements
------------

* Ansible >2.0

Role Variables
--------------

* yapkg\_\_names - mandatory, string or array of strings with packages to install, no default
* yapkg\_\_update\_cache - optional, boolean, default=yes
* yapkg\_\_cache\_valid\_time - optional, number of seconds, default=3600
* yapkg\_\_task\_group\_name - optional, string name for the group of packages to be installed, default='packages'

Dependencies
------------

* Currently only "Debian" is supported
* It will test for the OS/Distro, namely
 * 'ansible\_os\_family'
* playbook must provide a list (array) of packages to be installed ('yapkg\_\_names')

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: inofix.yapkg, yapkg__names: [ foo, bar ] }

License
-------

GPLv3

Author Information
------------------

* Michael Lustenberger at [inofix.ch](http://www.inofix.ch)
