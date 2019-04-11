
# linux相关笔记

### 文件目录类终端命令
1. 建立目录：
`mkdir 目录名`
2. 删除目录：
`rmdir 目录名`
3. 无条件删除子目录：
`rm -rf 目录名`
4. 删除文件：
`rm 文件名`
5. 进入当前所在目录中包含的下一级目录：
`cd 目录名`
6. 进入home：
`cd ~`或`cd`
7. 进入上一级：
`cd -`或`cd ..`
8. 查看自己所在目录：
`pwd`
9. 查看当前目录大小：
`du`
10. 查看目录文件列表：
`ls -l`  
其中：蓝—目录，绿—可执行文件，红—压缩文件……
11. 查看文件夹下的目录：
`ls`
12. 查看包括隐藏文件(夹)的目录：
`ls -a`
13. 浏览文件：
`more 文件名`或`less 文件名`
14. 复制、移动、重命名：
	- 复制文件：
	`cp 源文件 目标目录`
	- 复制文件夹：
	`cp -r 源文件夹 目标目录/`
	- 移动文件/文件夹：
	`mv 源文件(夹) 目标目录`
	- 重命名文件/文件夹：
	`mv 旧文件名 新文件名`
	- [命令中各选项的含义](http://blog.sina.com.cn/s/blog_6db312f101017wxg.html)
15. 查找文件：
	- find指令：
	`find ~/ -name linux.md`或`find ~/ -name *.md`  
	[find参数](https://blog.csdn.net/comefay2/article/details/79908755)
	- locate指令：
	`locate linux.md`会将所有文件名中包含linux.md的文件路径列出，当删除或添加文件后，需要用`sudo updatedb`更新locate。
	- which指令：
	`which python`寻找可执行文件的路径
	- [ubuntu16.04查看软件的安装位置](https://blog.csdn.net/WxyangID/article/details/53114276)
16. 链接：
	- 硬链接与软链接：[区别]，一般用软链接。
	- 建立硬链接：
	`ln 来源文件 链接文件`
	- 建立软链接：
	`ln -s 来源文件 链接文件`
[区别]:https://www.cnblogs.com/ylan2009/p/4287929.html
17. 新建文件：
`touch 文件名.文件类型` 例：`touch test.txt`
18. 打开文件：
`gedit 文件名.文件类型` 例：`gedit test.txt`
19. cat：
	- 在屏幕上显示文件m1的内容：
	`cat m1` 例：`cat ~/notes/linux.md`
	- 同时显示文件m1和m2的内容：
	`cat m1 m2`
	- 将文件m1和m2合并后放入文件file中：
	`cat m1 m2 > file`
	- [其他功能](https://blog.csdn.net/hubz131/article/details/79827117)
20. 对一个指令进行解释：
`man 指令名` 例：`man ln`
21. 查看ip地址：
	- 查看自己的ip：
	`ifconfig` (windows：`ipconfig`)
	- 查看局域网呢所有电脑ip：
	`arp-a`
22. `xdg-open`：
根据系统的默认打开方式打开一个文件，比如图片、音频等。
例：`xdg-open ~/notes/linux.md`
23. 通过命令打开图片：
`eog 路径`
24. 全局查找内容：
`prep -r -e "内容"`
25. 安装.deb文件：
`sudo dpkg -i xxx.deb`

### ubuntu下安装anaconda
[网址](https://blog.csdn.net/zhdgk19871218/article/details/46502637)

### 在终端中ctrl+c与ctrl+d
`ctrl+c`：外部中断；`ctrl+d`：shut down。

### 显示/隐藏隐含文件
`ctrl+h`在任意文件夹中可使用。

### 启用超级用户模式
- `su - root`
- `sudo passwd`：可以更改密码。
- 进入超级用户模式之后，默认位置在`/root`，如需进入home，应`cd /home/shiwb`

### ubuntu删除或移动带锁文件夹或文件的方法
- 文件夹右下带锁，说明该文件只能读尔不能操作，要对它进行操作时提示权限不够。
- 解决方法：`sudo chmod -R 777 路径(文件夹或文件)`执行该条命令后，锁消失。

### ssh传送文件

```
scp -r '~/Desktop/Literature Review' tangliang@192.168.2.200:~/Documents`
```

### git教程
- [廖雪峰](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
- 批量添加文件到仓库：
`git add *`
- 关联git远程库：（实验室的gitlab只能使用http方式）
	1. 使用http方式：
	`git remote add origin http://10.60.100.57/STONE17/notes.git`  
	使用服务器搭建的gitlab时，只能使用http方式
	2. 使用ssh方式：
	`git remote add origin git@github.com:michaelliao/learngit.git`
- [git 本地仓库同时推送到多个远程仓库](https://blog.csdn.net/fox9916/article/details/79386169)  
备注：第一个远程仓库名一般为origin，我若关联第二个远程仓库，则远程仓库名为shiwb。
- [git 查看单独一个文件的修改历史](https://blog.csdn.net/ahjxhy2010/article/details/80047553)  
`git log -p 文件名`：可以显示每次提交的diff。
- 查看某一个文件的diff：`git diff 文件名`。
- 在add之前删除：
	1. 所有文件中所做的修改：`git checkout .`
	2. 某类文件所做的修改：`git checkout -- *.cpp`
	3. 某个文件所做的修改：`git checkout -- note.md`

### ubuntu下打不开windows磁盘
[解决办法](https://zhidao.baidu.com/question/2118100971415421427.html)

### conda与pip关系
pip可以允许你在任何环境中安装python包，而conda允许你在conda环境中安装任何语言包（包括c语言或者python）。

### 登录服务器
- 打开终端，输入

```
ssh -p 252 tree@202.120.189.234
```
密码`tjark417`。
- 给服务器拷贝文件：   

```
scp -rP 252 ~/Downloads/DeblurGAN-master tree@202.120.189.234:/mnt/tree/shiwb/
```
其中，-r是复制文件夹下所有文件；-P是给出端口号252。
- 当使用服务器进行训练时，tensorflow会占用所有显卡内存，但只会用一块显卡进行计算，需要使用`CUDA_VISIBLE_DEVICES`进行限制，具体见python.md。

### 查询NVIDIA显卡运行状况
- `nvidia-smi` 显示一次当前GPU占用情况
- `nvidia-smi -l` 每秒刷新一次并显示
- [显示表格中各栏的意思](http://www.cnblogs.com/ranxf/p/9412242.html)

### 搭建独立的虚拟环境
- [virtualenv](https://blog.csdn.net/qq_33371343/article/details/78047853)
- 退出虚拟环境时，使用`deactivate`或`source deactivate 虚拟环境名`

### 安装搜狗输入法
[方法](https://blog.csdn.net/singleyellow/article/details/77448246)

### 安装chrome浏览器
[方法](http://www.ubuntuchrome.com/)。翻墙，直接安装。

### 安装lantern
1. 登录`https://github.com/getlantern/lantern`获取最新版蓝灯安装包
2. `sudo apt-get gdebi`
3. `sudo gdebi lantern-installer-64-bit.deb`
4. 使用时直接在终端中输入`lantern`

### 因为proxy原因断网的解决方法
`system settings→network→network proxy->none`

### 安装tensorflow gpu版本步骤
- [方法](https://www.linuxidc.com/Linux/2016-11/137561.htm)  
注意：目前的搭配为cuda8.0+cudnn6.0，tensorflow版本为1.3。  
注意：如果已经单独安装NVIDIA驱动，在安装cuda时就**不要安装驱动**了。
- cudnn6.0下载命令：
`wget http://developer.download.nvidia.com/compute/redist/cudnn/v6.0/cudnn-8.0-linux-x64-v6.0.tgz`
- [cuda各版本下载地址](https://developer.nvidia.com/cuda-toolkit-archive)
- [cudnn各版本下载地址](https://developer.nvidia.com/rdp/cudnn-download)
- [NVIDIA驱动安装教程](https://blog.csdn.net/u014797226/article/details/79626693)

### markdown文本格式使用
- [使用语法1](https://blog.csdn.net/zhaokaiqiang1992/article/details/41349819)
- [使用语法2](https://www.cnblogs.com/liugang-vip/p/6337580.html)
- [在线.md文件编辑器](http://mahua.jser.me/)
- [Remarkable：.md文档编辑器](https://remarkableapp.github.io/linux.html)

### python安装cv2
- 直接`pip install opencv-python`安装的是pip2的
- 若要[在anaconda中使用](https://blog.csdn.net/jacke121/article/details/79512586)

### ubuntu设置开机默认启动顺序
[方法](https://jingyan.baidu.com/article/b7001fe17485950e7282ddae.html)

### ubuntu安装matlab
- [方法](https://www.cnblogs.com/Amedeo/archive/2018/06/03/9129925.html)
- [给Matlab 建立快捷方式](https://www.linuxidc.com/Linux/2011-01/31632.htm)
- 在使用过程中，matlab无法画图并出现Resolving low-level graphics issues in MATLAB的提示，[解决方案](https://ww2.mathworks.cn/matlabcentral/answers/157894-resolving-low-level-graphics-issues-in-matlab)：  
在matlab的command window输入`opengl('save','software')`

### 安装labelimg
##### anaconda3版安装
1. `conda install pyqt=5`
调用时使用`import PyQt5`
2. [下载labelimg](https://github.com/tzutalin/labelImg)
3. `pyrcc5 -o resources.py resources.qrc`
4. 进入存放目录下并`python labelImg.py`

##### [pip版安装]
[pip版安装]:https://www.cnblogs.com/andre-ma/p/9116447.html

### 几个从youtube下载视频的在线网页
1. [ClipConverter](https://www.clipconverter.cc/)
2. [savefrom.net](https://en.savefrom.net/)

### ubuntu搭建jdk1.8运行环境
- [教程](https://blog.csdn.net/smile_from_2015/article/details/80056297)
- [通过update-alternatives切换jdk版本](https://blog.csdn.net/smile_from_2015/article/details/80057169)

##### 使用update-alternatives标注优先级
- update-alternatives是ubuntu系统中专门维护系统命令链接符的工具，通过它可以很方便的设置系统默认使用哪个命令、哪个软件版本。
- 查看当前系统存在的jdk及优先级：

```
update-alternatives --display java
```

### 安装Clang & Clang版本切换
- [教程](https://blog.csdn.net/DumpDoctorWang/article/details/84567757)

### update-alternatives切换软链接
- 安装某东西某版本的“快捷方式”。例：（安装java jdk）  

```
sudo update-alternatives --install /usr/bin/java  java  /usr/lib/jdk/jdk1.7.0_131/bin/java 400
```
最后的400代表优先级。
- 查看打印当前的版本。例：（以clang为例）  

```
clang --version
clang++ --version
```
- 查看所有优先级。例：（以java为例）  

```
update-alternatives --display java
```
- 切换版本。例：（以clang为例）  

```
sudo update-alternatives --config clang
```
然后出现提示：

```
There are 2 choices for the alternative clang (providing /usr/bin/clang).
 Selection Path Priority Status
  ------------------------------------------------------------ 
  * 0 /usr/bin/clang-4.0 2 auto mode 
  1 /usr/bin/clang-3.8 1 manual mode 
  2 /usr/bin/clang-4.0 2 manual mode 
  Press <enter> to keep the current choice[*], or type selection number:
```
然后输入想切换版本的版本序号（第一列），如3.8输入1，然后回车，就切换为3.8版本了。

### vim的安装与使用
##### 1. 安装
- 在终端输入：

```
sudo apt install vim
```
- 安装之后测试：

```
vim a.txt
```

##### 2. 使用
- [使用介绍](https://blog.csdn.net/lixinghua666/article/details/82289809)

### sublime更改默认配置（tab缩进等）
- 打开Preferences->Browse Packages
- 打开User/Preferences.sublime-settings，更改其中内容。

### github上下载单文件（夹）
1. 单文件：  
github打开文件后右键单击Raw，然后选择save link as。
2. 单文件夹：

```
sudo apt install subversion
svn checkout https://github.com/gaoxiang12/slambook2/trunk/ch2/CMakeLists.txt 
#原地址是https://github.com/gaoxiang12/slambook2/blob/master/ch2/CMakeLists.txt，将/blob/master替换为/trunk。
```

### 安装opencv
- [步骤](https://blog.csdn.net/cocoaqin/article/details/78163171)
- [opencv官网发布页](https://opencv.org/releases.html)：从中下载sources版本。

##### [在对opencv进行cmake时卡在ippicv下载的解决方法]
[在对opencv进行cmake时卡在ippicv下载的解决方法]:(https://blog.csdn.net/orDream/article/details/84311697)

- [手动下载ippicv的地址](https://download.csdn.net/download/ordream/10797348)

### 使用cmake编译时与anaconda冲突的问题
- [很有用的帖子](https://github.com/pism/pism/issues/356)
- 原因：anaconda在.bashrc中添加了路径，使得执行python以及c++程序时都会优先在anaconda中调用库函数，导致编译失败。
- 解决方法：在.bashrc中增加了一个NOCONDA_PATH路径，每次在cmake的时候都需要输入：  

```
PATH=$NOCONDA_PATH cmake ..
```
这样便可以不从anaconda下面调用库函数，从而解决问题。

### U盘启动安装Ubuntu16.04
- [教程](https://blog.csdn.net/lingyunxianhe/article/details/81415675)
- 在dell G3的安装过程中，如果使用的SATA OPERATION为RAID，将会导致在安装时看不到磁盘，因此需要设置成ACHI安装。但在安装完毕后，系统无法正常进入windows，[解决方法]是使用安全模式登入windows，使其自检修复。
[解决方法]:(https://blog.csdn.net/hikkilover/article/details/82289070)

### GIT 学习

* [教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013743858312764dca7ad6d0754f76aa562e3789478044000)

