# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

  config.vm.network "forwarded_port", guest: 80, host: 80

  # Use rsync to keep files on the host continually updated in the VM
  # This is required for live reload to work correctly
  config.vm.synced_folder ".", "/vagrant", type: "rsync", rsync__exclude: ".git/", rsync__args: ["--verbose", "--archive", "-z", "--copy-links"]

  # Enable X11 forwarding
  config.ssh.forward_agent = true
  config.ssh.forward_x11 = true

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
  end

  config.vm.provision "shell", inline: <<-SHELL
    #### Install Android SDK - this section heavily borrowed from
    #### https://github.com/driftyco/ionic-box/blob/master/bootstrap.sh
    apt-get update
    apt-get install -y npm git
    npm install -g n
    n stable
  SHELL

end