# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # To refresh settings below, use `vagrant reload`
  config.vm.box = "generic/ubuntu2004"
  config.vm.network "private_network", ip: "192.168.33.60"
  config.vm.synced_folder "./web", "/home/vagrant/web", create: true
  config.vm.synced_folder "./logs", "/home/vagrant/logs", create: true

  # To refresh settings below, use `vagrant provision`
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.inventory_path = "hosts"
    ansible.playbook = "ansible/provision-local.yml"
    ansible.limit = 'all'
  end
end
