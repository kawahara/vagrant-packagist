# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "quantal64"
  config.vm.network :private_network, ip: "192.168.33.10"
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  #config.vm.synced_folder "work/", "/home/vagrant/work", :owner => "vagrant", :group => "www-data", :extra => "dmode=2775,fmode=2664"

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "./cookbooks"
    chef.add_recipe "packagist_cookbook"
    chef.json.merge!(JSON.parse(File.read("./chef.json")))
  end
end
