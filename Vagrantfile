# -*- mode: ruby -*-
# vi: set ft=ruby :
# test

Vagrant.configure(2) do |config|
    config.vm.box = "precise64"
    config.vm.box_url = "http://files.vagrantup.com/precise64.box"

    config.vm.network "forwarded_port", guest: 80, host: 8080
    config.vm.network "forwarded_port", guest: 8888, host: 8888
    config.vm.network "private_network", ip: "192.168.50.4"

    # config.vm.synced_folder "/Users/sbraznikov/Development", "/home/vagrant/Development", type: "rsync", rsync__exclude: ".git/"
    config.vm.synced_folder "/Users/sbraznikov/Development", "/home/vagrant/Development", type: "nfs"

    config.vm.provision :shell, :inline => "echo \"Europe/Berlin\" | sudo tee /etc/timezone && dpkg-reconfigure --frontend noninteractive tzdata"

    config.vm.provision :ansible do |ansible|
        ansible.playbook = "vagrant.yml"
    end
end
