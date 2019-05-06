# GPU+tensorflow安装

## 1、安装anaconda

​     使用清华的镜像包：https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/
或者：https://mirrors.ustc.edu.cn/anaconda/archive/
```
使用命令：bash Anaconda2-5.0.0.1-Linux-x86_64.sh
```
然后激活一下
```
使用命令：source .bashrc
```
## 2、查看ubuntu版本、GPU型号

```
1）cat /proc/version
```

- ubuntu-16.04.10

```
2）nvidia-smi
```

- GTX 1080

## 3、安装cuda和cudnn 

参考：https://blog.csdn.net/m0_37477175/article/details/81326665

CUDA，NVIDIA官网：https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604&target_type=deblocal

- 安装CUDA Toolkit 9.0 和cuDNN 7.0 ：

  ```
  wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_9.0.176-1_amd64.deb
  wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/libcudnn7_7.0.5.15-1+cuda9.0_amd64.deb
  wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/libcudnn7-dev_7.0.5.15-1+cuda9.0_amd64.deb
  wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/libnccl2_2.1.4-1+cuda9.0_amd64.deb
  wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/libnccl-dev_2.1.4-1+cuda9.0_amd64.deb
  sudo dpkg -i cuda-repo-ubuntu1604_9.0.176-1_amd64.deb
  sudo dpkg -i libcudnn7_7.0.5.15-1+cuda9.0_amd64.deb
  sudo dpkg -i libcudnn7-dev_7.0.5.15-1+cuda9.0_amd64.deb
  sudo dpkg -i libnccl2_2.1.4-1+cuda9.0_amd64.deb
  sudo dpkg -i libnccl-dev_2.1.4-1+cuda9.0_amd64.deb
  sudo apt-get update
  sudo apt-get install cuda=9.0.176-1
  sudo apt-get install libcudnn7-dev
  sudo apt-get install libnccl-dev
  ```

- 重启，若机器无法重启，则参考资料2

- nvidia-smi查看显卡信息

- 设置环境 添加 PATH and LD_LIBRARY_PATH 到 .bashrc 的最后:

```
export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}12
```

- 使用命令source .bashrc

## 4、安装tensorflow

```
1) conda create -n tensorflow python=2.7
2) source activate tensorflow

3) pip install tensorflow-gpu==1.5 # 安装 gpu 版本的 tensorflow 和 keras

4）source deactivate

5）source activate tensorflow 

6）import tensorflow as tf
   hello = tf.constant('Hello, TensorFlow!')
   sess = tf.Session()
   print(sess.run(hello))
```



