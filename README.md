# vagrant-ubuntu-desktop-i3

## Description

Graphical [Ubuntu 16.04](http://www.ubuntu.com/) environment [Vagrant](https://www.vagrantup.com/) with [i3wm](http://i3wm.org/) as window manager. Created with the intention of doing Linux development on Windows or OSX.

## Credentials
* Login: __vagrant__
* Password: __vagrant__

## Issues
* First login fails, you have to manually select i3 as the default desktop environment by clicking the Ubuntu icon above the password field.
* Zsh may not be the default shell. Use the command `chsh` and change the shell to `/bin/zsh`. This usually requires logging in and logging out. Use `i3-msg exit` to log out.

## Included Tools

* my [dotfiles](https://github.com/hekar/dotfiles)
* [i3](http://i3wm.org/)
* [lightdm](https://freedesktop.org/wiki/Software/LightDM/)
* [git](https://git-scm.com/)
  * Copies ~/.ssh/id_rsa from host
* [docker](https://www.docker.com/)
  * Includes [docker-compose](https://docs.docker.com/compose/)
* [nvm](https://github.com/creationix/nvm)
  * Defaults to latest node 4

## Requirements

- [VirtualBox](https://www.virtualbox.org/)
- [Vagrant](https://www.vagrantup.com/)

## Instructions

1. Clone the repo and `vagrant up`
1. (Optional) Highly recommend you install to get the latest guest additions: https://github.com/dotless-de/vagrant-vbguest
1. Wait for VM to start. VirtualBox Graphical Interface is enabled

## Extras

Get rid of VirtualBox menu and status bar:
```
VBoxManage setextradata global GUI/Customizations noMenuBar,noStatusBar
```

To re-enable:
```
VBoxManage setextradata global GUI/Customizations MenuBar,StatusBar
```

## License

[MIT](./LICENSE)
