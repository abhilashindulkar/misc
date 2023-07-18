## Ansible Commands Reference

Imperative
1. Ping Target Server(s)

```
# Specific Server
ansible web1 -m ping -i inventory
# Group of Servers
ansible web_servers -m ping -i inventory
```

2. Run command on Targer Server(s)
```
ansible web1 -m ping
ansible all -a "/sbin/reboot"
```

Declarative
1. Run Ansible Playbook for certain tasks defined
```
ansible-playbook ping.yaml -i inventory
```
---

Ansible Roles
1. Create your own ansible role.
```
ansible-galaxy init mysql
```

2. Search for a role in ansible galaxy.
```
ansible-galaxy search mysql
```

3. List currently installed ansible roles
```
ansible-galaxy list
```

3. Install a role from ansible galaxy.
```
ansible-galaxy collection install community.mysql
```