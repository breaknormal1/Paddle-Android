# Paddle-Android

要在android app中使用paddlepaddle，大概需要一下几步：
1。配置编译android版paddle：
准备交叉编译环境，构建独立工具链
https://github.com/PaddlePaddle/Paddle/blob/develop/doc/mobile/cross_compiling_for_android_cn.md
下载Paddle源码，并cmake

$ git clone https://github.com/PaddlePaddle/Paddle.git
$ cd Paddle
$ mkdir build
$ cd build
$ cmake -DCMAKE_SYSTEM_NAME=Android 
-DANDROID_STANDALONE_TOOLCHAIN=/home/wyf/android-ndk-r14b/build/tools/arm64_standalone_toolchain 
-DANDROID_ABI=arm64-v8a 
-DUSE_EIGEN_FOR_BLAS=OFF 
-DCMAKE_INSTALL_PREFIX=/home/wyf/paddle-android-demo   //该目录也是第二步的DPADDLE_ROOT
-DWITH_C_API=ON 
-DWITH_SWIG_PY=OFF 
..

CMake配置完成后，执行以下命令，PaddlePaddle将自动下载和编译所有第三方依赖库、编译和安装PaddlePaddle预测库。

make
make install

2。编译示例程序
参考 https://github.com/PaddlePaddle/Mobile/blob/develop/benchmark/tool/C/README_cn.md 
Step 2，编译示例程序
以arm64-v8a架构为例：
$ git clone https://github.com/PaddlePaddle/Mobile.git
$ cd Mobile/benchmark/tool/C/
$ mkdir build
$ cd build

$ cmake .. \
        -DANDROID_ABI=arm64-v8a \
        -DANDROID_STANDALONE_TOOLCHAIN=your/path/to/arm64_standalone_toolchain \
        -DPADDLE_ROOT=The output path generated in the first step \
        -DCMAKE_BUILD_TYPE=MinSizeRel

$ make


3。待续。。。。
