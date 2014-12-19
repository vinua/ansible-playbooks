Ansible Playbooks
=================

[Ansible Documentation][1]

[1]: http://docs.ansible.com/index.html


Usage
-----

    $ git clone https://github.com/vinua/ansible-playbooks.git
    $ cd ansible-playbooks
    $ sudo pip install -r requirements.txt
    $ export DO_CLIENT_ID=XXX DO_API_KEY=XXX

You may want to update DigitalOcean's variables (regions, images, and sizes).

    $ python do_vars.py > group_vars/droplets.yml

Rename and edit `hosts.sample`, `apps.yml.sample`, and `domains.yml.sample`.

    $ ansible-playbook -i hosts site.yml
