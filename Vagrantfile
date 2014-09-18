# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "hashicorp/precise64"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.ssh.forward_agent = true

  config.vm.provision :shell, path: "bootstrap.sh"
  
  config.vm.synced_folder "./public", "/vagrant", id: "vagrant-root",
    owner: "www-data",
    group: "www-data",
    mount_options: ["dmode=2775,fmode=0664"]
    
  config.vm.provider :virtualbox do |vb, override|
    vb.gui = false
    vb.customize ['modifyvm', :id, '--memory', '1024']
    vb.customize ['modifyvm', :id, '--cpus', '4']
  end
end
