sleif.nextcloud_docker
============

This role runs a nextcloud instance on docker.

Requirements
------------

Use it on a machine setup with ansible role sleif.docker, sleif.redis_docker and sleif.mariadb_docker.

Role Variables
--------------

See defaults/main.yml for customination.

Dependencies
------------

- geerlingguy.docker to make sure Docker is available.
- sleif.docker to make sure Docker is configured as needed.
- sleif.redis_docker
- sleif.mariadb_docker

Example Playbook
----------------

    - hosts: "server"
      user: root
      vars:
        docker_network_name: 'custom_docker_network'
      roles:
        - { role: sleif.redis_docker, tags: "redis_docker" }
        - { role: sleif.mariadb_docker, tags: "mariadb_docker" }
        - { role: sleif.nextcloud_docker, tags: "nextcloud_docker",
                                                      nextcloud_version: "21",
                                                      mysql_user: "mysql_db_user",
                                                      mysql_password: "mysql_db_user_password",
                                                      mysql_database: "mariadb_nextcloud_database",
                                                      virtual_host: "cloud.example.com",
                                                      letsencrypt_email: "letsencrypt@example.com" }

License
-------

MIT

Author Information
------------------

Created in 2021 by Sebastian Berthold
