# IMPLEMENTING 10 CIS BENCHMARK FOR UBUNTU 20.04 LTS

## CIS
### 1: SYSTEM CONFIGURATION
#### 1.1: Filesystem Configuration
##### 1.1.1: Ensure mounting of cramfs filesystems is disabled (Scored)
```bash
sudo modprobe -n -v cramfs
```
##### 1.1.2: Ensure mounting of freevxfs filesystems is disabled (Scored)
```bash
sudo modprobe -n -v freevxfs
```
##### 1.1.3: Ensure mounting of jffs2 filesystems is disabled (Scored)
```bash
sudo modprobe -n -v jffs2
```
##### 1.1.4: Ensure mounting of hfs filesystems is disabled (Scored)
```bash
sudo modprobe -n -v hfs
```
##### 1.1.5: Ensure mounting of hfsplus filesystems is disabled (Scored)
```bash
sudo modprobe -n -v hfsplus
```
##### 1.1.8: Ensure mounting of FAT filesystems is disabled (Scored)
```bash
sudo modprobe -n -v vfat
```
##### 1.1.9: Ensure mounting of ntfs filesystems is disabled (Scored)
```bash
sudo modprobe -n -v ntfs
```
#### 1.2: Configure Software Updates
##### 1.2.1: Ensure package manager repositories are configured (Not Scored)
```bash
sudo apt-get update
```
##### 1.2.3: Ensure gpgcheck is globally activated (Scored)
```bash
sudo grep -r gpgcheck /etc/apt/
```
##### 1.2.4: Ensure package manager repositories are configured (Not Scored)
```bash
sudo apt-get update
```
##### 1.2.5: Ensure GPG keys are configured (Not Scored)
```bash
sudo apt-key list
```
##### 1.2.6: Ensure gpgcheck is globally activated (Scored)
```bash
sudo grep -r gpgcheck /etc/apt/
```
#### 1.3: Filesystem Integrity Checking
##### 1.3.1: Ensure AIDE is installed (Scored)
```bash
sudo apt-get install aide
```
##### 1.3.2: Ensure filesystem integrity is regularly checked (Scored)
```bash
sudo aide --init
sudo cp /var/lib/aide/aide.db.new.gz /var/lib/aide/aide.db.gz
sudo aide --check
```

### 2: services
#### 2.1: inetd services
##### 2.1.1: Ensure chargen services are not enabled (Scored)
```bash
sudo systemctl is-enabled chargen-dgram
sudo systemctl is-enabled chargen-stream
```
##### 2.1.2: Ensure daytime services are not enabled (Scored)
```bash
sudo systemctl is-enabled daytime-dgram
sudo systemctl is-enabled daytime-stream
```
##### 2.1.3: Ensure discard services are not enabled (Scored)
```bash
sudo systemctl is-enabled discard-dgram
sudo systemctl is-enabled discard-stream
```
##### 2.1.4: Ensure echo services are not enabled (Scored)
```bash
sudo systemctl is-enabled echo-dgram
sudo systemctl is-enabled echo-stream
```
##### 2.1.5: Ensure time services are not enabled (Scored)
```bash
sudo systemctl is-enabled time-dgram
sudo systemctl is-enabled time-stream
```
##### 2.1.6: Ensure tftp server is not enabled (Scored)
```bash
sudo systemctl is-enabled tftp
```
##### 2.1.7: Ensure xinetd is not enabled (Scored)
```bash
sudo systemctl is-enabled xinetd
```
#### 2.2: Special Purpose Services
##### 2.2.1: Ensure time synchronization is in use (Scored)
```bash
sudo timedatectl
```
##### 2.2.2: Ensure ntp is configured (Scored)
```bash
sudo apt-get install ntp
```
##### 2.2.3: Ensure X Window System is not installed (Scored)
```bash
sudo dpkg -s xserver-xorg
```
##### 2.2.4: Ensure Avahi Server is not enabled (Scored)
```bash
sudo systemctl is-enabled avahi-daemon
```
### 3: network configuration
#### 3.1: Network Parameters (Host Only)
##### 3.1.1: Ensure packet redirect sending is disabled (Scored)
```bash
sudo sysctl net.ipv4.conf.all.send_redirects
sudo sysctl net.ipv4.conf.default.send_redirects
```
##### 3.1.2: Ensure source routed packets are not accepted (Scored)
```bash
sudo sysctl net.ipv4.conf.all.accept_source_route
sudo sysctl net.ipv4.conf.default.accept_source_route
```
##### 3.1.3: Ensure ICMP redirects are not accepted (Scored)
```bash
sudo sysctl net.ipv4.conf.all.accept_redirects
sudo sysctl net.ipv4.conf.default.accept_redirects
```
##### 3.1.4: Ensure secure ICMP redirects are not accepted (Scored)
```bash
sudo sysctl net.ipv4.conf.all.secure_redirects
sudo sysctl net.ipv4.conf.default.secure_redirects
```


