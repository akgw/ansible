# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "backend" do |u|
    u.vm.box = "ubuntu/trusty64"
    u.vm.network :private_network, ip: "192.168.3.10"
    u.vm.hostname = "backend.co.jp"
    u.vm.synced_folder "../Backend", "/home/vagrant/Backend", mount_options:['dmode=777','fmode=755']

    config.vm.provision "ansible" do |ansible|
       ansible.playbook = "provisioning/backend.yml"
       ansible.inventory_path = "provisioning/hosts/local/backend"
       ansible.limit = 'all'
    end
  end

  config.vm.define "frontend" do |u|
    u.vm.box = "ubuntu/trusty64"
    u.vm.network :private_network, ip: "192.168.3.11"
    u.vm.hostname = "frontend.co.jp"
    u.vm.synced_folder "../Frontend", "/home/vagrant/Frontend", mount_options:['dmode=777','fmode=777']
    
    config.vm.provision "ansible" do |ansible|
       ansible.playbook = "provisioning/frontend.yml"
       ansible.inventory_path = "provisioning/hosts/local/frontend"
       ansible.limit = 'all'
    end
  end

  config.vm.define "db_master" do |u|
    u.vm.box = "ubuntu/trusty64"
    u.vm.network :private_network, ip: "192.168.3.20"
    u.vm.hostname = "db-master.co.jp"

    config.vm.provision "ansible" do |ansible|
       ansible.playbook = "provisioning/db_master.yml"
       ansible.inventory_path = "provisioning/hosts/local/db_master"
       ansible.limit = 'all'
    end
  end

end
