# 3DReconstruction_identification
Identity recognition system based on 3D human body modeling

## OpenNI 2 SDK Environment Configuration
>For reference only, the development environment is currently being migrated to the Astra SDK (as it provides a skeleton feature API)

Hardware environment: Zora P1 development board+Astra camera

Software environment: Ubuntu based on Arm64 pre installed on the development board; OpenNI2 SDK

### Equipment function verification

In Linux environment, Astra can be directly connected to the development board via USB

**Download OpenNI2 SDK * * ` OpenNI-Linux-Arm64-2.3.0.65 ` from the official website [Android System Firmware, 3D Vision Developer Community, Orbbec. com. cn]（ https://developer.orbbec.com.cn/download.html?id=64 ）If there are any changes to the link path, please search for it on the official website by yourself.

Extract to the development board directory and run it/ Install. sh * * (requires modifying file permissions with chmod. As an unqualified Linux developer, it is usually a simple and crude ` chmod+777 install. sh ')`

>Note: This script does two things in total, adding UDEV rules to the camera device and writing the development environment to the 'OpenNIDevEnvironment' file

Install the dependencies mentioned in the README file

```
- GCC 4.x
- Python 2.6+/3.x
- LibUSB 1.0.x
- LibUDEV
- JDK 6.0
- FreeGLUT3
- Doxygen
- GraphViz
```

Run NiViewer in the directory 'OpenNI Linux-Arm64-2.3.0.65/Tools/Orm64-Release' to verify

### Development environment configuration

Load the system variable 'source OpenNIDevEnvironment' generated before loading`

`There are some Sample Programs under the Samples directory For example, opening SimpleRead`

Modify the Makefile file because the definition of 'INC-DIRS' in the Makefile uses'../...'/ Include, but the actual file path is lowercase 'include' The Linux system is case sensitive, so change the include to lowercase or simply change the folder name to uppercase. Because I see that other programs use lowercase. And the referenced/ The Common directory does not exist in the sample project. But it didn't affect the subsequent compilation, so I haven't paid attention to it for the time being

Execute 'make' and successfully compile. Although it is stated in the 'README' of the root directory that some system variables need to be defined for ARM platform compilation, there are no errors reported here, so I am not currently concerned.

Execute the generated file 'SimpleRead/Bin/Arm64 Release/SimpleRead'`

I haven't looked at the source code, so I don't know what this program means. However, when there is no one in front of the camera, the output is 0. If someone outputs a bunch of numbers, I think it's correct for now.

Now you can build your own project according to the engineering architecture in the Sample.

## Astra SDK environment configuration
Hardware environment: Zora P1 development board+Astra camera

Software environment: Ubuntu based on Arm64 pre installed on the development board; OpenNI2 SDK

Because according to the official description, Astra provides an SDK for extracting bone information, which is useful for experiments, let's try configuring this development environment.

1. Download the Linux-aarch64 SDK (orbbec. com. cn) for Ubuntu 14.04 or later on the official website（ https://api.orbbec.com.cn/uploads/files/AstraSDK-v2.1.1-24f74b8b15-20200426T012326Z-Linux-aarch64.tar.gz )
2. After decompression, run 'install/install. sh'. Unlike the above, this script only prints out the environment variables. It is recommended to place them in the configuration file of the system variables, such as'. bash_defile 'or'. bashrc '. Because the OpenNI SDK development environment has been configured, it is still necessary to save these two system variables to the 'environment' file. Execute 'source environment' before compilation.
3. Run cmake in the 'sample' directory`
4. According to the generated Makefile, run the corresponding target to compile. Like 'make InfraredColorReaderEvent'`
5. The generated program is located in the 'samples/bin' directory

>This project currently relies on the Astra SDK environment and will be placed in the samples directory

## Visual Studio 2019+AstraSDK Development Environment Configuration
Refer to the official guidance document https://developer.orbbec.com.cn/technical_library.html?id=22

Note that the generated exe file depends on the dll file in the bin directory of AstraSDK

So we also need to copy those DLLs to the generation path of our own project, such as under 'x64/Debug'



## This project environment

OpenCV 4.2

jsonxx

glew-2.1.0

glfw-3.3.2

openpose v1.6
