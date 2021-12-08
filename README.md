# Ansible playbook to install and configure cloudamize in linux and windows machine

The playbook consits of roles to intall cloudamize in linux (Debian, RedHat) and windows machine. The task for linux are inside roles/linux/tasks/main.yml and for windows are inside roles/windows/tasks/main.yml


## Note
* Please installed ansible in your host machine. 
* Update your Linux and Windows IP and credentials in inventory/hosts
* If you've copied the public key of ansile server to the remote host and use it to connect via ssh to the remote host, you can only put the name and ansible_host in inventory/hosts.


## Linux task

* At first step the playbook downloads cloudamize installation file in the remote machine
* It makes the downloaded file executable
* It runs the installation file with environment variable. To run installation, run the following command
```
ansible-playbook -i inventory/hosts master.yml --extra-vars "role_name=linux run_option=install";
```
* It also runs uninstallation. To run uninstallation, run the following command
```
ansible-playbook -i inventory/hosts master.yml --extra-vars "role_name=linux run_option=uninstall";
```


## Windows task

* At first step, the playbook downloads the installation file in the remote machine
* It runs the installation file with the environment variable. Run the following command to install cloudamize in Windows.
```
ansible-playbook -i inventory/hosts master.yml --extra-vars "role_name=window run_option=install";
```
* It also runs uninstallation. Run the following command to uninstall cloudamize in Windows.
```
ansible-playbook -i inventory/hosts master.yml --extra-vars "role_name=windows run_option=uninstall";
```

## Vars

* become_user_linux denotes which the user of the remote machine
* linux_cloudamize_download_url denotes the url to download the cloudamize installation file
* linux_cloudamize_download_destination denotes the destination where the file will be downloaded in the remote machine
* env_vars denotes the environment variables. CLOUDAMIZE_CUSTOMER_KEY is used inside it.

* windows_cloudamize_download_url denotes the url to download the cloudamize installation file in machine
* windows_cloudamize_download_destination denotes the destination for the downloaded file.
* install_cloudamize_in_windows denotes the command to run the downloaded file in windows to install cloudmize. You can replace the customerkey with yours


## Inventory

* You can edit the inventory file in inventory/hosts
