# Install Checkmk test environment

## Server Env with Vagrant

Vagrant is a mighty tool to spawn instantly server and container environment for a bunch of Providers
To use more Features please check https://www.vagrantup.com/docs/

### Create Environment
execute from folder

```
vagrant up
```
### Destroy Environment
execute from folder

```
vagrant destroy
```

## Inventory

You can adjust Inventory regarding IPs and Server and Client version
You can change or add some Variables

## install Checkmk on server
```
ansible-playbook -i Ansible/inventory.yml install_checkmk_server.yml
```
## install Checkmk on client
```
ansible-playbook -i Ansible/inventory.yml install_checkmk_client.yml
```
## uninstall Checkmk server
```
ansible-playbook -i Ansible/inventory.yml remove_checkmk_server.yml
```
## update Checkmk

Change checkmk_server_download and checkmk_client_download in inventory file

execute 

```
ansible-playbook -i Ansible/inventory.yml Ansible/update_checkmk_server.yml
ansible-playbook -i Ansible/inventory.yml install_checkmk_server.yml
ansible-playbook -i Ansible/inventory.yml install_checkmk_client.yml
```

Now the environment is updated
