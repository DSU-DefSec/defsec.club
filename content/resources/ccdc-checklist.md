---
title: "CCDC Checklist"
---

# CCDC Checklist

This is a sample checklist for [CCDC](/competitions/dsu_competitions/dcdc/)-style competitions.

## Linux

### Password Changes

Change all shell user passwords:
```text
read; for u in $(cat /etc/passwd | grep -E "/bin/.*sh" | cut -d":" -f1); do echo "$u:$REPLY" | chpasswd ; done
```


Change all shell users' Samba passwords:
```text
read; for u in $(cat /etc/passwd | grep -E "/bin/.*sh" | cut -d":" -f1); do echo -e "$REPLY\n$REPLY" | smbpasswd -sU $u ; done
```


### Firewall

Enable the firewall:
```text
ufw enable
```

Check the permitted ports and remove unnecessary whitelists:
```text
ufw status numbered

ufw delete [number]
```


### Service Hardening

#### PHP

Searching for web shells:
```text
Find your webroot (Typically /var/www/html). Look through .php files for functions like system or shell_exec being used.
```

Disable functions that allow hackers to execute code on your system:
```text
disable_functions = proc_open, popen, disk_free_space, diskfreespace, set_time_limit, leak, tmpfile, exec, system, shell_exec, passthru, show_source, system, phpinfo, pcntl_alarm, pcntl_fork, pcntl_waitpid, pcntl_wait, pcntl_wifexited, pcntl_wifstopped, pcntl_wifsignaled, pcntl_wexitstatus, pcntl_wtermsig, pcntl_wstopsig, pcntl_signal, pcntl_signal_dispatch, pcntl_get_last_error, pcntl_strerror, pcntl_sigprocmask, pcntl_sigwaitinfo, pcntl_sigtimedwait, pcntl_exec, pcntl_getpriority, pcntl_setpriority

Add line above to /etc/php/7.4/apache2/php.ini.
```

*Note: This may not be your file location for php.ini. If it isn't you'll need to find it manually.*

#### SSH

Remove keys:
```text
rm /home/*/.ssh/authorized_keys
rm /root/.ssh/authorized_keys
```

Modify config:
```text
Modify /etc/ssh/sshd_config so the settings match with the settings below.
- PermitRootLogin no
- PermitEmptyPasswords no
- PubkeyAuthentication no

```


## Windows

### Password Changes

Change all passwords for local users:
```text
Get-LocalUser | Set-LocalUser -password (read-host -AsSecureString)
```

Change all passwords for domain users:
```text
Get-ADUser -Filter * | Out-GridView -PassThru | Set-ADAccountPassword -NewPassword (Read-Host -AsSecureString) -Reset
```

*Note: These must be ran in an administrative powershell. When ran there is sometimes no prompt. Just type in the password and hit enter.*


### Firewall

Check that all the profiles are enabled and it blocks all inbound by default:
```text
Windows + R, wf.msc > Windows Defender Firewall Properties
```

*Note: If the option to enable the firewall is grayed out, that means it is being disabled by the registry or group policy*

Remove rules you don't need:
```text
Windows + R, wf.msc > Inbound Rules
```
Look for any that allow all traffic inbound.


### Other User Management

```text
Windows Key + R, compmgmt.msc > Local Users and Groups

  - Remove all users that aren't required.
  - Remove users from groups that they don't need to be apart of.
  - Disable the default Administrator and Guest account
```


### Service Hardening

#### SMB

Check SMB Version:
```text
Get-WindowsOptionalFeature -Online -FeatureName SMB1Protocol

OR

Get-SmbServerConfiguration | Select EnableSMB1Protocol
```


If SMBv1 is enabled then disable it:
```text
Disable-WindowsOptionalFeature -Online -FeatureName SMB1Protocol

OR

Set-SmbServerConfiguration -EnableSMB1Protocol $false
```

If SMB is required then enable SMBv2 which is secure:
```text
Set-SmbServerConfiguration -EnableSMB2Protocol $true
```

#### RDP

Enable Network Level Authentication:
```text
Windows Key + R, systempropertiesremote, then double check if "Allow connections only from computers running remote desktop with Network Level Authentication.

If this option is grayed out check out: https://www.kapilarya.com/how-to-configure-network-level-authentication-for-remote-desktop-connections-windows-10
```

Make sure only required users are in RDP group:
```text
Windows Key + R, systempropertiesremote, Under "Select Users", double check that only the Remote Desktop Users groups is added.

Windows Key + R, compmgmt.msc, then check Remote Desktop Users for user accounts that shouldn't be there.
```

## Finished this checklist?

Find much more at <https://drive.google.com/drive/folders/13KuyOkwokTuIhO9wsP0PayGGXxYLRhsJ>
