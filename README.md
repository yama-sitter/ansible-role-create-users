create-users
=========

Create new users for Linux.
It is also possible to delete them if desired.

Requirements
------------

- install Ansible
- public keys (optional)

When you place a public key that contains the user name in the **public_key** directory, you will be able to register any of the public key to the target user.

Example:

    create-users
    |- files/
        |- public_keys/
            |- dadayama.pem // a public_key that contains the user name.


Role Variables
--------------

 name                             | required | default        | comment
----------------------------------|----------|----------------|------------
 create\_users\_users             | yes      |                | Array of user settings.
 create\_users\_users[].name      | yes      |                | A name of user.
 create\_users\_users[].uid       | yes      |                | A uid of user.
 create\_users\_users[].password  | no       | !              | A password of user.
 create\_users\_users[].groups    | no       |                | Groups of user.<br>Describe in a comma-separated when you specify more than one.<br>**Example:**<br>`wheel,develop,upload`
 create\_users\_users[].comment   | no       | A name of user | A comment of user.
 create\_users\_users[].shell     | no       | /usr/bin/zsh   | Any command interpreter.
 create\_users\_users[].state     | no       | present        | Whether the account should exist or not.<br>If you specify the `absent`, and the same behavior as `usrdel -r`.

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers
      sudo: yes
      roles:
         - dadayama.create-users

License
-------

MIT

Author Information
------------------

[dadayama](https://github.com/dadayama)
