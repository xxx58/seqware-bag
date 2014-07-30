## About Seqware-bag

This project consists of a set of Ansible playbooks that allow you to deploy a SeqWare cluster. Metadata makes the Playbooks compatible with [CloudBindle](https://github.com/CloudBindle/Bindle) allowing you to deploy to Amazon-AWS, VirtualBox, Openstack, and vCloud. 

## Sample Configuration Files

### Updated for Bindle 2

In sample\_configs , we have four sample configuration files that can be used to setup SeqWare clusters with Bindle 2. For now, make sure that Bindle and seqware-bag are checked out at the same directory. Copy your desired json config file into the Bindle directory and customize. 

The config files that we have provided are:

* vagrant\_cluster\_launch.seqware.sge\_node.json.template This sets up a seqware single node cluster using git and builds out a cluster from whatever is currently in develop. This is mainly for testing use due to amount of load on only one VM. 
* vagrant\_cluster\_launch.seqware.sge\_cluster.json.template Similar to the previous, this sets up a seqware three node cluster from develop. 
* vagrant\_cluster\_launch.seqware.install.sge\_node.json.template This sets up a production single node cluster using a defined version of SeqWare from artifactory.        
* vagrant\_cluster\_launch.seqware.install.sge\_cluster.json.template This sets up a production three node cluster using a defined version of SeqWare from artifactory


### Needs Work

* vagrant\_cluster\_launch.seqware.admin\_webservice.template This demos the setup of the admin web service by creating one database and one web service node
* bindle1\_configs\\vagrant\_cluster\_launch.seqware.centos.single.json.template This sets up SeqWare on CentOS using Bindle 1.X, this needs to be merged into this project as conditional Ansible tasks

* message of the day on login over ssh

### Improvements Compared with 1.X Bindle

Many tasks that used to be handled by Bindle are now handled by Ansible
* Multithreaded setup and multiple passes
* Templating of files sent to remote
* Logging of stdout and stderr
* Failfast behaviour

### Limitations

Currently, the following specific setup are not handled

* Although we incorporate a modular shared storage, we have not tested with anything but gluster and our json config refers to gluster explicitly
* failfast when expected variables are not defined
* setup of encryptfs
* setup of sge-init-master Bash restart script

## Detailed Descriptions of Templates

### SeqWare - Single Node

This will launch a single node that's a self-contained SeqWare box. This is
suitable for snapshoting for redistribution as a machine image (e.g. AMI on
Amazon's cloud, VirtualBox snapshot, etc).

### SeqWare - Cluster

This will launch a 4 node cluster with 3 workers and one master node. You can
reduce or increase the number of worker nodes depending on your requirements.
Keep in mind the nodes are provisioned sequentially so adding nodes will increase
the runtime.

### SeqWare - Install Only

The profiles previously mentioned install SeqWare from source, build it, and
then run complete integration tests.  This is a very time consuming process, we
created the *.seqware.* install profiles so you could create a new SeqWare node
or cluster from pre-compiled SeqWare release files and avoid the lengthy build
and integration test time. These profiles are, therefore, useful when
installing SeqWare rather than testing it.

### SeqWare - CentOS

A user-contributed profile for setting up SeqWare on a CentOS VM. This needs to be migrated to Ansible

#### CentOS Information

This is for development of features relating to CentOS support. It includes the following updates and fixes:

* A CentOS 6.2 64-bit base box.
* Compatibility with Vagrant v1.4.0
* Minimal, Master and SeqWare Master install scripts for CentOS.
* A veewee definition to create a CentOS base box, for use with [veewee](https://github.com/jedi4ever/veewee).

