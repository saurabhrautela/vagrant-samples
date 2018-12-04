# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

Vagrant.configure("2") do |config|

    # Configuration for a VM
    # Copy and modify to create multiple VMs
    config.vm.define "app" do |app|
        # Look for boxes at: https://app.vagrantup.com/boxes/search
        app.vm.box = "ubuntu/bionic64"
        app.vm.hostname = "app"

        # Network settings
        app.vm.network "private_network", ip: "192.168.33.30"
        app.vm.network "forwarded_port", guest: 8000, host: 3800
        app.vm.network "forwarded_port", guest: 443, host: 3443
        app.vm.network "forwarded_port", guest: 80, host: 3080

        # Folder setting
        app.vm.synced_folder "./shared", "/shared", create: true, owner: 'vagrant', group: 'vagrant', mount_options: ['dmode=750', 'fmode=640']

        # Provider settings
        app.vm.provider "virtualbox" do |vb|
            vb.name = 'app'
            vb.memory = 1024
        end
    end

    config.vm.provider "virtualbox" do |vb|
        vb.gui = false
        vb.cpus = 2
        vb.memory = 2048
    end

    $script = <<-SHELL
    # Install docker on Ubuntu
    apt-get update
    apt-get upgrade
    apt-get install -y apt-transport-https ca-certificates curl software-properties-common
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    apt-get update
    apt-get install -y docker-ce
    base=https://github.com/docker/machine/releases/download/v0.16.0 && curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine && sudo install /tmp/docker-machine /usr/local/bin/docker-machine
    curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    chmod u+x /usr/local/bin/docker-compose
    usermod -a -G docker vagrant
    SHELL

    config.vm.provision "shell", inline: $script

    # To execute a shell script
    #config.vm.provision "shell", path: "bootstrap.sh"
end
