# FreeBSD Packer template

Prerequisites:

 * Install [Vagrant](https://www.vagrantup.com)
 * Install [Packer](https://www.packer.io/)
 * Clone this repo onto your machine

To create a vagrant box for FreeBSD 10.2-RELEASE:

 * Build the Vagrant box with: `packer build template-10.2.json`
 * Wait.
 * Add the appropriate Vagrant box for your system.  For example, on VMware:
   `vagrant box add --name FreeBSD-10.2 FreeBSD-10.2-RELEASE-vmware.box`

to build virtualbox image only:

`packer build -only=virtualbox-iso template-10.2.json`

to build kvm image only (hides display also):

`packer build -only=qemu --var qemu_display=none template-10.2.json`

To use any Vagrant box:

 * Initialize vagrant using: `vagrant init --minimal <box name>`
 * Start the Vagrant VM: `vagrant up`
 * Connect to the VM: `vagrant ssh`
 * Hack away

Notes:

 * The VM is set to have 1024MB of RAM and a 20GB drive
 * When bringing vagrant boxes up for the first time, you will
   need sudo privileges to add entries in /etc/exports to allow
   vagrant to mount /vagrant in the guest.  See 
   [Vagrant NFS synced folders](https://docs.vagrantup.com/v2/synced-folders/nfs.html)
