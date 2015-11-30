StoryBoard Ansible Role
=======================

[![Build Status](https://travis-ci.org/palvarez89/ansible-role-storyboard.svg?branch=master)](https://travis-ci.org/palvarez89/ansible-role-storyboard) [![Ansible Galaxy](https://img.shields.io/badge/role-palvarez89.storyboard-blue.svg)](https://galaxy.ansible.com/detail#/role/6187)

Installs and configures StoryBoard.


Requirements
------------

None.


Role Variables
--------------

Available variables are listed below, along with default values (see
`defaults/main.yml`):

    storyboard_src_root_api: /opt/storyboard
    storyboard_src_root_webclient: /opt/storyboard-webclient

Locations where StoryBoard is going to be cloned (using git) to be installed
later.

    storyboard_install_root: /var/lib/storyboard
    storyboard_www_root: "{{ storyboard_install_root }}/www"
    storyboard_working_root: "{{ storyboard_install_root }}/spool"

Locations where StoryBoard is going to be installed.

    storyboard_fqdn: 192.168.77.60.xip.io

FQDN used for StoryBoard VirtualHost configuration for Apache.

    storyboard_enable_notifications: 'True'
    storyboard_openid_url: https://login.launchpad.net/+openid
    storyboard_authorization_code_ttl: 300
    storyboard_access_token_ttl: 3600
    storyboard_refresh_token_ttl: 604800
    storyboard_valid_oauth_clients:
    - "{{ ansible_hostname }}"
    - "{{ storyboard_fqdn }}"

    storyboard_mysql_host: localhost
    storyboard_mysql_port: 3306
    storyboard_mysql_database: storyboard
    storyboard_mysql_user: storyboard
    storyboard_mysql_user_password: storyboard

    storyboard_rabbitmq_host: localhost
    storyboard_rabbitmq_port: 5672
    storyboard_rabbitmq_vhost: '/'
    storyboard_rabbitmq_user: storyboard
    storyboard_rabbitmq_user_password: storyboard

    storyboard_enable_token_cleanup: 'True'
    storyboard_enable_scheduler: 'True'
    storyboard_enable_cron: 'False'

Some configuration parameters used in `/etc/storyboard/storyboard.conf`. See
`templates/storyboard.conf.j2` for more information.

    storyboard_server_admin: ''

Email of the Server Admin for Apache configuration.

    storyboard_ssl_cert: ''
    storyboard_ssl_key: ''
    storyboard_resolved_ssl_ca: ''

SSL certificate files to configure StoryBoard with `https`.

    storyboard_worker_count: 5
    storyboard_use_upstart: false

Number of workers and boolean to use Upstart or SysV.

    storyboard_cors_allowed_origins_string: ''
    storyboard_cors_max_age: 3600

CORS configuration.

    apache_vhosts_version: -

Apache vhosts version, read from `geerlingguy.apache` role.


Dependencies
------------

This role depends on `geerlingguy.apache` role. Storyboard needs a web server
to run and Apache looks like a good choice.


Example Playbook
----------------

    - hosts: sb_server
      vars_files:
        - vars/main.yml
      roles:
        - { role: palvarez89.storyboard }

In `vars/main.yml` you can set some variables that you want to change from the
defaults.


Full installation on Ubuntu Trusty
----------------------------------

Install the roles needed. Note: `RabbitMQ` and `mysql` doesn't need to be
installed if the services are already present.

    mkdir -p roles
    ansible-galaxy install palvarez89.storyboard -p `pwd`/roles
    ansible-galaxy install Mayeu.RabbitMQ,1.4.0 -p `pwd`/roles
    ansible-galaxy install geerlingguy.mysql,1.5.0 -p `pwd`/roles

Tweak the vars.yml file and then run:

    ansible-playbook -i hosts instance-config.yml

Or simply run:

    vagrant up


License
-------

GPLv2


Author Information
------------------

This role was created in 2015 by [Pedro Alvarez Piedehierro](http://pedro.alvarezpiedehierro.com/).
