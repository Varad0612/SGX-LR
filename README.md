# INSTALL LOCAL

- Use Linux/Linux VM, see PreReqs here:
  https://github.com/intel/linux-sgx#install-the-intelr-sgx-sdk (Do not follow
the rest of those install instructions! - follow mine)
	
- Get SDK Installer (note: driver not needed)
```
wget https://download.01.org/intel-sgx/sgx-linux/2.13/distro/ubuntu20.04-server/sgx_linux_x64_sdk_2.13.100.4.bin
chmod a+x sgx_linux_x64_sdk_2.13.100.4.bin
./sgx_linux_x64_sdk_2.13.100.4.bin
```
- Source environment variables according to instructions
- Get modified SGX GMP
```
mkdir sgxgmp_build
git clone https://github.com/intel/sgx-gmp.git
cd sgx-gmp
./configure --enable-cxx --enable-sgx --enable-static --disable-shared --enable-assembly --prefix=../sgxgmp_build
make
make install
```
- Clone SGX-LR
- Change SGX-LR Makefile to reflect correct SDK and GMP build directories (should be correct already)

```
cd SGX-LR
make
./sgx_lr_exec
```









# INSTALL NOTES FOR BIG MACHINE

[x] Build (enclave modified) GMP library (https://github.com/intel/sgx-gmp)
Note: make check doesn't pass - ostensibly bc of sgx defined types

In this order (Intel_SGX_Installation_Guide_Linux_2.13_Open_Source)
[x] Build SGX Pre-Reqs
[x] Build SGX Driver (without ECDSA attestation)
Note: may need to (re)execute /home/jess/sgxsdk/enviornment for correct env vars after reinitializing

[x] Build SGX PSW
[x] Build SGX SDK 
Note: mitigation tools?
Reference: https://download.01.org/intel-sgx/sgx-linux/2.13/docs/Intel_SGX_Installation_Guide_Linux_2.13_Open_Source.pdf

[x] set appropriate directories in Makefile


# RUN

Note: may need to (re)execute /home/jess/sgxsdk/enviornment for correct env vars after reinitializing

make


# DOCUMENTATION

TODO: We should create a guide here
