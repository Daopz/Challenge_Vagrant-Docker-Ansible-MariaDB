# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.provision "docker", run: "once"

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "provisioning/playbooks/databasemariadb.yml"
    ansible.extra_vars = {
        db_name: ENV['DB_NAME'],
        db_username: ENV['DB_USERNAME'],
        db_password: ENV['DB_PASSWORD'],
        db_root_password: ENV['DB_ROOT_PASSWORD'],
        docker_network: ENV['DOCKER_NETWORK'],
        docker_mariadb_image: ENV['MARIADB_IMAGE']
    }
  end
end
