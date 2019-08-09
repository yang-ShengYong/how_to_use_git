# Git

## 什么是Git

- Git 是源代码管理工具
- 是Linux之父为了维护Linux系统开发的管理工具，现在开源了

## Git 安装
- 从官网上下载安就完事儿了

## 初始化Git仓库
- 仓库存放Git对我们项目代码进行备份的文件
- 在项目目录下 右键打开 Git bash
- 命令：`git init`

## 自报家门（谁动了仓库里的代码）
- 设置当前使用的用户是谁
- 命令:
	- 配置用户名：`git config --global user.name "zhangsan"`
	- 配置邮箱：`git config --global user.email "zhangsan@qq.com"`

## 把代码放到仓库
- 1.把代码放到仓库门口
	+ `git add ./README.md`
	+ `git add ./`把所有./目录下修改的文件放入仓库门口
- 2.把代码放到仓库中（必须加说明）
	+ `git commit -m "必须的一些说明"` 
- 3.直接整合前两步操作
  - `git commit --all -m "说明"`
  - --all 指的是所有修改的文件

## 查看当前状态

- 查看代码有没有存放在仓库中
- `git status`

## git中的忽略文件

- .gitignore 在这个文件中设置要被忽略的文件或者目录
- 被忽略的文件不会提到仓库里去
- 写法：（以/开头，一行写一个路径）
  - `/.idea` 忽略.idea文件
  - `/js` 忽略js目录下的所有文件
  - `/js/*.js` 忽略js目录下的所有js文件

## 查看日志

- `git log` 查看带具体信息的日志
- `git log --oneline`  查看精简版日志

## 回退到指定的版本

- `git reset --hard Head~0`  回退到最近一次提交代码的状态

  > 0 是日志数组的索引
  
- `git reset --hard [版本号]` 精确回退到某个版本

- `git reflog` 可以看到每一次切换版本的记录

## 分支

- 默认有一个主分支master

### 创建分支

- `git branch dev`
  - 刚创建的dev分支
  - dev中的内容和master是一样的

### 切换分支

- `git checkout dev` 切换到dev分支

### 查看有哪些分支

- `git branch`

### 合并分支

- `git merge dev` 把当前分支（带*的分支，用`git branch`查看）与指定分支（现在是 dev）进行合并
- 合并时如果有冲突，需要手动去处理，然后再提交一次

## Github

### 提交代码到github

- `git push [地址] master`
  - 示例：`git push https://github.com/yang-ShengYong/test-demo.git master`
  - 把当前内容上传到远程分支上
- `git pull [地址] master`
  - 示例：`git pull https://github.com/yang-ShengYong/test-demo.git master`
  - 把远程代码拖到本地（前提得初始化一个本地仓库）
  - 如果多次执行会合并
- `git clone [地址] master`
  - 会得到远程仓库相同的数据，用一个文件夹包裹
  - 如果多次执行会覆盖

### ssh方式上传代码

- **公钥** **私钥**，两者之间有关联
- 生成公钥和私钥
  - `ssh-keygen -t rsa -C "zhangsan@qq.com"`

### 先pull，再push

- 防止服务器和本地的版本不同从而产生冲突
- 给url起个名
  - `git remote add test-demo git@github.com:yang-ShengYong/test-demo.git`
- 在push时加上 `-u`，那么在下一次上传时只需`git push`（pull也一样）
  - `git push test-demo -u master`
  - `git push`