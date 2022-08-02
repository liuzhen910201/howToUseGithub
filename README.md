<a href="https://996.icu"><img src="https://img.shields.io/badge/link-996.icu-red.svg" alt="996.icu"></a>
[![LICENSE](https://img.shields.io/badge/license-Anti%20996-blue.svg)](https://github.com/996icu/996.ICU/blob/master/LICENSE)
[![LICENSE](https://img.shields.io/badge/license-Anti%20996-blue.svg)](https://github.com/996icu/996.ICU/blob/master/LICENSE_CN)

# github配置 连接本地文件夹 上传代码 同步
## 注册
在[github](https://github.com )官网直接注册 用户名 邮箱 密码
## 创建目录
注册并登录后 点击右上角 new repository
![](https://github.com/liuzhen910201/howToUseGithub/blob/master/repository.png)
<br>
<br>
命名后 点击创建
![](https://github.com/liuzhen910201/howToUseGithub/blob/master/newRepository.png)
<br>
## 下载并安装客户端
选择mac或windows https://desktop.github.com

## 配置
在命令行(用户文件夹)
  ```
 ssh-keygen -t rsa -C "注册邮箱地址"
  ```
 <br>
 会在当前文件夹下生成一个.ssh的文件夹 打开该文件夹 找到id_rsa.pub的文件并拷贝内容(mac用户可以使用cat或者vi等 windows如果office打不开也可以用text)
 <br>
 打开github的个人设置选项   <br>
 ![](https://github.com/liuzhen910201/howToUseGithub/blob/master/settings.png)
 <br>
 选择ssh key 并创建新的ssh key   <br>
 ![](https://github.com/liuzhen910201/howToUseGithub/blob/master/sshkey.png)
  <br>
  检验是否连接成功 <br>
  `
  ssh -T git@github.com
  `
 
## 上传

在github上创建目录完毕后 克隆至本地 <br>
```
git clone //目录的URL(http) 
```
获取目录的URL可以直接拷贝地址栏 也可以
![](https://github.com/liuzhen910201/howToUseGithub/blob/master/clone.png)
<br>

完成此操作后 在本地文件夹Github(连接github的操作时生成)下 会生成与目录同名的文件夹 <br>
将希望上传的文件导入该文件夹 并在命令行cd到该与目录同名的文件夹下 <br>
第一步 添加
```
git add <filename> //上传全部则是 git add .
```
第二步 版本名
```
git commit -m "版本名"(对应客户端 commit to master)
```
第三步 上传(同步更新)
```
git push //如果不能上传 可以git push -u origin master -f (对应客户端 Sync)
```
## 删除
先cd到希望删除文件所在的文件夹下（即与目录同名的文件夹）<br>
第一步 rm删除
```
git rm <filename>
```
第二步 版本名
```
git commit -m "版本名"
```
第三步 同步更新
```
git push //如果不能上传 可以git push -u origin master -f
```

## 更新(本地修改同步更新至github目录)
在本地修改后保存文件<br>
重新添加文件
```
git add <filename> //上传全部则是 git add .
```
版本名
```
git commit -m "版本名"
```
同步更新
```
git push -u origin master -f
```
<br>

另外 使用命令

```
git status
```

查看当前文件夹下文件是否被上传至目录或者是否同步更新

## 更新(github修改同步更新至本地仓库)
在github上修改完成后 

```
git pull origin master
```

## 版本回退

```
git log
```
查看提交历史，以便确认回退到哪个版本 <br>

```
git log　--pretty=oneline
```
以行的形式显示 <br>
```
git reflog
```
看命令历史，以便确定要前进未来的哪个版本  <br>
```
git reset --hard 版本号
```
回退或者前进到指定版本 <br>
提交 <br>
```
git push -u origin master -f
```
确定回退或前进 <br>

出现`Unstaged changes after reset `的解决办法
```
git add .
git reset --hard
```

## 取消本地更改
```
git reset --hard origin/master
```

## 分支创建，合并
创建并移动到分支<br>
```
git checkout -b <name>
```
或者<br>
```
git branch <name>
git checkout <name>
```
查看当前分支<br>
```
git branch
```

删除分支<br>
```
git branch -d <name>
```
合并分支<br>
例如，将<name>合并至master
先移动到分支name
```
git checkout <name>
```
再合并分支<br>
```
git merge <name>
```
如果需要同步修改(将分支的修改同步到当前分支master)<br>
```
git push -u origin master -f
```
## 切换用户
 有多个账号情况下的用户切换
 ```
 git config --global user.email "注册邮箱"
 ```
 
 查看当前用户
  ```
  git config user.email
  ```
## git push 输入用户名和密码
