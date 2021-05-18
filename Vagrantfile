# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # To refresh settings below, use `vagrant reload`
  config.vm.box = "ubuntu/focal64"
  config.vm.hostname = "wordpress-local-ubuntu2004"
  config.vm.network "private_network", ip: "192.168.33.60"
  config.vm.synced_folder "./web", "/home/vagrant/web/wpdev.test", create: true
  config.vm.synced_folder "./logs", "/home/vagrant/logs", create: true

  # To refresh settings below, use `vagrant provision`
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.inventory_path = "ansible/hosts"
    ansible.playbook = "ansible/provision-local.yml"
    ansible.limit = 'all'
    #ansible.config_file = "ansible/ansible.cfg"
    ansible.vault_password_file = "ansible/.vault_password"
    #ansible.tags = "debug"
  end
end
