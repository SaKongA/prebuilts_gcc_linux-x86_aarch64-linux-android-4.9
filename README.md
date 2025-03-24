# Prebuilt android kernel google GCC build toolchains.

## Info: 
- Backup from: [Google Git](https://android.googlesource.com/platform/prebuilts/gcc/linux-x86/aarch64/aarch64-linux-android-4.9/+/refs/tags/android-9.0.0_r61)
- Version: android-9.0.0_r61

## How to use?
1. Clone Toolchains:
- Enter your kernel source root directory, and clone this repository into your toolchains floder, for exmaple:
```bash
> git clone https://github.com/SaKongA/prebuilts_gcc_linux-x86_aarch64-linux-android-4.9.git -b android-9.0.0_r61 --depth=1 toolchains/gcc
```

2. Set Env:
- Now, you need set your toolchains' environment variables, the following is an example of the environment variables of a kernel compiled with pure gcc for Xiaomi 6 Android 9, you may need to modify it according to your kernel source code:
```bash
> export PATH=$PATH:~/msm8998/toolchains/gcc/bin
> export CROSS_COMPILE=aarch64-linux-android-
> export ARCH=arm64
```
 
 3. Generate make file:
 Use the following command to create a compilation description file for the device kernel. You need to modify the deconfig parameter in the command to the configuration file corresponding to your device:
 ```bash
 > make ARCH=arm64 O=out sagit_user_defconfig
 ```

 4. Start building kernel:
 Now we start compiling the kernel. The j16 in the command is the maximum number of CPU threads, which is usually set to the number of cores multiplied by 2：
 ```bash
 make ARCH=arm64 O=out -j16 2>&1 | tee kernel_log.log
 ```

 5. Check the compilation results:
 Open the out file in the source code root directory to get the file you need:
