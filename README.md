# continuent-ansible

Configuring servers for Tungsten purposes using Ansible. For more information read our blog article [Automated server preparation using Ansible](#).

## Usage

1. Clone repository
    ```
    git clone https://github.com/continuent/continuent-ansible.git
    ```

2. Define [inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html) with hostnames or IP addresses of your hosts
    ```
    $ cat myhosts.txt

    my-centos-host  ansible_user=centos     ansible_ssh_private_key=~/.ssh/id_rsa_centos
    my-ubuntu-host  ansible_user=ubuntu     ansible_ssh_private_key=~/.ssh/id_rsa_ubuntu
    my-amazon-host  ansible_user=ec2-user   ansible_ssh_private_key=~/.ssh/id_rsa_amazon
    ```

3. Replace `roles/prerequsites/files/id_rsa.tungsten` and `roles/prerequsites/files/id_rsa.tungsten.pub` files with valid keys

4. Update `roles/prerequsites/files/tungsten.ini` file

5. Copy `{{ tungsten_version }}.tar.gz` into this directory (variable `tungsten_version` you will use in next step)

6. Run playbook
    ```
    ansible-playbook -i path/to/myhosts.txt -e "tungsten_version=tungsten-clustering-6.1.3-37" playbook.yml
    ```

    alternatively you can overwrite default passwords
    ```
    ansible-playbook -i path/to/myhosts.txt -e "tungsten_version=tungsten-clustering-6.1.3-37 passwd_mysql_tungsten=password passwd_mysql_root=Secret-4-root passwd_mysql_app_user=secret" playbook.yml
    ```

### Tested on following Linux distributions:
- Amazon Linux 2
- CentOS 7
- Debian GNU/Linux 10 (Buster)
- Ubuntu 18.04 (Bionic)
- SUSE Linux Enterprise Server 15
- RHEL 7
