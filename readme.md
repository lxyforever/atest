
# 个人博客搭建完全教程

## 1.为什么要搭建个人博客

## 2.如何搭建个人博客

## 3.环境准备

### 3.1 本地环境搭建

  ************
  本节完成本地 `git` 及 `Node.js` 的安装，电脑上已配置过可跳过本节。
  ************

* 安装 `git`  
  
  访问 [git官网][1] 来下载 `git` 安装包：  
![git官网点击Download下载git安装包][2]  
根据你的平台选择不同版本。本教程以win为例：  
![选择合适的安装版本][3]
安装包下载完成后一路默认即可完成 `git` 的安装：
![一路火花带闪电NNNNext][]  
ps：什么？你之前从未用过 git？那还不赶紧体验一下可能是这个星球目前为止**最好用最伟大的版本控制软件**？附上两个学习链接：  
[廖雪峰老师的git教程][5]  易上手易操作！半小时入门首选！  
[Pro Git的免费在线版本][6]  一整本讲 git 的书！看完完全掌握了 git！

[1]:https://git-scm.com
[2]:https://github.com/lxyforever/atest/raw/master/IMG/img/1.PNG
[3]:https://github.com/lxyforever/atest/raw/master/IMG/img/2.PNG
[4]:https://github.com/lxyforever/atest/raw/master/IMG/img/3.PNG
[5]:https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000 "廖雪峰老师的 git 教程"
[6]:https://git-scm.com/book/zh/v2 "Pro Git的在线版本"

* 安装 `Node.j

  进入[Node.js 官网下载页面][7]下载对应系统版本的 Node.js 的安装包，双击打开一路默认即可完成 `Node.js` 的安装：
  ![下载对应版本][8]  
  一路默认点击 next 即可完成安装：  
  ![一路next][9]  

  [7]:http://nodejs.cn/download/  "Node.js 官网下载页面"
  [8]:https://github.com/lxyforever/atest/raw/master/IMG/img/4.PNG  "我选择的64bit安装版本"
  [9]:https://github.com/lxyforever/atest/raw/master/IMG/img/5.PNG  "Node,js安装包打开界面"

### 3.2 注册Github账号并配置ssh key
  
* 注册 Github 账号
  进入 [Github 官网][10] 注册账号并登入，记住你的 `email`及`username`字段：  
  ![注册Github账号][11]
  点击右上角的 `+` 号并选择 `New repository` 新建一个空仓库，以后的hexo博客代码将会托管在这个库中：  
  ![新建远程库][12]
  新建时需要注意：
  1.`Repository name` 字段格式**务必为**   `xxxxxxx.github.io`，其中xxxxxx为用户自取，推荐使用github账号的username以避免不必要的麻烦。  
  2.为你的库添加合适的描述文字。  
  3.其他配置保持默认即可，确认无误点击绿色 `Create repository` 按钮完成创建  
  ![几个注意的地方][13]

* 配置本地 git

  打开资源管理器，在电脑合适的位置新建空文件夹存放博客相关文件。例如我的文件夹路径为 `D:\lxy\blog`。
  在文件夹内右键，选择 `Git Bush Here` 打开 git bash：
  ![新建文件夹][14]  
  打开后大概是这样：
  ![Git Bash][15]  
  输入下列代码配置 `git` 的基本信息，其中 `your username` 和 `your email` 根据个人的基本信息填写，推荐与注册 github 时的个人信息相同： 

  >git config --global user.name "your username"  
  >git config --global user.email "your email"  

* 配置ssh key
  为了把本地仓库的内容上传到 Github，需要为你的电脑配置 ssh key。简单的理解 ssh key 就是你这台计算机的身份证明，github 能确认是不是你本人在操作你托管在 github 上的仓库而不是非法访问。配置步骤如下：
  1.打开bash，输入如下代码生成RSA，将邮箱更换为注册 github 时的邮箱：
  
  >ssh-keygen -t rsa -C "email@example.com"  

  输入后连按三下回车，进入 `C:\Users\Administrator\.ssh` 目录下，可以看到生成了三个文件：
  ![.ssh目录下][16]  
  使用文本编辑器打开图中标注的文件 `id_rsa.pub`，复制其中的内容（通常是一段乱码）。  
  
  进入 [github][10] 按如图所示进入设置界面：  
  ![github设置][17]
  
  按下图所示先点击右侧的 `SSH and GPG keys` 菜单进入 SSH 配置界面，再点击右上角绿色按钮 `New SSH key` 创建新的 SSH key：
  ![配置SSHkey][17]  （马赛克部分是我本来已经配置好的SSH key）

  title框中的内容随便填写，例如 `RSA_Home`。下面的 key 文本框复制入刚刚在 `id_rsa.pub` 文件中的乱码，检查后点击绿色按钮 `Add SSH key` 即可完成 SSH 配置。 
  ![配置SSHkey2][18]  

  配置完成后，在bash中输入：

  >ssh -T git@github.com

  (不用将git@github.com替换，只输入上述指令即可)检查SSH是否配对完成。如果bash显示：

  >Hi xxxxx(your user name)! You've successfully authenticated, but GitHub does not provide shell access.

  则表示SSH配对完成！至此，表示Github账号已经与个人电脑成功连接。

* 
[10]:https://github.com/ "Github官网"
[11]:https://github.com/lxyforever/atest/raw/master/IMG/img/6.PNG "注册Github账号"
[12]:https://github.com/lxyforever/atest/raw/master/IMG/img/7.PNG "新建远程库"
[13]:https://github.com/lxyforever/atest/raw/master/IMG/img/8.png "新建远程库2"
[14]:https://github.com/lxyforever/atest/raw/master/IMG/img/9.png "新建项目文件夹"
[15]:https://github.com/lxyforever/atest/raw/master/IMG/img/10.png "打开Git Bash"
[16]:https://github.com/lxyforever/atest/raw/master/IMG/img/11.png "本地生成ssh key"
[16]:https://github.com/lxyforever/atest/raw/master/IMG/img/12.png "github设置"
[17]:https://github.com/lxyforever/atest/raw/master/IMG/img/13.png "配置SSH key1"
[18]:https://github.com/lxyforever/atest/raw/master/IMG/img/14.png "配置SSH key2"

#### 