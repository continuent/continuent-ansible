# continuent-ansible

Configuring servers for Tungsten purposes using Ansible. For more informations read our blog article [Automated server preparation using Ansible](#).

## Usage

1. Clone repository
    ```
    git clone https://github.com/continuent/continuent-ansible.git
    ```

2. Define [inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html) with hostnames or IP addresses of your hosts
    ```
    # file myhosts.txt

    host1
    host2

    52.90.35.76

    192.0.2.51

    ```

3. Copy tungsten-clustering.tar.gz into this directory

4. Update variables in `vars/tungsten_vars.yml`
    - `ansible_user` - remote user used for configuration
    - `ansible_linux_distribution` - remote machines Linux distribution
    - `ansible_tungsten_version` - basename of tarball from previous step
    - passwords for MySQL users

5. Update `roles/prerequsites/files/tungsten.ini` file

6. Run playbook
    ```
    ansible-playbook -i path/to/myhosts.txt playbook.yml
    ```

### Linux distributions you can use:
- **amazon-linux** - based on Amazon Linux 2
- **centos** - based on CentOS 7
- **debian** - based on Debian GNU/Linux 10 (Buster)
- **ubuntu** - based on Ubuntu 18.04 (Bionic)
- **suse** - based on SUSE Linux Enterprise Server 15
- **rhel** - based on RHEL 7
