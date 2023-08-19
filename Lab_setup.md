Let configure SSH key so ansible can access remote hosts

we using 6 hosts in total - 3 centos and 3 ubuntu based
    
```cmd
for user in ansible root; do for host in ubuntu centos; do for instance in 1 2 3;do sshpass -f passwd.txt ssh-copy-id -o StrictHostKeyChecking=no ${user}@${host}${instance}; done; done; done
```

Let test ansible connectivity
```cnd
ansible@ubuntu-c:~$ ansible -i,ubuntu1,ubuntu2,ubuntu3,centos1,centos2,centos3 all -m ping -o
ubuntu2 | SUCCESS => {"ansible_facts": {"discovered_interpreter_python": "/usr/bin/python3"},"changed": false,"ping": "pong"}
ubuntu1 | SUCCESS => {"ansible_facts": {"discovered_interpreter_python": "/usr/bin/python3"},"changed": false,"ping": "pong"}
ubuntu3 | SUCCESS => {"ansible_facts": {"discovered_interpreter_python": "/usr/bin/python3"},"changed": false,"ping": "pong"}
centos2 | SUCCESS => {"ansible_facts": {"discovered_interpreter_python": "/usr/libexec/platform-python"},"changed": false,"ping": "pong"}
centos1 | SUCCESS => {"ansible_facts": {"discovered_interpreter_python": "/usr/libexec/platform-python"},"changed": false,"ping": "pong"}
centos3 | SUCCESS => {"ansible_facts": {"discovered_interpreter_python": "/usr/libexec/platform-python"},"changed": false,"ping": "pong"}
ansible@ubuntu-c:~$
```