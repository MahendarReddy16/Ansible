```
ansible -i 172.31.13.105, all -e ansible_user=<username> -e ansible_password=<password> -m ping
```

```
ansible -i <private IP>, all -e ansible_user=<username> -e ansible_password=<password> -b -m dnf -a "name=nginx state=install"
```

```
ansible -i <private IP>, all -e ansible_user=<username> -e ansible_password=<password> -b -m service -a "name=nginx state=started"
```