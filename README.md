# bootstrap-host

Ansible scripts to bootstrap a fresh host machine

## Usage

Start the bootstrapping process by running
```bash
$ ansible-playbook playbook/bootstrap.yml
```

The playbook makes use of the [become][https://docs.ansible.com/ansible/latest/user_guide/become.html] keyword to execute tasks with root privileges when installing packages. The tasks assume your user is in `sudoers` and it can run the `sudo` command passwordless. If you need to type your password, start the bootstrapping process by running
```bash
$ ansible-playbook playbook/bootstrap.yml --ask-become-pass
```

The `--ask-become-pass` argument is used so you won't write your password in plaintext in the playbook.
You should never keep your password in plaintext.

## Compatibility

This was tested only on Ubuntu.
