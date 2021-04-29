# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2004"
  config.vm.synced_folder "./", "/var/www/site", owner: "www-data", group: "www-data"
  config.vm.network "private_network", ip: "192.168.33.60"

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "vvv"
    ansible.inventory_path = "hosts"
    ansible.playbook = "provision-local.yml"
    ansible.limit = 'all'
  end
end
