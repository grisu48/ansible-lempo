# Lempo

Lempo is a configurable ansible role for setting up a LEMP (Linux, nginx, MariaDB, PHP) server. This role works with

* openSUSE Leap

## TODOs

* `default` pages does not work without manually setting `server_name` (`nginx.conf` contains default config)

## Post-Install steps

* MariaDB should be secured via `mysql_secure_installation`


## Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: lempo }

## License

MIT

## Author Information

phoenix