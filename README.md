# LEMP Ansible

Repository contains a playbook for provisioning modern LEMP environment. Following is handled out of the box.

* User setup
* SSH setup
* Firewall setup

It will also install following software:

* Nginx with HTTP/2
* PHP 7
* MySQL (You can change it to MariaDB role under `provision.yml` file)
* Node.JS
* Git
* Fail2Ban

## Usage

Configure your hosts file:

```
[web]
<server or droplet ip>
```

Edit `var/all.yml` to configure your default user and [hashed](http://docs.ansible.com/ansible/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module) sudo password. This will create a new user on the provisioned servers that you can use to gain SSH access. You can also configure other relevant settings for nginx, mysql and server. For example if you want to install any extra packages you can add it under array like in server block:
```
server:
    install: '1'
    packages: [ fail2ban, git, vim, htop, acl, ufw , zip, unzip]
    timezone: UTC
```

##Note:

Make sure to have your generated ssh key under your droplet/instance in `~/.ssh/authorized_key`. In order to run setup smoothly. You can follow steps for generating key [here](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/). Every hosting has it's own configuration of adding ssh keys.

## Run:
`ansible-playbook --syntax-check provision.yml` To test if there is any error (If reconfigured)

`ansible-playbook provision.yml`

## Support/Contribution
Please feel free to give suggestion or report bug by [creating issue](https://github.com/CrowdLinker/ansible-lemp/issues).
