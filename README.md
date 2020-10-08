# Lempo

Lempo is a configurable ansible role for setting up a LEMP (Linux, nginx, MariaDB, PHP) server. This role works with

* openSUSE Leap

## TODOs

* `default` pages does not work without manually setting `server_name` (`nginx.conf` contains default config)

## Post-Install steps

* MariaDB should be secured via `mysql_secure_installation`

## Role Variables
--------------

You can set the following variables to configure the role. Here listed are the variables and their default settings.

Include additional php modules for specific installations:

	mediawiki: false                    # Install additional php modules for MediaWiki
	nextcloud: false                    # Install additional php modules for NextCloud
	lychee: false                       # Install additional php modules for Lychee

Configure memcache (currently only [APCu](https://www.php.net/manual/en/book.apcu.php))

	apcu_enable: false                   # enable APCu memcache
	apcu_shm_size: "32M"                 # shared memory size

Firewall configuation, which is by default disabled

	config_firewall: false               # Enable firewall configuration
	firewall_zone: "public"              # Firewall zone to configure

Some custom `nginx` settings

	nginx_user: "nginx"                  # Default nginx user (for permission ecc.)
	nginx_group: "nginx"                 # Default nginx group (for permission ecc.)

Custom PHP settings

	php_memlimit: "128M"                 # Default PHP memory limit
	php_uploads: "On"                    # Enable uploads
	php_maxuploadsize: "256M"            # Max file upload size
	php_maxuploads: "20"                 # Max uploads per request
	php_socket: "/var/run/php-fpm.sock"  # Location of the php socket to be used
	php_chdir: "/srv/www"                # Location to change directory to

Custom (advanced) MariaDB settings

	innodb_config: false                 # Configure InnoDB
	innodb_cache_size: "256M"            # InnoDB cache size
	innodb_io_cap: "200"                 # IOPS for the background task
	innodb_no_double_write: false        # Disable double write (careful!!!)
	innodb_file_format: "Barracuda"      # Default file format


## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: lempo, config_firewall: true }

A bit more advanced example for the imaginary `jellyfish` test server

    - hosts: jellyfish
      roles:
         - role: lempo
           vars:
             setup_default_page: true
             default_page_hostname: "{{ansible_host}}"
             apcu_enable: true
             php_memlimit: "128M"
             apcu_shm_size: "32M"
             config_firewall: true
             firewall_zone: "public"
             innodb_config: true
             innodb_cache_size: "128M"

## License

MIT

## Author Information

phoenix