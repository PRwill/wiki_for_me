# 那些年我们踩过的坑
- Q:docker无法访问内网
- A:docker无内网dns，由于docker会自动挂载本机的`/etc/hosts` `/etc/resolve.conf`,所以修改docker的对应文件是无效的。解决方法在本机的`/etc/resolve.conf`中加入:
~~~
nameserver 内网DNS
~~~

- Q:docker在`build`的过程中提示：`"docker build" requires exactly 1 argument`
- A:正确的docker`build`语句如下：（可能缺少了最后的.)
~~~
$ docker build -t docker-registry.qiyi.virtual/oss/python-test:python-transform-v1 -f ./Dockerfile .
~~~

- Q:docker在`build`的过程中加载了很多数据。
- A:docker把当前目录下的很多文件都加载进去了，建议如下:
~~~
$ mkdir docker
$ cd docker
$ cp <your-dockerfile-path> ./
~~~

- Q:如何使用`Python`的虚拟环境
- A:执行命令：
~~~
$ source your-venv-position/venv/bin//activate
~~~

- Q:当docker以`-d`选项运行立即退出
- A:大概率由于docker执行的程序退出/出错，请检查程序运行情况。
