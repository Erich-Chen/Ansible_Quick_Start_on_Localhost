# Ansible_Quick_Start_on_Localhost

A very quick start to use Ansible on *localhost* (Debian-like).
It took me like 45 minutes to start from almost-zero knowledge of Ansible.

1. `sudo apt install ansible`

2. `mkdir ansible_test && cd ansible_test`

3. `vim hosts`

An example inventory with only localhost (127.0.0.1):

````
[sites]
127.0.0.1 ansible_connection=local
````

4. `vim playbook.yml`

An example to display system distribution (equivalent of `lsb_release`):

````
- hosts: 127.0.0.1
  become: yes 
  tasks:
    - name: Show System Distribution
      debug: msg="{{ ansible_distribution }}"
````

5. `ansible-playbook -i hosts playbook.yml --ask-become-pass`
