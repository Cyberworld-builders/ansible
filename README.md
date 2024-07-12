# Ansible
A great place to learn Ansible as well as some useful playbooks to get started using it. Over time, it may grow into a place for more advanced and complex implementations.

## Getting Started

Certainly! Here's a guide to help you get started with Ansible:

1. Install Ansible:
   - On Ubuntu/Debian: `sudo apt update && sudo apt install ansible`
   - On macOS: `brew install ansible`
   - On Windows: Use Windows Subsystem for Linux (WSL) or run Ansible in a virtual machine

2. Understand key concepts:
   - Control Node: The machine where Ansible is installed
   - Managed Nodes: The servers you're managing with Ansible
   - Inventory: A list of managed nodes
   - Playbooks: YAML files describing the desired state of your systems
   - Modules: Units of code Ansible executes on managed nodes

3. Create an inventory file:
   ```
   [webservers]
   192.168.1.101
   192.168.1.102

   [databases]
   192.168.1.103
   ```

4. Write a simple playbook (e.g., `webserver.yml`):
   ```yaml
   ---
   - hosts: webservers
     become: yes
     tasks:
       - name: Install Apache
         apt:
           name: apache2
           state: present

       - name: Start Apache service
         service:
           name: apache2
           state: started
   ```

5. Run your playbook:
   ```
   ansible-playbook -i inventory webserver.yml
   ```

6. Learn about Ansible roles for organizing more complex playbooks

7. Explore Ansible Galaxy for community-contributed roles and collections

8. Practice with more complex tasks and playbooks

Would you like me to explain or elaborate on any of these steps?

### Issues with my Ansible Install
```sh
ansible --version
```

```
Traceback (most recent call last):
  File "/usr/bin/ansible", line 34, in <module>
    from ansible import context
ModuleNotFoundError: No module named 'ansible'
```

Tried installing with Conda
```sh
conda install ansible
```

That threw an error
```
Retrieving notices: ...working... done
Channels:
 - defaults
Platform: linux-64
Collecting package metadata (repodata.json): done
Solving environment: failed
PackagesNotFoundError: The following packages are not available from current channels:
  - ansible
Current channels:
  - defaults
To search for alternate channels that may provide the conda package you're
looking for, navigate to
    https://anaconda.org
and use the search bar at the top of the page.
```

Tried instead with pip
```sh
pip install ansible
```

Looks like it worked with pip
```
Collecting ansible
  Downloading ansible-10.1.0-py3-none-any.whl.metadata (8.2 kB)
Collecting ansible-core~=2.17.1 (from ansible)
  Downloading ansible_core-2.17.1-py3-none-any.whl.metadata (6.9 kB)
Collecting jinja2>=3.0.0 (from ansible-core~=2.17.1->ansible)
  Downloading jinja2-3.1.4-py3-none-any.whl.metadata (2.6 kB)
Collecting PyYAML>=5.1 (from ansible-core~=2.17.1->ansible)
  Downloading PyYAML-6.0.1-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (2.1 kB)
Collecting cryptography (from ansible-core~=2.17.1->ansible)
  Downloading cryptography-42.0.8-cp39-abi3-manylinux_2_28_x86_64.whl.metadata (5.3 kB)
Collecting packaging (from ansible-core~=2.17.1->ansible)
  Downloading packaging-24.1-py3-none-any.whl.metadata (3.2 kB)
Collecting resolvelib<1.1.0,>=0.5.3 (from ansible-core~=2.17.1->ansible)
  Downloading resolvelib-1.0.1-py2.py3-none-any.whl.metadata (4.0 kB)
Collecting MarkupSafe>=2.0 (from jinja2>=3.0.0->ansible-core~=2.17.1->ansible)
  Downloading MarkupSafe-2.1.5-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (3.0 kB)
Collecting cffi>=1.12 (from cryptography->ansible-core~=2.17.1->ansible)
  Using cached cffi-1.16.0-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (1.5 kB)
Collecting pycparser (from cffi>=1.12->cryptography->ansible-core~=2.17.1->ansible)
  Downloading pycparser-2.22-py3-none-any.whl.metadata (943 bytes)
Downloading ansible-10.1.0-py3-none-any.whl (47.9 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 47.9/47.9 MB 27.5 MB/s eta 0:00:00
Downloading ansible_core-2.17.1-py3-none-any.whl (2.2 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 2.2/2.2 MB 30.3 MB/s eta 0:00:00
Downloading jinja2-3.1.4-py3-none-any.whl (133 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 133.3/133.3 kB 5.4 MB/s eta 0:00:00
Downloading PyYAML-6.0.1-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (757 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 757.7/757.7 kB 20.7 MB/s eta 0:00:00
Downloading resolvelib-1.0.1-py2.py3-none-any.whl (17 kB)
Downloading cryptography-42.0.8-cp39-abi3-manylinux_2_28_x86_64.whl (3.9 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 3.9/3.9 MB 33.6 MB/s eta 0:00:00
Downloading packaging-24.1-py3-none-any.whl (53 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 54.0/54.0 kB 2.3 MB/s eta 0:00:00
Using cached cffi-1.16.0-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (464 kB)
Downloading MarkupSafe-2.1.5-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (28 kB)
Downloading pycparser-2.22-py3-none-any.whl (117 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 117.6/117.6 kB 5.1 MB/s eta 0:00:00
Installing collected packages: resolvelib, PyYAML, pycparser, packaging, MarkupSafe, jinja2, cffi, cryptography, ansible-core, ansible
Successfully installed MarkupSafe-2.1.5 PyYAML-6.0.1 ansible-10.1.0 ansible-core-2.17.1 cffi-1.16.0 cryptography-42.0.8 jinja2-3.1.4 packaging-24.1 pycparser-2.22 resolvelib-1.0.1

[notice] A new release of pip is available: 24.0 -> 24.1.2
[notice] To update, run: pip install --upgrade pip
```

