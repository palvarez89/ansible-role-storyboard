StoryBoard Ansible Role
=======================

[![Build Status](https://travis-ci.org/palvarez89/ansible-role-storyboard.svg?branch=master)](https://travis-ci.org/palvarez89/ansible-role-storyboard)

Installs and configures StoryBoard.

Requirements
------------

None.

Role Variables
--------------

A description of the settable variables for this role should go here, including
any variables that are in defaults/main.yml, vars/main.yml, and any variables
that can/should be set via parameters to the role. Any variables that are read
from other roles and/or the global scope (ie. hostvars, group vars, etc.)
should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in
regards to parameters that may need to be set for other roles, or variables
that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a
website (HTML is not allowed).


To run
------


Install the roles needed

    mkdir -p roles
    ansible-galaxy install palvarez89.storyboard -p `pwd`/roles
    ansible-galaxy install Mayeu.RabbitMQ,1.4.0 -p `pwd`/roles
    ansible-galaxy install geerlingguy.mysql,1.5.0 -p `pwd`/roles

Tweak the vars.yml file and then run:

    ansible-playbook -i hosts instance-config.yml

Or simply run:

    vagrant up
