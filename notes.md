## Git： 最先进的分布式版本控制系统

### 1  安装

自报家门： --global 该机器上所有Git仓库都会是这个配置

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

### 2  初始化

- 声明：所有版本控制系统追踪的都是文件的改动。

- Microsoft的Word格式是二进制，图片也是。
- 千万不要使用Windows自带的**记事本**编辑任何文本文件，原因是Microsoft开发记事本的团队使用了一个非常弱智的行为来保存UTF-8编码的文件，他们自作聪明地在每个文件开头添加了0xefbbbf（十六进制）的字符。

### 3  基本命令

```
git init

git add <filename> 
git add .  //可以一次性添加所有改动.

git commit -m "xxx"

git status：掌握仓库状态
git diff ：查看修改信息

git log：查看历次提交的信息
git reflog   //记录每一次命令

HEAD：当前版本		HEAD^：上一个版本		HEAD^^：上上个版本
git reset --hard HEAD^ //回退到上一个版本

```

### 4 工作区和暂存区

#### 4.1 工作区：我们电脑里的目录，例如learngit文件夹

#### 4.2 版本库：.git隐藏目录

​	Git的版本库里存了很多东西:

- 称为stage的暂存区
- Git自动创建的第一个分支`master`
- 指向`master`的指针HEAD

![git-repo](https://www.liaoxuefeng.com/files/attachments/919020037470528/0)

​	git add负责将文件放入暂存区，commit将暂存区内容提交到当前分支

### 5  管理修改

- 声明：Git追踪的是修改，提交暂存区的内容。

  `git diff HEAD -- readme.txt`命令可以查看工作区和版本库里最新版的区别

#### 5.1 撤销修改

- 丢弃工作区修改：git restore \<filename>

​	一种是`readme.txt`自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

​	一种是`readme.txt`已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

​	总之，就是让这个文件回到**最近一次`git commit`或`git add`**时的状态。

- 丢弃暂存区修改：git restore --staged \<filename>
- 丢弃版本库修改：版本回退（git reset --hard commit_id）

#### 5.2 删除文件

- 声明：删除也是一种操作，与修改内容性质是一样的。
- git restore <filename> ：版本库内容替换工作区版本
- git rm <filename> ：从版本库删除，之后commit，该条指令与git add的性质是一样的。

### 6  远程仓库

- 声明：将电脑的公钥加入GitHub的SSH key中。

#### 6.1添加远程库

- 创建新仓库:

  ​	git init 

  ​	git remote add origin /http/

- 使用已有的仓库

  ​     git remote add origin /http/

- 注:

  git branch -M main     

  -m / -M Means: Rename

[解决 Github port 443 : Timed out - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/636418854)

```bash
git config --global http.proxy http://127.0.0.1:7890 
git config --global https.proxy http://127.0.0.1:7890
```

这两句话设置了git的网络代理，告诉git当它们要进行http或https连接时，应当通过指定的代理服务器进行连接。这里，代理服务器位于本地主机，监听端口在7890上。

Git客户端默认使用的http/https连接端口是80/443。



GitHub报错：unable to access. Failed to connect to github.com port 443 after ...ms。

