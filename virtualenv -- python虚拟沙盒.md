# [virtualenv -- python虚拟沙盒](https://www.cnblogs.com/tk091/p/3700013.html)



有人说：virtualenv、fabric 和 pip 是 pythoneer 的三大神器。

一、安装

```
pip install virtualenv
```

因为我已经安装了pip，那么就直接用pip来安装了，简单方便。

其它的安装方式请参考官方网站：<http://www.virtualenv.org/en/latest/index.html>

二、创建虚拟环境

```
root@kali:/recall/code# virtualenv test_env
New python executable in test_env/bin/python
Installing setuptools, pip...done.
root@kali:/recall/code# 
```

很简单，就是virtualenv 环境名称[自定义的名称，自己喜欢什么就写什么]

默认情况下，虚拟环境会依赖系统环境中的site packages，就是说系统中已经安装好的第三方package也会安装在虚拟环境中，

如果不想依赖这些package，那么可以加上参数 

```
--no-site-packages
```

建立虚拟环境

即变成了：

```
root@kali:/recall/code# virtualenv test_env --no-site-packages
New python executable in test_env/bin/python
Installing setuptools, pip...done.
root@kali:/recall/code# 
```

三、启动虚拟环境

创建成功后，会在当前目录下生成对应的目录文件。

```
root@kali:/recall/code# ls -l test_env/
总用量 16
drwxr-xr-x 2 root root 4096  4月 29 20:03 bin
drwxr-xr-x 2 root root 4096  4月 29 19:58 include
drwxr-xr-x 3 root root 4096  4月 29 19:58 lib
drwxr-xr-x 2 root root 4096  4月 29 19:58 local
root@kali:/recall/code# 
```

我们先进入到该目录下：

```
cd test_env/
```

然后启动

```
root@kali:/recall/code/test_env# source ./bin/activate
```

启动成功后，会在前面多出 test_env 字样，如下所示

```
(test_env)root@kali:/recall/code/test_env# 
```

四、使用测试

```
(test_env)root@kali:/recall/code/test_env# pip install requests
Downloading/unpacking requests
  Downloading requests-2.2.1-py2.py3-none-any.whl (625kB): 625kB downloaded
Installing collected packages: requests
Successfully installed requests
Cleaning up...
(test_env)root@kali:/recall/code/test_env# python
Python 2.7.3 (default, Jan  2 2013, 13:56:14) 
[GCC 4.7.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import requests
>>> 
>>> response = requests.get("http://www.baidu.com")
>>> response.status_code
200
>>> 
```

五、退出虚拟环境

```
deactivate
```
