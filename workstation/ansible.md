# Ansible Setup

## Requirements

```shell
# install ansible
sudo apt install ansible -y

# install ansible community plugins
ansible-galaxy collection install community.general
```

## Run the setup

```
ansible-playbook -i inventory.ini setup.yaml -K -u santhosh --ask-pass
```
