# git指南

## 一、前言

> git是分布式版本控制系统，用来控制文件版本的。当每次修改很多文件后，使用git提交修改，git就会创建一个项目版本记录所有的文件，我们可以通过这个版本记录看到不同版本间的差异，更重要的是可以随时回退到某个提交时的状态------而最大的好处是——其他人也可以同时修改。

## 二、git环境搭建

略，环境搭建完成后，进入需要创建git仓库的文件夹的终端，即可通过输入git指令完成特定的git操作。

## 三、git基本语法

> 额外常见shell语法:
> pwd(print word directory):显示当前终端会话所在目录的位置.
>
> ls(list file):显示当前目录下的所有文件.
>
> cd(change directory):切换目录.     cd ..进入上一级    cd .\下一级
> 

`git version`输出git版本号,检查git是否安装

//config配置 --global全局  user用户 

```git
git config --global user.name "123zengyue"
git config --global user.email "3229587344@qq.com"
```

> Q:请问这里的邮箱和用户名需要使用github上对应的用户名和邮箱吗？
> A:不用，只是做个标记，看是谁提交的，你随便打都没问题

### 3.1 新手三步（代码提交）

//init:初始化

```git
git init
```

 	git init会在当前目录初始化,创建一个.git隐藏文件夹.这个文件夹里会保存我们文件的每个git版本记录和变化。

​	初始化后,文件其实还没有被记录,我们需要使用命令`git add`把此时的初始化后的文件加入git版本控制系统中。

// add:添加

```git
git add <文件名>
```

​	git add后面要加文件名,git add . 是添加当前目录的全部文件.

​	添加后git只是暂时保存,还不会保存提交记录.我门还需要使用`git commit`命令进行提交，把刚刚暂时保存的变更提交固定成一个版本。

//commit：提交

```git
git commit
```

git commit后会打开**vim终端编辑器**，在这里我们需要写提交说明：

* /i进入编辑模式，写几行说明
* 写完说明后按esc退出编辑模式，然后输入`:wq`保存并退出回终端目录

但是vim操作及其反人类，我们可以通过`git commit -m "第n次提交"`来快速提交并附带提交说明

```git
git commit -m "第n次提交"
```

**注意**：若遇到企业级国际级项目，commit的提交说明最好符合git commit风格规范：`fix(test):change content`，在此仅举一例。自己的项目无所吊谓。

//log 日志
我们还可以使用`git log`查看提交日志

![image-20241122191102221](D:\zengyue\Blog\source\images\image-20241122191102221.png)

commit 后面的大串黄色字符 是这次提交的随机id作为唯一标识

> 新手三步大概就是这样，注意使用一次git init初始化一次就够了，后续的提交更改只用 git add .    然后git commit就行了，最好 能养成每次commit之后使用git log查看提交日志以检查提交是否成功 的好习惯。

### 3.2 版本回退

首先`git log`查看所有的提交日志信息

然后选择要回退的版本，复制其commit id（上面提到的黄色字符串）

然后输入`git reset --hard commitid`

//reset:重置      --hard:重置模式的一种（硬重置，即覆盖所有变更）此外还有soft模式和默认的mixed模式，在此不作过多介绍。

```git
git reset --hard  <commitid>
```

**但是 git reset虽然回退了，但是把后面的提交日志都清空了**（还可以使用git reflog看到并切换）

为了在不同的版本之间 来回切换，我们在这里引入分支（branch）的概念。、

### 3.3 branch分支

#### 分支创建

所谓分支就是把当前主分支上的版本复制一份，我们可以在本来 要coomit的时候使用`git branch <分支名>`

```git
git branch  2.0
```

上述代码等同于`git commit -m "第二次提交"`，但使用git branch新建了一个分分支，而git commit是在原有分支上进行修改的提交。

#### 分支查看

```git
git branch -a
```

查看当前 Git 仓库的所有分支，`-a` 选项表示显示所有的本地分支和远程分支。

#### 分支选择

//checkout

```git 
git  checkout <分支名 >
```

我们可以选择某条特定的分支，在这条特定的分支上提交回退版本。

#### 分支合并

> branch的作用不仅仅是切换版本，更重要的是开发 者可以 在主流上继续写代码，也可以在支流上同时写，然后在某天利用git merge把主流直支流合并在一起。

//merge:合并 

```git
git checkout master
git merge <分支名>
```

合并可以有效帮助团队开发，换言之，一个团队开发项目离不开分支。

![image-20241122201425489](D:\zengyue\Blog\source\images\image-20241122201425489.png)

每人branch出自己的新分支，写自己单独负责的功能，最后merge合并在一起

![image-20241122201558390](D:\zengyue\Blog\source\images\image-20241122201558390.png)

这就好比与大家把1.0版本文档复制一遍，然后大家在自己复制得到的副本上写自己复制的功能模块1、2、3、4...最后admin管理员把每个人的功能模块黏贴到一起，最终另存为文档1.1新版本，这就是merge。

## 四、团队协作

团队协作肯定不能在一个电脑上，不能只让一个本地电脑 存储 git仓库。

这时就需要找一个服务器来搭建git仓库服务，比如github和gitee这种方便的公共git仓库，，说白了就是个符合git操作的网盘 。

### github

先 new repository创建一个新仓库，选择public公开。选择添加Readme文件。（或者稍后手动git commit提交也可以）

```git
git init
git add.
git commit -m "first commit"
git branch -M main  //创建一个main分支，并把主分支切换成main
git remote add origin xxx//添加一个远程仓库地址xxx,相当于给这个git项目设置一个网盘地址
git push -u origin  main
```

![image-20241122205247857](D:\zengyue\Blog\source\images\image-20241122205247857.png)

![image-20241122205157622](D:\zengyue\Blog\source\images\image-20241122205157622.png)

![image-20241122205208071](D:\zengyue\Blog\source\images\image-20241122205208071.png)

> 这里终端可能会提示你输入github账户的邮箱以及密码。按要求输入即可

再次刷新github仓库页面即可 看到上传成功

![image-20241122205629396](D:\zengyue\Blog\source\images\image-20241122205629396.png)