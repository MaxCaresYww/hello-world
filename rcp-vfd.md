## VFd installation guide

VFd installation can be divided into following steps:

* Build DPDK
* Build VFd
* Create VFs on the PFs to be controlled
* Create the main VFd configuration file
* Start VFd
* Create individual VF configuration files
* Start a guest and test

### Build DPDK

You could directly clone DPDK repository from Github if your target node has Internet connectivity. Otherwise you could download compressed DPDK package from [dpdk website](dpdk.org) and upload that to target environment. In this case, we use the first option.

1. Create a directory (`mkdir -p $HOME/build`; assume that is $HOME/build
2. Switch to the build directory
3. Execute: git clone http://dpdk.org/git/dpdk
4. Switch to $HOME/build/dpdk/usertools and execute ```bash dpdk-setup.sh``` 
