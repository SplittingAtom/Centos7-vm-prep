#Hadoop Python Packages
```
cd /etc/yum.repos.d && wget http://archive.cloudera.com/kudu/redhat/7/x86_64/kudu/cloudera-kudu.repo
yum -y install kudu-client-devel kudu-client0
yum -y install -y kudu

pip install Cython kudu-python==1.2.0
pip install kafka-python
pip install impyla

```