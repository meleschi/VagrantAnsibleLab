# VagrantAnsibleLab
A set of Vagrant and Ansible configuration files to spin up VMs using Vagrant / VirtualBox  suitable for learning or developing using Ansible.  Both ansible-core and ansible-navigator are installed.  At the time the VMs are spun up, the most current version of both are installed.

Requirements:
Virtualbox
Vagrant
Ram - 8GB Minimum with stock # of VMs configured
Disk - 8GB Minumum with stock # of VMs configured

How to install Vagrant: https://developer.hashicorp.com/vagrant/docs/installation

How to install VirtualBox: https://www.virtualbox.org/manual/ch02.html

The VMs used here require internet access to install and configure various items.  Please ensure you have internet access when you are starting the VMs.

Once the above requirements have been met, start all VMs with a single command:

```
./start-all-vms.sh
```

(Please be patient, this will take a few minutes)

Once the VMs have been started, connect and use the workstation VM using the following command:

```
./connect-workstation.sh
cd classwork
```

If you keep your labwork / playbooks within ./classwork/, this will survive across rebuilds of the VMs and you will not loose any data.

There is an example playbook under ./classwork/playbook that will perform a 'dnf -y update" to all of the VMs spun up in Vagrant.  To use please run the following command after you've connected to the workstation:

(using ansible-navigator)
```
[vagrant@workstation classwork]$ ansible-navigator run -m stdout playbook/system-updates.yml
```

(using ansible-playbook)
```
[vagrant@workstation classwork]$ ansible-playbook playbook/system-updates.yml
```
The stock vagrant configs will spin up the following VMs:

```
workstation=[
  {
    :hostname => "workstation.example.com",
    :ip => "192.168.60.3",
    :box => "rockylinux/9",
    :ram => 2048
  }
]
```
```
servers=[
  {
    :hostname => "server1.example.com",
    :ip => "192.168.60.4",
    :box => "rockylinux/9",
    :ram => 1024
  },
  {
    :hostname => "server2.example.com",
    :ip => "192.168.60.5",
    :box => "rockylinux/9",
    :ram => 1024
  },
  {
    :hostname => "server3.example.com",
    :ip => "192.168.60.6",
    :box => "rockylinux/9",
    :ram => 1024
  },
  {
    :hostname => "server4.example.com",
    :ip => "192.168.60.7",
    :box => "rockylinux/9",
    :ram => 1024
  },
  {
    :hostname => "server5.example.com",
    :ip => "192.168.60.8",
    :box => "rockylinux/9",
    :ram => 1024
  }
]
```
