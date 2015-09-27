# openjdk8
记录下JDK8的学习之路
#编译JDK8
1. 环境准备：安装boot jdk. sudo apt-get install openjdk7
 源代码是在openjdk.java.net下载的,文件名称为：openjdk-8-src-b132-03_mar_2014.zip
 解压缩后，进入openjdk的根目录
 需要unset JAVA_TOOL_OPTIONS,否则，configure会报错
```bash 
unset JAVA_TOOL_OPTIONS
bash configure --with-debug-level=slowdebug
```
2. 之后需要修改下这个文件，原因出在adjust-mflags上面，应该是个BUG，我是直接把参数写出来了，不同的人CPU核心个数不一样，自己注意，改成和自己核心数目一样即可。如果你有一个8核的CPU，设置 -j8即可
```bash
# **** MODIFIED BY DXT
#MFLAGS-adjusted = -r `$(adjust-mflags) "$(MFLAGS)" "$(HOTSPOT_BUILD_JOBS)"`
MFLAGS-adjusted = -r $(MFLAGS) -j4
```
3. 之后执行make即可，make会构建全部模块，包括hotspot，corba等，在我的机器上执行时间不到10分钟（i5 4460/8G/4核心）
```bash
make CONF=linux-x86_64-normal-server-fastdebug HOTSPOT_BUILD_JOBS=4
```
