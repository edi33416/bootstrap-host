# bootstrap-host

Ansible scripts to bootstrap a fresh host machine

## Prerequisites

You must have Ansible [installed](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) on your machine.

If you're lazy, like me, and using Ubuntu, this is what you have to do to install it [on Ubuntu](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-ubuntu).

```bash
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```

## Usage

Start the bootstrapping process by running
```bash
$ ansible-playbook playbook/bootstrap.yml
```

The playbook makes use of the [become](https://docs.ansible.com/ansible/latest/user_guide/become.html) keyword to execute tasks with root privileges when installing packages. The tasks assume your user is in `sudoers` and it can run the `sudo` command passwordless. If you need to type your password, start the bootstrapping process by running
```bash
$ ansible-playbook playbook/bootstrap.yml --ask-become-pass
```

The `--ask-become-pass` argument is used so you won't write your password in plaintext in the playbook.
You should never keep your password in plaintext.

## What you'll get

- [First](playbook/helper-pkgs.yml) it will perform an update and autoclean on your system (:warning: take care if the system isn't a fresh install).
- Basic [dev tools](playbook/dev-tools.yml): `build-essential`, `git`, `tmux`, `valgrind`, etc.
- D Language [toolkit](playbook/dlang.yml): `ldc2`, `dub`, etc.
- Vim as in [ide](playbook/ide.yml): this will also clone [my vimrc](https://github.com/edi33416/vim) and install the plugins
- [Zsh](playbook/zsh.yml) with oh-my-zsh: I'm not trying to force `zsh` on anyone; I just like it.

Feel free to clone, fork and hack to meet your needs. PRs are welcomed.

## Compatibility

This was tested only on Ubuntu.
