# openjdk8
记录下JDK8的学习之路
#编译JDK8
1. 环境准备：安装boot jdk. sudo apt-get install openjdk7
源代码是在openjdk.java.net下载的
解压缩后，进入openjdk的根目录
需要unset JAVA_TOOL_OPTIONS,否则，configure会报错
``` 
bash configure
```

之后执行make即可，make会构建全部模块，包括hotspot，corba等，在我的机器上执行时间不到10分钟（i5 4460/8G/4核心）
```
make CONF=linux-x86_64-normal-server-fastdebug HOTSPOT_BUILD_JOBS=4
```
