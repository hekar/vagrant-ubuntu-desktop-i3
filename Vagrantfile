# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "boxcutter/ubuntu1604"
  config.vm.box_check_update = false

  config.vm.define "vagrant-ubuntu-desktop-i3" do |host|
  end

  config.vm.provider "virtualbox" do |vb|
    vb.name = "vagrant-ubuntu-desktop-i3"
    vb.gui = true
    vb.cpus = 2
    vb.memory = "4096"

    vb.customize ['modifyvm', :id, '--clipboard', 'bidirectional']
    vb.customize ['modifyvm', :id, '--accelerate3d', 'on']
    vb.customize ['modifyvm', :id, '--vram', '64']
    vb.customize ['modifyvm', :id, '--cpus', '2']
    vb.customize ['modifyvm', :id, '--bioslogofadein', 'off']
    vb.customize ['modifyvm', :id, '--bioslogofadeout', 'off']
    vb.customize ['modifyvm', :id, '--bioslogodisplaytime', '1000']
  end

  config.vm.provision "file", source: "~/.ssh/known_hosts", destination: ".ssh/known_hosts"
  config.vm.provision "file", source: "~/.ssh/id_rsa", destination: ".ssh/id_rsa"

  config.vm.provision "shell", privileged:false, inline: <<-SHELL
    chmod og-rw .ssh/id_rsa
  SHELL

  config.vm.provision "shell", privileged:false, inline: <<-SHELL
    sudo apt update

    # dotfiles setup
    sh -c "$(curl -fsSL https://raw.github.com/hekar/dotfiles/master/setup.sh)"

    # nvm
    curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.1/install.sh | bash
    bash -c '. ~/.nvm/nvm.sh && nvm install 4 && nvm alias default 4'

    sudo apt install -y lightdm  
    sudo systemctl enable lightdm
    sudo systemctl reboot
  SHELL

end