Now I'm able to run the playbook. 
```sh
ansible-playbook -i inventory.ini webserver.yml
```

It's throwing errors obviously, because I'm testing all of this locally. Let's set up a containerized server simulation with Docker so we can get this do do stuff.
```

PLAY [webservers] ************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *******************************************************************************************************************************************************************************************
fatal: [192.168.1.102]: UNREACHABLE! => {"changed": false, "msg": "Failed to connect to the host via ssh: ssh: connect to host 192.168.1.102 port 22: Connection refused", "unreachable": true}
fatal: [192.168.1.101]: UNREACHABLE! => {"changed": false, "msg": "Failed to connect to the host via ssh: ssh: connect to host 192.168.1.101 port 22: No route to host", "unreachable": true}

PLAY RECAP *******************************************************************************************************************************************************************************************************
192.168.1.101              : ok=0    changed=0    unreachable=1    failed=0    skipped=0    rescued=0    ignored=0   
192.168.1.102              : ok=0    changed=0    unreachable=1    failed=0    skipped=0    rescued=0    ignored=0   

```

Here is my Dockerfile
```Dockerfile
FROM ubuntu:20.04
RUN apt-get update && apt-get install -y openssh-server python3
RUN mkdir /var/run/sshd
RUN echo 'root:password' | chpasswd
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
```

Build it.
```sh
docker build -t ansible-test-server .
```

Run two containers.
```sh
docker run -d -p 2224:22 --name server1 ansible-test-server
docker run -d -p 2223:22 --name server2 ansible-test-server
```

Update the inventory file.
```ini
[webservers]
localhost ansible_port=2224 ansible_user=root ansible_password=password
localhost ansible_port=2223 ansible_user=root ansible_password=password
```

Update your Ansible configuration to allow using password authentication:
Create or edit `ansible.cfg` in your project directory:
```cfg
[defaults]
host_key_checking = False

[ssh_connection]
scp_if_ssh = True
```

Modify your playbook to use apt instead of yum for Ubuntu:
```yaml
---
- hosts: webservers
  become: yes
  tasks:
    - name: Install Apache
      apt:
        name: apache2
        state: present
        update_cache: yes

    - name: Start Apache service
      service:
        name: apache2
        state: started
```

Got an error related to SSH
```
(base) jay@RevenantCyborg-237:~/Web/CyberWorld/ansible$ ansible-playbook -i inventory.ini webserver.yml

PLAY [webservers] ******************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *************************************************************************************************************************************************************************************************************
fatal: [localhost]: FAILED! => {"msg": "to use the 'ssh' connection type with passwords or pkcs11_provider, you must install the sshpass program"}

PLAY RECAP *************************************************************************************************************************************************************************************************************************
localhost                  : ok=0    changed=0    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0   
```

Installed `sshpass`
```sh
sudo apt-get update
sudo apt-get install sshpass
```

Now it's working.

```

PLAY [webservers] ******************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *************************************************************************************************************************************************************************************************************
[WARNING]: Platform linux on host localhost is using the discovered Python interpreter at /usr/bin/python3.8, but future installation of another Python interpreter could change the meaning of that path. See
https://docs.ansible.com/ansible-core/2.17/reference_appendices/interpreter_discovery.html for more information.
ok: [localhost]

TASK [Install Apache] **************************************************************************************************************************************************************************************************************
changed: [localhost]

TASK [Start Apache service] ********************************************************************************************************************************************************************************************************
changed: [localhost]

PLAY RECAP *************************************************************************************************************************************************************************************************************************
localhost                  : ok=3    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```

I think something was using port 2222, which is where I originally had server1 forwarding to. If I skip 2222 and use 2223, 2224, and so on, it works with any number of other ports.

Anyway, it works now.

```sh
docker exec server2 service apache2 status
```

Gives the response
```
 * apache2 is running
```

So does `server3`, which is running on 2224.

So that's a pretty good intro. I'll call that a commit for now and build more complexity and security into it in future examples.