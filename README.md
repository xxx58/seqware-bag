## About Seqware-bag

This project consists of a set of Ansible playbooks that allow you to deploy a SeqWare cluster. Metadata makes the Playbooks compatible with [CloudBindle](https://github.com/CloudBindle/Bindle) allowing you to deploy to Amazon-AWS, VirtualBox, Openstack, and vCloud. 

### Improvements Compared with 1.X Bindle

Many tasks that used to be handled by Bindle are now handled by Ansible
* Multithreaded setup and multiple passes
* Templating of files sent to remote
* Logging of stdout and stderr
* Failfast behaviour

### Limitations

Currently, the following specific setup are not handled

* failfast when expected variables are not defined
* setup of encryptfs
* setup of sge-init-master Bash restart script
