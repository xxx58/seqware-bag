Shared Storage Role
----------------------------------

This role was provided by https://github.com/capsid/capsid-vagrant
It is used to setup shared storage for the /mnt/seqware-oozie directory

Note that this is distinct from the regular NFS which is used to share the 
/home/ directories. The current reasoning is that workflow working directories
may need to store files that are much larger than the amount of space
available on one host. We may want to investigate sharing all home directories
using the shared storage role as well.  