# k8s-vagrant-centos

# About...

This setup is used to create ***kubernetes*** cluster on  ***local laptop / desktop*** using vagrant - with this we can create a ***two node cluster setup*** which contains ***one master*** and ***one worker node*** with one single command.


# What are the prerequisites ?
* [Git](https://git-scm.com/downloads "Git")
* [Vagrant](https://www.vagrantup.com/downloads.html "Vagrant")
* [Oracle Virtual Manger](https://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html "Oracle Virtual Manger")
* `Virtualization needes to be enabled in System BIOS`
* `Recommended laptop/desktop configuration  - 32GB RAM / 8CPU (not to worry base OS will balance the cpu need on time sharing model), 80GB hdd disk space`
* `Minimal laptop/desktop configuration  - 8GB RAM / 4CPU (not to worry base OS will balance the cpu need on time sharing model), 60GB hdd disk space`




# How to deploy kubernetes cluster ?
* Open `bash` terminal
* Checkout the code  (git clone https://github.com/krlex/kubernetes-centos.git)
* `$ cd kubernetes-centos/provisioning`

Recommended settings:`Vagrantfile`
```yaml
VM:
  password: kubeadmin
  master:
    ip: 100.10.10.100
    cpus: 2
    memory: 2048
    vmname: kmaster
    hostname: kmaster.example.com
  worker1:
    ip: 100.10.10.101
    cpus: 3
    memory: 16384
    vmname: kworker1
    hostname: kworker1.example.com
```

Default settings:`Vagrantfile`
```yaml
VM:
  password: kubeadmin
  master:
    ip: 100.10.10.100
    cpus: 2
    memory: 1024
    vmname: kmaster
    hostname: kmaster.example.com
  worker1:
    ip: 100.10.10.101
    cpus: 3
    memory: 1024
    vmname: kworker1
    hostname: kworker1.example.com
```


By running the below command kubernetes cluster will be created with 2 Centos VM's installed.

* `vagrant up`


# What are the VM's configured ?
By default below are the IP Addresses that will be configured for the VM's

Name|IP|OS|RAM|CPU|
|----|----|----|----|----|
kmaster  |100.10.10.100|CentOS7|1 GB|2|
kworker1 |100.10.10.101|CentOS7|1 GB|3|


# How to access Kubernetes Dashboard ?
The ***Kubernetes Dashboard*** can be accessed via the below ***URL*** without any changes from your host machine

[http://100.10.10.100:30070/#!/overview?namespace=_all](http://100.10.10.100:30070/#!/overview?namespace=_all)


# How to access Vagrant VM's ?

The Vagrant VM can be accessed in two ways

1) ***Login*** through ***vagrant ssh***
* `$ cd kubernetes-centos/provisioning`
* `$ vagrant ssh kmaster`
* `$ vagrant ssh kworker1`

2) ***Login*** through ***putty***
* `100.10.10.100 / 100.10.10.101` [Username/Password:***vagrant/vagrant (OR) root/kubeadmin***]


# How to stop Vagrant VM's ?
* `$ cd kubernetes-centos/provisioning`
* `$ vagrant halt`

# How to restart Vagrant VM's ?
* `$ cd kubernetes-centos/provisioning`
* `$ vagrant up`

# How to destroy Vagrant VM's ?
* `$ cd kubernetes-centos/provisioning`
* `$ vagrant destroy`
