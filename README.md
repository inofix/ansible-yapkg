YAPKG
=====

This is Yet-Another-PacKaGe-installer role for ansible.

Why we do not use one of the existing roles?

* For the first reason read the section "Promise" below. We need something reliable.
* This role will be used by [maestro](https://github.com/inofix/maestro) and must follow the logic used there. (Of course, the role can be used without maestro..)

A note on the only mandatory variable: You need to tell what packages you want to get installed.
The main variable is 'yapkg\_names' and takes a list of package names. As they might be called different
on different distributions, you can distinguish between the targets as follows. Currently supported are:
'yapkg\_deb\_names' (Debian).

State
-----

UNSTABLE! We are just migrating from zwischenloesung.yapkg.


Promise
-------

Sure this role may change in the future, but we will only expand features to not break backwards compatibility.

If radical changes should become necessary, a new role will be created, probably with an 'ng' or version suffix...


Installation
------------

 # ansible-galaxy install inofix.ansible-yapkg

Requirements
------------

* Ansible >2.0

Role Variables
--------------

* yapkg\_names - mandatory, array
 * yapkg\_deb\_names - alternative for packages unique to debian, used as soon as other targets will be supported
* yapkg\_update\_cache - optional, default=yes
* yapkg\_cache\_valid\_time - optional, default=3600
* yapkg\_group\_name - optional, default='packages'

Dependencies
------------

* Currently only "Debian" is supported
* It will test for the OS/Distro, namely
 * 'ansible\_os\_family'
* playbook must provide a list (array) of packages to be installed ('yapkg\_names', or 'yapkg\_deb\_names')

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: inofix.ansible-yapkg, yapkg_names: [ foo, bar ] }

License
-------

GPLv3

Author Information
------------------

* Michael Lustenberger at [inofix.ch](http://www.inofix.ch)
