## VFd installation guide

VFd installation can be divided into following steps:

* Build DPDK
* Build VFd
* Create VFs on the PFs to be controlled
* Create the main VFd configuration file
* Start VFd
* Create individual VF configuration files
* Start a guest and test

### Environment Overview

* Host: 
```bash
    cloudinfra@compute2:~$ lsb_release -a
    No LSB modules are available.
    Distributor ID: Ubuntu
    Description:    Ubuntu 16.04.2 LTS
    Release:        16.04
    Codename:       xenial
```
* Kernel version: 
```bash
    cloudinfra@compute2:~$ uname -a
    Linux compute2 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

### Build DPDK

You could directly clone DPDK repository from Github if your target node has Internet connectivity. Otherwise you could download compressed DPDK package from [dpdk website](http://www.dpdk.org) and upload that to target environment. In this case, we use the first option.

1. Create a directory; assume that is $HOME/build(`mkdir -p $HOME/build`)
2. Switch to the build directory
3. Execute: `git clone http://dpdk.org/git/dpdk`
      * DPDK version used here is 18.05-rc0. Commit ID: c06ddf9698e0c2a9653cfa971f9ddc205065662c
      * Other version should be OK as well (customer side 16.11/17.08 is used, but that will be upgraded as well)
4. Switch to $HOME/build/dpdk/usertools and execute `bash dpdk-setup.sh` 
5. Select the menu option to a. build the system b. insert the `igb_uio` driver
6. Exit the script
7. Export DPDK variables for later use
      * `export RTE_SDK=$HOME/build/dpdk && export RTE_TARGET=x86_64-native-linuxapp-gcc`

Please note for successful installation, you probably need install some packages like gcc, make, libnuma-dev.
      
