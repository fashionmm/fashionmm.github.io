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

注：不设置用户名和邮箱地址，git无法提交，因为未建立关联，不知道是谁在提交。
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

- 工作区

    可以理解为未通过git add 操作的工作区域。
    通过 git add 命令将文件添加到暂存区。
    git add '文件名'
    git add -A 把当前目录下所有的文件都添加到暂存区域
    git status 查看修改后状态

- 暂存区

    暂存区是工作区与历史库之间的“过渡”，起过渡作用。保护工作区、历史区。
    通过git commit 命令添加到历史区。或者准确点说是当前分支。
    git commit -m '备注信息'
    git commit -a -m '备注信息' 添加文件到缓存区，并提交到历史库

- 历史区

    存放历史版本。
    通过git log 查看历史状态

## 5. git diff
### 5.1 工作区与暂存区
````
 git diff  查看工作区与暂存区的区别，此命令后不带参数
````
### 5.2 暂存区与历史区
````
git diff --cached
git diff --staged
暂存起来的数据和之前提交到历史区的数据之间的差异。
````
### 5.3 工作区与历史区
````
git diff HEAD  工作区与HEAD之间的差别
````

## 6. 撤销
### 6.1 撤回git add 的内容
````
git reset HEAD 文件名 将工作区修改后内容添加到暂存区后，退回到暂存之前。
如果还要继续讲工作区的修改内容退回，还要多一步操作git checkout -- 文件名
Head 参数表示最新版本

git checkout --文件名  将文件从缓冲区撤回到修改前。也就是撤回还未通过git add 命令的添加的文件。即在工作区修改的内容
````
### 6.2 退回版本
````
git reset -- 文件名
git reset --hard HEAD^ 退回到上一版本. head^ 上一个版本，head^^ 上两个版本 一次类推， 退回到前100版本，Head~100。
如果不带--hard 参数 将把把版本安全退回。 修改过的内容还存在。 如果想把修改过的内容也撤销，还需要使用git checkout --文件名.
实际上不带参数hard的退回，是把commit 提交退回到了缓存（也就是工作区的缓存，即还未添加到暂存区的时候）
````
## 7. 删除
### 7.1  删除暂存区和工作区文件
删除暂存区中的内容，并且保证工作区中的内容不存在
````
    git rm 文件名
    若干本地文件存在则不能删除，需要通过-f 参数删除
````
## 8. 推送 git push
````
git push origin master  将本地commit 推送到远程仓库.
把本地的 commit(提交) push 到远程服务器上，
origin 也就是之前 git remote add origin 那个命令里面的 origin，origin 替代了服务器仓库地址：git push git@github.com:winter1991/helloworld.git master
git push -u origin master
由于远程库是空的，我们第一次推送master分支时，加上了 –u参数，
Git不但会把本地的master分支内容推送的远程新的master分支，
还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
````
## 9. 拉取 git pull
````
git pull origin master 从远程服务器 pull 新的改动.
````
## 10. 检出 git checkout
````
git checkout tag1 切换分支
git checkout -b tagl 创建并切换分支
````
## 11. 分支
### 11.1 创建、删除、切换、查看分支

````
git branch tag1 创建分支 tag1为分支名称
git checkout tag1 切换到分支tag1
git checkout -b tag1 创建分支tag1，并切换到tag1分支
git branch -d tag1 删除分支tag1
git branch 查看分支，仅显示分支名称
git branch -v 查看分支，并显示版本，提交信息
````

### 11.2 合并分支
````
git merge test 合并分支test到当前分支，同时在当前分支创建一个新的commit。
正常情况下会执行成功，发现异常，就可能要手动解决冲突

````
### 11.2 解决分支冲突
````
若两个分支对同一文件同一个位置进行修改，分支合并就会产生冲突。此时将合并会失败，需要手动解决冲突，选择其中一个分支或者自己重写这个部分。
然后将修改的部分添加到暂存区，再commit。就可以了。
查看哪些文件冲突可以用git status
````
## 12. 克隆 git clone
````
第一次时，从远程服务器采用 git clone 将远程全部版本和历史记录复制到本地，此时较慢。
git clone git@gitgub.com:用户名/仓库名.git
上述命令 克隆到本地的目录名和仓库名相同。若想改成自己定义的名字，可以采用如下命令：
git clone git@gitgub.com:用户名/仓库名.git 自定义目录名
````

## 查看日志 git log git reflog
````
git log 查看日志具体信息
git log -pretty=oneline 查看版本信息，如果嫌弃git log 命令显示内容太多，可以使用此命令省略。

git reflog 对历史日志查看。如果通过回退后，原来的版本我们无法通过git log 查看到。 可以使用git reflog。
````
## git remote add
````
git remote add  别名 远程服务器地址  ---添加远程服务器地址，建立关联关系，下次推送也就不需要每次都用输入地址了.否则，不确定别名所对应的地址是什么，

````

## bug

参考内容：http://blog.csdn.net/wengpingbo/article/details/8985132