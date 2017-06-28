Ansible Role uWSGI
=========

Installs and configures uWSGI daemon.

This playbook highly values the KISS methodology - Keep It Simple Stupid.

- only takes care of uWSGI service installation and configuration -
  deployments would have to go in an extra play/role with a dep on this role.
- supports only a single uwsgi client - if you want to configure more clients, run this
  role multiple times while passing the corresponding facts.

Example Playbook
----------------

    - hosts: all
      vars:
        uwsgi_enabled: yes
        uwsgi_apps:
          - name: example_com
            options:
              socket: 127.0.0.1:3031
              chdir: /var/www/example_com
              virtualenv: venv
              python-path: ..
              module: example_com:application
              processes: 4
              threads: 2
              stats: 127.0.0.1:9191
              master: true
      roles:
         - blunix.role-uwsgi

License
-------

Apache

Author Information
------------------

Service and support for orchestrated hosting environments, continuous integration/deployment/delivery and various Linux and open-source technology stacks are available from:

```
Blunix GmbH - Professional Linux Service
Glogauer Straße 21
10999 Berlin - Germany

Web: www.blunix.org
Email: mailto:service@blunix.org
```
