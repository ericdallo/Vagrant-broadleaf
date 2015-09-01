# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu"

  #Supervisor
  config.vm.define :monitor do |monitor_config|
    monitor_config.vm.network :private_network, :ip => "192.168.33.20"
  end

  # Database Virtual Machine
  config.vm.define :db do |db_config|
    db_config.vm.network :private_network, :ip => "192.168.33.21"
    db_config.vm.provision "puppet" do |puppet|
      puppet.manifest_file = "db.pp"      
    end
  end
  # Web Virtual Machine
  config.vm.define :web do |web_config|
    web_config.vm.network :private_network, :ip => "192.168.33.22"
    web_config.vm.provision "puppet" do |puppet|
      puppet.manifest_file = "web.pp"
    end
  end
end
