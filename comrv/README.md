
# Overlay Run-Time engine code

This directory includes the RT-Engine source code, implemented according to the [HLD](https://github.com/riscv/riscv-overlay/blob/master/docs/overlay-hld.adoc)
Following are instructions for building it.


# Prerequisites

- Install scons build system (for Debian OS)
    ```
    $ sudo apt-get install scons
    ```
- Toolchain 
  - You can download the latest LLVM toolchain (executables) here:   [LLVM-Debian download link](https://wdc.box.com/s/hqign6gmlzojoxevbzv5xi62li3igple)
  - The toolchain build includes `binutils-gdb` changes needed for the Overlay engine build/link and support.
  - Alternatively you can build it yourself, please check section [Build overlay toolchain](#Build-overlay-toolchain)   


# Configure comrv build

Comrv has compile-switch flags to disable/enable features in the RT engine.
To change these flags open the file  ```./build/SConstruct``` and comment/uncomment relevant comrv features under  ```Env['PUBLIC_DEF']```

# Build comrv library
    $ cd build
    $ scons llvmpath=<path-to-overlay-llvm-installed-directory> gccpath=<path-to-overlay-gcc-installed-directory>
    
# Build overlay toolchain
- The active development repo can be found in this link [llvm-project](https://github.com/westerndigitalcorporation/llvm-project/tree/comrv)
  Follow instructions to build llvm with Overlay support.
- You will need to build `binutils-gdb` as well to be used for link and debug.
  It's advised to build the entry GNU toolchain from this link [riscv-gnu-toolchain](https://github.com/westerndigitalcorporation/riscv-gnu-toolchain/tree/comrv-devel)

Build description:
```
url=https://github.com/westerndigitalcorporation/riscv-gnu-toolchain.git
branch=comrv-devel
hash=f456f6d03fe702d6190a63d035566a935fba95db
```
