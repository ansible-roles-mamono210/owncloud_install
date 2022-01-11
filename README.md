[![](https://github.com/ansible-roles-mamono210/owncloud_install/workflows/build/badge.svg)](https://github.com/ansible-roles-mamono210/owncloud_install/actions?query=workflow%3Abuild)

Role Description
=========

Installs [WordPress](https://owncloud.org) for CentOS7.

Requirements
------------

Before running this role, the following packages must be installed on the target system.

* Extra Packages for Enterprise Linux ([EPEL](https://docs.fedoraproject.org/en-US/epel/))
* [Remi's RPM repository](https://rpms.remirepo.net)
* [PHP](https://www.php.net)
* [Apache HTTP Server](https://httpd.apache.org)
* [WP-CLI](https://wp-cli.org)


Role Variables
--------------

```YAML
---
# Working directory
wp_install_work_dir: /tmp/wp-install

# WordPress installation settings parameters
# ----------------------------------------------------
wp_install_dir: owncloud
wp_install_path: "/var/www/html/{{ wp_install_dir }}"
wp_host: localhost
wp_url: "http://{{ wp_host }}/{{ wp_install_dir }}"
# ----------------------------------------------------

# WordPress database parameters
# ----------------------------------------------------
db_name: owncloud
db_user: owncloud
db_password: owncloud
db_host: db:3306
db_port: 3306
db_prefix: wp_
# ----------------------------------------------------

# WordPress site parameters
# ----------------------------------------------------
wp_title: test
wp_admin_user: test
wp_admin_password: test
wp_admin_email: mail@example.com

# .htaccess file name
httpd_conf_confd: owncloud.conf
# ----------------------------------------------------
```

Dependencies
------------

None

Example Playbook
----------------

```YAML
---
- hosts: all
  become: true
  roles:
    - role: geerlingguy.repo-epel
    - role: geerlingguy.repo-remi
    - role: mamono210.php
    - role: mamono210.wp_cli
    - role: owncloud_install
```

License
-------

BSD
