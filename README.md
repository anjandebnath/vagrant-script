# vagrant-script
Vagrant provides the framework and configuration format to create and manage complete portable development environments. These development environments can live on your computer or in the cloud, and are portable between Windows, Mac OS X, and Linux.


# Vagrant linux setup on Windows machine 

### step 1: install virtual box with vagrant 
https://portal.cloud.hashicorp.com/vagrant/discover/ubuntu/jammy64

### step 2: plugin setup for sync and share host folders to guest machine
    vagrant plugin install vagrant-vbguest |output: Installed the plugin 'vagrant-vbguest (0.32.0)'!

    vagrant plugin install vagrant-vbguest --plugin-version 0.31.0
### step 3: up the virtual machine
vagrant up
### step 4: provision 
vagrant provision

### Docker and Docker compose install in vagrant 
https://aqibhafeez473.hashnode.dev/setting-up-docker-on-ubuntu-with-bash-script-day-3

    Docker version 28.0.4, build b8034c0
    Docker Compose version v2.35.0

### VBoxManage --version
    6.1.50_Ubuntur161033

### mount related problem
    dpkg -l | grep virtualbox
    lsmod | grep vbox

##### output should be
    vboxsf                 36864  0
    vboxguest              45056  1 vboxsf
    vboxvideo              28672  0
    drm_vram_helper        24576  1 vboxvideo
    drm_ttm_helper         16384  2 drm_vram_helper,vboxvideo
    drm_kms_helper        311296  4 drm_vram_helper,vboxvideo
    drm                   622592  6 drm_kms_helper,drm_vram_helper,vboxvideo,drm_ttm_helper,ttm

`The vboxsf module is part of VirtualBox Guest Additions and is required for mounting shared folders in the guest OS`

### Try mounting manually 
    sudo mkdir -p /home/vagrant/data
    sudo mount -t vboxsf -v -o uid=1000,gid=1000 data /home/vagrant/data


