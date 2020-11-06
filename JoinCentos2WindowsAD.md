#Join Computer to Windows AD

You will need to have a Window AD user with Admin rights, set the Hostname using the FQDN of the VM, and know the OU the machine will be in

```
yum install realmd sssd oddjob oddjob-mkhomedir adcli samba samba-common samba-common-tools krb5-workstation authselect-compat -y
hostnamectl set-hostname <Add Fully Qualified Domain Name here> #USE FQDN
realm join --user=<Add AD user with rights to join VM to AD> --computer-ou=OU=<Add the OU where the VM will reside.  ex- LabServers> <Add AD Domain Name>
```   


```
authselect select sssd
adcli info <enter your domain here>
authconfig --enablesssd --enablesssdauth --update
```
Make the change below in sssd
```
vi /etc/sssd/sssd.conf
```
Change use_fully_qualified_names = False

```
klist -kt
systemctl start sssd
systemctl is-active sssd
systemctl enable sssd
```



```
id <Add a Username to test>
```

Set AD usergroup that can login to the VM
```
realm permit -g <AD Group>@<AD Domain>

```

Add Sudo access to the LinuxUsers group in Windows AD (I created this and added all my users who will login to Linux VMs)
``` 
visudo
```
and add the line
```
%<AD Group>@<AD Domain> ALL=(ALL)  ALL
```
