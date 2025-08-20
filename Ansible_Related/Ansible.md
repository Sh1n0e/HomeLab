# Why is this here?

I intend to also try and create another home server for myself using proxmox as a hypervisor on an old laptop of mine. And looking back on how long it took for me to set up everything I need, I realized I could use the bit of practice I got from working wth Ansible in a previous class and use it here for my own passion project as a way to both improve my learning and also have a more efficient deployment.

## What Do I need before I can begin?

1. Install Ansible

```
python3 -m pip install ansible 
```

Note: MAKE SURE TO NOT RUN THIS WITH SUDO.

2. Install docker galaxy extension for ansible to manage docker containers remotely.

```
ansible-galaxy collection install community.docker 
```

After those two steps are done we can begin working with Ansible to set everythign up.

3. A
