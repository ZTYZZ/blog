# git简介
git 是好的分布式版本管理系统。
![用了git之前](http://upload-images.jianshu.io/upload_images/271046-b7d4c26a3765e8fa?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![用了git之后](https://upload-images.jianshu.io/upload_images/271046-c0ecffad1f7a591d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 集中式和分布式

集中式：
集中式版本控制系统，见名之意，版本库放在中央服务器的。
![](http://upload-images.jianshu.io/upload_images/271046-eee0a34d56fcf605?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

工作的过程就是，从版本库中拿出文件-->干活-->新版本推送到服务器。

缺点：
1. 由于是集中式，所以要有足够的带宽。如果同时有多个人从服务器取东西，那岂不是很慢。

2. 如果中间的服务器坏了，那么所有人都需要等着，什么都不能干。

## 分布式
分布式没有所谓的“中央版本服务器”。每个人的电脑上面都是一个完整的版本库，所以他的好处显而易见。
1. 不必联网
2. 安全性更高。某一人的电脑坏了不要紧，直接拿别人的就好了

需要注意的是，很少在两个人之间推送版本库的修改，你们两个不在同一个局域网，或者某一个人根本就没开机。因此。分布式管理器还需要有一台充当“中央服务器”电脑，这个服务器仅仅用来方便交换大家的修改。
![](http://upload-images.jianshu.io/upload_images/271046-4e6983d65bb00b0f?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# git安装
最初只能linux unix下安装，后来移植到了windows上，所以都可以用了。

## 安装过程：
首先试着输入`git`查看是否已经存在。
我的机子上已经安装有了，so开心到飞起。。。

重要的一步，要让git知道你是谁！！
```
git config --global user.name “Your Name"
git config --global user.email "email@example.com"
```
--global:这台机器上所有的Git仓库都会使用这个配置。

# 版本库
repository.你可以把它理解成一个目录，但是和普通目录不同的是，这个目录下的所有文件都被git管理了，每一个文件的修改，git都能跟踪到，并且可以还原。

1. 在本地创建一个版本库：
```
mkdir learngit
cd learngit
pwd
```
2. 用git管理
```
git init 
```
多了一个`.git`文件夹，这个是用来跟踪版本库的，不要改，也不要删，不然就破坏了git仓库。
如果看不到，则是隐藏掉了，以`.`开头的文件夹，会隐藏掉。
使用 
```
ls -ah
```
来观察。
【注】版本库只能追踪文本文件，不能追踪类似图像文件、视频文件的二进制文件。他只能知道由2k变成了4k,不能也无法知道里面哪里更改了。

3. 创建一个`readme.txt `
```
touch readme.txt
vim readme.txt
```
也可以直接就是用
```
vim readme.txt
```

添加内容为：
```
Git is a version control system.
Git is free software.
```
4. 将文件加到git中，
```
git add readme.txt
```
5. 将文件提交到git仓库
```
git commit -m “wrote a readme file”
```
```
[master （根提交） 5e37b12] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```

-m选项是message的意思，后面跟上本次提交的说明，这样以后就好方便找到记录。
# 常用命令
## 查看状态
`git status`` 查看仓库的当前状态
```
On branch master 位于分支 master
Changes not staged for commit: 尚未暂存以备提交的变更：
  (use "git add <file>..." to update what will be committed) （使用 "git add <文件>..." 更新要提交的内容）
  (use "git checkout -- <file>..." to discard changes in working directory)
 （使用 "git checkout -- <文件>..." 丢弃工作区的改动）

    modified:   readme.txt 修改：     readme.txt

no changes added to commit (use "git add" and/or "git commit -a") 修改尚未加入提交（使用 "git add" 和/或 "git commit -a"）
```
`git diff` 查看修改内容
`git diff HEAD -- readme.txt`命令可以查看工作区和版本库里面**最新版本**的区别：
```
git diff readme.txt
diff --git a/readme.txt b/readme.txt
index 46d49bf..9247db6 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
 Git is free software.
```
`git log`查看每次提交commit的内容
`git log --pretty=oneline`在一行显示
```
git log
commit bfbf4449ea7f806fc646ee209af3c8451bc27e8f
Author: Hilay <1528723869@qq.com>
Date:   Tue Apr 24 20:59:57 2018 +0800

    append distributed

commit 5e37b12776c0e6cef0e0696bcef670dae901067c　# 这个是 `commit id（版本号）` 由于是很多人协作，所以需要解决冲突问题。
Author: Hilay <1528723869@qq.com>
Date:   Tue Apr 24 20:47:23 2018 +0800

    wrote a readme file
```
##版本回退
`git reset --hard HEAD^`回退到上一版本 HEAD^^上上版本 HEAD~100往上100个版本
`git reset --hard xxxx `其中xxxx是版本号，只需写出几位git就会自己去找。

`git reflog`git用这个命令来记录每一个记录，包括版本回退，和`git log`还是有区别的，后者直接会退到版本回退的位置。
## 撤销修改
`git checkout -- readme`将工作区的修改全部撤销。换句话说，就是撤销到最近一次 `git commiit`或`git add `的状态。
`git reset HEAD file`将把暂存区的修改撤销掉。

## 删除文件
1. 确实需要从版本库中删除文件。 
```
git rm test.txt
git commit -m "remove test.txt"
```
2. 误删
```
git checkout -- reame.txt  
```
使用以上命令恢复.
## 小节
```
其实reset HEAD -- file 命令就是从已提交的分支上面将文件取回
而 checkout -- file 是将暂存区的内容放到工作区.
```

# 原理分析
[点击这里](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013745374151782eb658c5a5ca454eaa451661275886c6000)

# 远程仓库
git 最早只有一台机器有一个原始版本库,此后别的机器可以克隆
实际用一台电脑充当服务器的角色,没人从这个"服务器"仓库克隆一份到自己的电脑上.
我们没有必要自己搭建一台运行git的服务器,用Github就好了这个网站就是提供Git仓库托管服务的.
## Github 设置.
本地GIt仓库和GitHub仓库之间是通过SSH加密传输的.所以需要设置key,相当于将GitHub账号绑定认证到本地仓库

### 创建SSH Key
```
ssh-keygen -t rsa -C "youremail@example.com"
```
一路回车,就发现创建了`.ssh`文件夹,在`.ssh`文件夹下有`id_rsa(私钥)`和`id_rsa.pub(公钥)`

将这个绑定到github上.ok

## 开始github推送
在github创建一个远程库.
在本地仓库下运行
 ```
git remote add origin git@github.com:..../....git
```
origin 是远程库的名字.
使用`git push `命令推送到github上面.
```
git push -u origin master
```
由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。
##从远程仓库克隆
`git clone`命令

