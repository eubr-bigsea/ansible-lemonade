Ansible Role: Lemonade
=========

Installs and configures Lemonade's projects

Requirements
------------
This role requires root access.

Dependencies
------------
```
ansible-galaxy install geerlingguy.mysql geerlingguy.nginx geerlingguy.redis spitfast.rbenv
```

Role Variables
--------------
Variable are defined in [vars/main.yml](vars/mail.yml), they basicaly sets
repository location, branch and hosts for services like MySQL and Redis.

Which projects should be install are defined on its respective variables
```
citron: false
thorn: false
tahiti: false
stand: false
limonero: false
```

Example Playbook
----------------

An example is set on [lemonade.yml](lemonade.yml)

License
-------
BSD

Author Information
------------------
This role was created in 2016 by Guilherme Maluf Balzana, part of [EUBra-BIGSEA
Project](http://www.eubra-bigsea.eu/)
