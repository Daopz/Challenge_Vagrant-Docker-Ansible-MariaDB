# Ansible Vagrant profile for Docker
## Background

This Vagrant profile provisions, build and manage a linux instance (Centos 7) with Docker then it uses Ansible to build and run a MariaDB container.

[Docker](https://www.docker.com/) is used to build and manage linux containers. [Ansible](http://www.ansible.com/) is useful in managing the Docker container lifecycle.

## Getting Started

Inside of this repository you can see a file is call `Vagrantfile` which tells Vagrant how to set up your virtual machine but you can run `vars_group_vars` shell file. This inits vagrant with some environment variables.

To use the vagrant file, you will need to have done the following:

  1. Download and Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
  2. Download and Install [Vagrant](https://www.vagrantup.com/downloads.html)
  3. Install [Ansible](http://docs.ansible.com/ansible/latest/intro_installation.html)
  4. Open a shell prompt (Terminal app on a Mac) and run `vars_group_vars` shell file.

  Once all of that is done, Vagrant provisions a Centos 7 instance, passes variables to Ansible, Ansible uses Docker module to fetch and start specified MariaDB version with the given credentials within the VM.

  On this proccess `databasemariadb` playbook starts `install-docker-py` and `init-database` roles files. 
  
  Then `init-db` role uses `docker_container` Ansible module to fire up a MariaDB instance.

  You can log in into the database and check the database running the following command: 
  
  mysql -u DB_USERNAME -p DB_PASSWORD DB_NAME

  The right values for DB_USERNAME, DB_USERNAME and DB_NAME is on the `vars_group_vars` shell file.


  ## Author Information

Created in 2019 by [David Oliveros](https://github.com/Daopz/)
