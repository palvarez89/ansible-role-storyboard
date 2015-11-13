To run
======


Install dependencies, this should be automatic if this ends up being
a role.

    ansible-galaxy install geerlingguy.apache,1.4.2 -p `pwd`/roles
    ansible-galaxy install Mayeu.RabbitMQ,1.4.0 -p `pwd`/roles
    ansible-galaxy install geerlingguy.mysql,1.5.0 -p `pwd`/roles

Tweak the vars.yml file and then run:

    ansible-playbook -i hosts instance-config.yml
