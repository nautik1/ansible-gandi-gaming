# Ansible-Gandi-Gaming

This playbook helps installing various fun games easily on Gandi Cloud

## Requirements

Any debian-based linux using systemd should work, preferably Ubuntu 20.04

Tested with:
- Ansible 2.9
- Ubuntu 20.04 on [Gandi Cloud](https://www.gandi.net/fr/cloud)

## How to use

- Create your game server(s) with any debian-based system. On Gandi, as simple as:
  ```
  gandi vm create --datacenter="FR-SD5" --memory=1024 --cores=1 --sshkey ~/.ssh/id_rsa.pub --size="10G" --ip-version=4 --login="my-login" --hostname="my-teeworld-serv" --password --image="Ubuntu 20.04 LTS"
  gandi vm show teeworld-serv
  ```
- Clone this repository
- Install game roles: `ansible-galaxy install -r requirements.yml`
- `cp hosts.yml.example hosts.yml`
- Edit `hosts.yml`:
  - Set the IP or hostname of your server in the wanted groups,
  - Add any other configuration you want for your game servers (see roles below)
- Run the whole playbook:
  ```
  ansible-playbook -i hosts.yml start-playing.yml
  ```
  Or install only specified games:
  ```
  ansible-playbook -i hosts.yml start-playing.yml --tags minetest
  ```

You're all set !

When you are done playing, just can just destroy your VMs (you can reinstall anyway):
```
gandi vm delete <your-vm-names>
```

## Installable games

### Teeworlds

Teeworlds is installed using [this pretty simple role](https://galaxy.ansible.com/nautik1/teeworlds)

Few notes:
- After install, join `<your-server-ip-or-hostname>:8303`
- Make sure to install the same Teeworlds version on your computer as the one running on your server, or you might
  not be able to join!

### Minetest

Minetest is installed using [this pretty simple role](https://galaxy.ansible.com/nautik1/minetest)

Few notes:
- After install, join `<your-server-ip-or-hostname>:30000`
- Install the client (preferably using minetest ppa): https://www.minetest.net/downloads/

### Xonotic

Xonotic is installed using [this pretty simple role](https://galaxy.ansible.com/nautik1/xonotic)

Few notes:
- After install, you can join `<your-server-ip-or-hostname>:26000`

### Supertuxkart

Supertuxkart is installed using [this pretty simple role](https://galaxy.ansible.com/nautik1/supertuxkart)

Few notes:
- This role takes quite a while to execute, as it builds from source
- After install, you can join `<your-server-ip-or-hostname>:2759`

License
-------

[WTFPL](https://en.wikipedia.org/wiki/WTFPL)
