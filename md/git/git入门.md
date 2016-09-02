# git入门
## 1.安装
安装程序下载地址：http://github.com
## 2.配置
### 2.1 用户与邮箱

git是分布式版本控制系统，使用用户名和邮箱地址唯一标识，来管理仓库.
````
git config --global user.name "用户名" --设置用户名
git config --global user.email "邮箱地址" --设置邮箱地址
git config user.name  --查看用户名信息
git config user.emial  --查看邮箱信息
git config --list  --查看配置参数信息
````
### 2.2 秘钥生成
github提交与下载代码需要本机授权秘钥，生成的秘钥需要在github ssh管理单元添加本机的公共秘钥，否则无法上传下载代码。
生成的秘钥在本机用户.ssh 目录下，id_rsa 是私钥，不可泄露，id_rsa.pub  是公钥，用于在github ssh 中添加管理。
````
ssh-keygen -t rsa -C "邮箱地址"
注：输入命令，3个回车，密码不用输入。
````
## 3. 创建本地仓库
````
第一步：mkdir test 创建本地文件目录。可以手工创建，不一定非使用命令创建。
cd test 进入test目录
pwd 显示当前目录
第二步：git init 初始化本地仓库，在当前目录下，会生成一个.git 目录 ，目录默认是隐藏。
此文件用于管理仓库版本信息。 此步骤必不可少。
````
## 4. 仓库工作流程
http://fsjoy.blog.51cto.com/318484/244826/
![工作流程](http://img1.51cto.com/attachment/200912/200912171261023712254.png)