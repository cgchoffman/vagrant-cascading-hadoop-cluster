# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "puppetlabs/ubuntu-16.04-64-puppet"
  config.vm.box_version = "1.0.0"

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--cpus", "1", "--memory", "1024"]
  end

  config.vm.provider "vmware_fusion" do |v, override|
      override.vm.box_url = "http://files.vagrantup.com/precise64_vmware.box"
      v.vmx["memsize"] = "1024"
      v.vmx["numvcpus"] = "1"
  end

  config.vm.define :hadoop1 do |hadoop1|
    hadoop1.vm.network "private_network", ip: "192.168.7.12"
    hadoop1.vm.hostname = "hadoop1.local"

    hadoop1.vm.provision :puppet do |puppet|
      puppet.manifest_file = "datanode.pp"
      puppet.module_path = "modules"
    end
  end

  config.vm.define :hadoop2 do |hadoop2|
    hadoop2.vm.network "private_network", ip: "192.168.7.13"
    hadoop2.vm.hostname = "hadoop2.local"

    hadoop2.vm.provision :puppet do |puppet|
      puppet.manifest_file = "datanode.pp"
      puppet.module_path = "modules"
    end
  end

  config.vm.define :hadoop3 do |hadoop3|
    hadoop3.vm.network "private_network", ip: "192.168.7.14"
    hadoop3.vm.hostname = "hadoop3.local"

    hadoop3.vm.provision :puppet do |puppet|
      puppet.manifest_file = "datanode.pp"
      puppet.module_path = "modules"
    end
  end

  config.vm.define :master, primary: true do |master|
    master.vm.network "private_network", ip: "192.168.7.10"
    master.vm.hostname = "master.local"

    master.vm.provision :puppet do |puppet|
      puppet.manifest_file = "master.pp"
      puppet.module_path = "modules"
    end
  end
end
