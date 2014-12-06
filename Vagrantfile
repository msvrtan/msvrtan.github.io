# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "trusty32-20141024"
  config.vm.box_url = "http://dwnl.nulldevelopment.hr/boxes/trusty32-20141024.box"
    
  config.vm.network "private_network", ip: "10.1.40.80"
     
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", 1024]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
    v.customize ["modifyvm", :id, "--cpus", "2"]
    #v.gui = true
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "etc/provisioning/setup.yml"
    ansible.inventory_path = "etc/provisioning/hosts"
    ansible.verbose = true
    ansible.limit = 'all'
  end
end
