# Ansible playbooks for a mirror + backup server #

## Progetto Scuola [<img src="https://avatars1.githubusercontent.com/u/12886037?v=3&s=200" width="25" height="25" alt="BgLUG Logo" /> BgLUG][bglug] - Scenary 1 ##

Starting from a configured Debian 8 machine, this playbooks install some stuff
required to set up a mirror for Ubuntu, that keeps syncronized itself during
the night.

They also configure some exports for NFS to share the repository and a
`backups` folder for backups.

### Quick start ###

Start with a basic Debian 8 machine, with python, sudo and ssh server installed.
Then allow your user to use sudo without passwords:

    $ echo "${your_user} ALL = (ALL:ALL) NOPASSWD: ALL" >> /etc/sudoers.d/${your_user}

Then you may use these playbooks as follows:

    $ vim hosts # change IP address/hostname
    $ vim init.yml # change bglug with ${your_user}
    $ ansible-playbook init.yml --ask-pass -e "admin_sshkey=/path/to/id_rsa.pub"
    $ ansible-playbook setup.yml 

[bglug]: http://bglug.it/ "BgLUG Homepage"
