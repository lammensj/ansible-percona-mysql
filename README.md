# Percona-MySQL

Set up a [percona-server](https://www.percona.com/software/mysql-database/percona-server) server in Debian-like systems.

Requirements
------------

* `python-mysqldb` (auto-installed)

Role Variables
--------------

* `percona_mysql_version`: [default: `5.7`]: Version to install
* `percona_mysql_root_password`: [default: undefined]: Root password (**required**)
* `percona_mysql_databases`: [default: empty]: List of databases ([mysql_db](http://docs.ansible.com/ansible/mysql_db_module.html) list)
* `percona_mysql_users`: [default: empty]: List of users ([mysql_user](http://docs.ansible.com/ansible/mysql_user_module.html) list)
* `percona_mysql_config`: [default: empty]: Configuration dictionary (mysqld section of my.cnf)

Dependencies
------------

None

Example Playbook
----------------
    - hosts: servers
      vars:
        percona_mysql_root_password: mysql_root_pass
        percona_mysql_databases:
          - { name: database1 }
        percona_mysql_users:
          - { name: user1, password: sapun, priv: "database1.*:ALL" }
        percona_mysql_config:
          bind-address: "0.0.0.0"
          performance_schema: "off"
      roles:
         - lammensj.percona-mysql

License
-------

MIT
