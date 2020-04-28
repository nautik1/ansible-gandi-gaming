Ansible-Teeworlds
=================

This role helps installing a Teeworlds server.

Requirements
------------

Any debian-based linux using systemd should work, preferably Ubuntu 18.04.

Tested with:
- Teeworlds 0.7.5
- Ansible 2.9.7
- Ubuntu 18.04 on [Gandi Cloud](https://www.gandi.net/fr/cloud)

How to use
--------------

- Create your server with any debian-based system. On Gandi, as simple as:
  ```
  gandi vm create --datacenter="FR-SD5" --memory=1024 --cores=1 --sshkey ~/.ssh/id_rsa.pub --size="10G" --ip-version=4 --login="my-login" --hostname="my-teeworld-serv" --password --image="Ubuntu 18.04 LTS"
  gandi vm show teeworld-serv
  ```
- `git clone https://github.com/nautik1/ansible-teeworlds.git`
- `cp hosts.yml.example hosts.yml`
- Edit `hosts.yml` with the IP or hostname of your server, the Teeworlds version to download (check the latest available at https://downloads.teeworlds.com/) and any other configuration for your Teeworlds server
- `ansible-playbook -i hosts.yml install.yml`

You're all set ! Get the client on your laptop and join `<your-server-ip-or-hostname>:8303`.

/!\ Be careful to install the same Teeworlds version on your computer as the one running on your server, or you might not be able to join !

Dependencies
------------

No external role used; Teeworlds server downloaded from https://downloads.teeworlds.com

License
-------

[WTFPL](https://en.wikipedia.org/wiki/WTFPL)