### 4: logging and auditing
#### 4.1: Configure System Accounting (auditd)
##### 4.1.1: Ensure auditd is installed (Scored)
```bash
sudo dpkg -s auditd
```
##### 4.1.2: Ensure auditd service is enabled (Scored)
```bash
sudo systemctl is-enabled auditd
```
##### 4.1.3: Ensure auditing for processes that start prior to auditd is enabled (Scored)
```bash
sudo grep "^\s*linux" /boot/grub/grub.cfg
```
##### 4.1.4: Ensure events that modify date and time information are collected (Scored)
```bash
sudo grep time-change /etc/audit/audit.rules
```
##### 4.1.5: Ensure events that modify user/group information are collected (Scored)
```bash
sudo grep identity /etc/audit/audit.rules
```
### 5: Access, Authentication and Authorization
#### 5.1: Configure cron
##### 5.1.1: Ensure cron daemon is enabled (Scored)
```bash
sudo systemctl is-enabled cron
```
##### 5.1.2: Ensure permissions on /etc/crontab are configured (Scored)
```bash
sudo stat -c %a /etc/crontab
```
##### 5.1.3: Ensure permissions on /etc/cron.hourly are configured (Scored)
```bash
sudo stat -c %a /etc/cron.hourly
```
##### 5.1.4: Ensure permissions on /etc/cron.daily are configured (Scored)
```bash
sudo stat -c %a /etc/cron.daily
```
##### 5.1.5: Ensure permissions on /etc/cron.weekly are configured (Scored)
```bash
sudo stat -c %a /etc/cron.weekly
```

### 6: System Maintenance
#### 6.1: System File Permissions
##### 6.1.1: Ensure permissions on /etc/passwd are configured (Scored)
```bash
sudo stat -c %a /etc/passwd
```
##### 6.1.2: Ensure permissions on /etc/shadow are configured (Scored)
```bash
sudo stat -c %a /etc/shadow
```
##### 6.1.3: Ensure permissions on /etc/group are configured (Scored)
```bash
sudo stat -c %a /etc/group
```
##### 6.1.4: Ensure permissions on /etc/gshadow are configured (Scored)
```bash
sudo stat -c %a /etc/gshadow
```
##### 6.1.5: Ensure permissions on /etc/passwd- are configured (Scored)
```bash
sudo stat -c %a /etc/passwd-
```


### 7: Additional Process Hardening
#### 7.1: Restrict Core Dumps
##### 7.1.1: Ensure core dumps are restricted (Scored)
```bash
sudo sysctl fs.suid_dumpable
```
#### 7.2: Restrict Address Space Layout Randomization (ASLR)
##### 7.2.1: Ensure address space layout randomization (ASLR) is enabled (Scored)
```bash
sudo sysctl kernel.randomize_va_space
```

### 8: Network Configuration
#### 8.1: Network Parameters (Host Only)
##### 8.1.1: Ensure packet redirect sending is disabled (Scored)
```bash
sudo sysctl net.ipv4.conf.all.send_redirects
sudo sysctl net.ipv4.conf.default.send_redirects
```
##### 8.1.2: Ensure source routed packets are not accepted (Scored)
```bash
sudo sysctl net.ipv4.conf.all.accept_source_route
sudo sysctl net.ipv4.conf.default.accept_source_route
```
##### 8.1.3: Ensure ICMP redirects are not accepted (Scored)
```bash
sudo sysctl net.ipv4.conf.all.accept_redirects
sudo sysctl net.ipv4.conf.default.accept_redirects
```

### 9: Logging and Auditing
#### 9.1: Configure rsyslog
##### 9.1.1: Ensure rsyslog Service is enabled (Scored)
```bash
sudo systemctl is-enabled rsyslog
```
##### 9.1.2: Ensure logging is configured (Not Scored)
```bash
sudo cat /etc/rsyslog.conf
```
##### 9.1.3: Ensure rsyslog default file permissions configured (Scored)
```bash
sudo grep -E "^\$FileCreateMode" /etc/rsyslog.conf
```
##### 9.1.4: Ensure rsyslog is configured to send logs to a remote log host (Scored)
```bash
sudo grep -E "^\*.*[^I][^I]*@" /etc/rsyslog.conf
```
##### 9.1.5: Ensure remote rsyslog messages are only accepted on designated log hosts. (Not Scored)
```bash
sudo grep -E "^\$ModLoad imtcp.so" /etc/rsyslog.conf
sudo grep -E "^\$InputTCPServerRun" /etc/rsyslog.conf
```

### 10: System Access, Authentication and Authorization
#### 10.1: Configure PAM
##### 10.1.1: Ensure password creation requirements are configured (Scored)
```bash
sudo grep pam_pwquality.so /etc/pam.d/common-password
```
##### 10.1.2: Ensure lockout for failed password attempts is configured (Scored)
```bash
sudo grep pam_faillock.so /etc/pam.d/password-auth
sudo grep pam_faillock.so /etc/pam.d/system-auth
```
##### 10.1.3: Ensure password reuse is limited (Scored)
```bash
sudo grep remember /etc/pam.d/password-auth
sudo grep remember /etc/pam.d/system-auth
```


