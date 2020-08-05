### python的好处.
人生苦短,我用python. 一句话概括完了.然后在学习python之前,我们得知道怎样安装python.不知道怎么安装,那怎么学习python呢.
### 源码安装
需要获取最新版的python. 直接从官网获取即可.[点击此处](https://www.python.org/downloads/). windows直接就是一个exe的执行文件.点击运行即可.如果是linux下.我们就可以直接通过下载源码的形式来编译安装了.既然是用源代码的方式. 那就得安装依赖. 方法如下.
```
// centos 
sudo yum install yum-utils
sudo yum-builddep python3
// or Fedora
sudo dnf install dnf-plugins-core
sudo dnf builddep python3
// or ubuntu,debian
sudo apt-get build-dep python3.6
```
安装完依赖过后.就可以开始我们正常的解压和安装了.
```
// .xz
xz -d Python-3.8.5.tar.xz
// .tgz
tar zxvf Python-3.8.5.tgz
```
然后直接进行编译安装即可.
```
cd Python3.8.5
./confguire // 检查环境依赖和配置信息.
make        // 开始编译
make install// 安装
```
就即可安装完成了.源码安装可以安装指定的模块. 可以自定义的参数，可以使用如下的命令来进行查看
```
./configure --help
``` 
### 软件源安装
当然,我们这里处理源码安装.在linux下还能进行yum源的方式来进行安装. 不过这种方式安装的python版本. 有些时候不是想要的版本. 但是胜在非常简单. 所以我们想要快速的安装的话可以参考以下的命令.
```
// centos 
yum install python3-3.6.8-13.el7.x86_64 // 或者其他版本
// ubuntu
sudo apt install python3.8
```
### python源更换
我们用到的所有的python的扩展跟我们php的扩展类似.php使用了pecl来安装扩展,python则使用了pip.当然.国外的东西在就下载速度而言,速度会比较慢.当然,不介意下载速度慢可以直接跳过这部分. 那我们就需要更换源的信息. 而更换源有两种方式. 1.临时更换,使用如下的命令即可
```
pip install -i https://mirrors.aliyun.com/pypi/simple/ 扩展包名
```
永久更换会稍微麻烦一下.使用如下命令.
```
echo '[global]
index-url = https://mirrors.aliyun.com/pypi/simple/
[install]
trusted-host = https://mirrors.aliyun.com' >> ~/.pip/pip.conf
```
注意如果没有文件夹.则需要创建文件夹.
```
mkdir -p ~/.pip
```
### virtualenv
当我们安装完成过后. 会发现出现很多的python.例如python,python2,python2.7,python3.6,python3.6m等等.为什么我们的环境会出现这种情况. 这是由于python的版本不向下兼容.python2的设计有很多缺陷. 以致于兼容python2是不可能完成的任务.so.所以就放弃了python2.弄了一个大版本python3.可以参考[这篇](https://www.zhihu.com/question/267005361).为了兼容.python的各个版本和扩展的关系.就出了virtualenv.用来创建单独的虚拟环境. 首先, 我们就先来安装virtualenv
```
pip3.8 install virtualenv
```
安装完成后,使用如下的命令即可创建并切换到一个虚拟环境
```
virtualenv -p /usr/local/bin/python3.8 venv  // -p 用来指定python环境.
source ./venv/bin/activate
```
这时, 我们就创建并进入到一个新的虚拟环境中了. 如何退出, 可使用如下命令.
```
deactivate
```
如果需要加载扩展包，可以在创建时增加--system-site-packages选项来创建. 详细参数可以参考[这篇文章](https://virtualenv.pypa.io/en/latest/cli_interface.html)
### pipenv
除了使用virtualenv外,还可以使用pipenv. 安装方式如下.
```
pip install pipenv
```
使用方式如下 
```
// 创建虚拟环境.
pipenv --python 3.8
// 激活虚拟环境.
pipenv shell
// 离开虚拟环境.
Ctrl + D(键盘) or exit
```
pipenv 创建后,所有的软件包安装和卸载,请使用pipenv来进行安装. 它能自动根据对应的环境来引入对应的包. 如果使用pipenv来创建虚拟环境,则会在当前目录下创建一个Pipfile的文件.这里面包含源的信息及python的其他版本声明.这意味着,每次更换虚拟环境后,你得手动更换源的信息.如果安装软件包过后,还会生成Pipfile.lock文件.用于统一扩展包的信息.其他具体的参数可以参考[这篇文档](https://pipenv.pypa.io/en/latest/)
### 最后
当我们解决完python的环境问题过后,就可以开始我们正式学习python了.

