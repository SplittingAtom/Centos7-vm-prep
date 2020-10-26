# Centos7-vm-prep

Turn off SElinux
```
sestatus
vi /etc/selinux/config
```
Change SELINUX=disabled to SELINUX=enabled

Turn off Firewall
```
systemctl disable firewalld
systemctl stop firewalld
```

Update Centos and install wget
```
yum update yum -y
yum install wget -y
```

Add Proxmox Agent
First enable QEMU Guest Agent in Proxmox options for the VM
```

yum install qemu-guest-agent -y
systemctl enable qemu-guest-agent
systemctl start qemu-guest-agent
```

#Anaconda Install
```
wget https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh
bash Anaconda3-2020.02-Linux-x86_64.sh
rm Anaconda3-2020.02-Linux-x86_64.sh
conda -init
source ~/.bashrc
python --version
```

Install all that other stuff I usually need
```
pip install cython
pip install --upgrade setuptools
pip install ez_setup

yum -y install python-devel libevent-devel gcc libffi-devel openssl-devel gcc-c++ jq
easy_install gevent

pip install Jinja2 pyzmq tornado flask

```
#Docker Setup
```
yum install -y yum-utils
yum-config-manager     --add-repo     https://download.docker.com/linux/centos/docker-ce.repo
yum -y install docker-ce docker-ce-cli containerd.io
systemctl enable docker
systemctl start docker
```
Install Docker COmpose
```
curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

Install jq
```
yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
yum install jq -y
``` 




   
