# 基础概念与原理
Git 更像是把数据看作是对小型文件系统的一组快照。 
每次你提交更新，或在 Git 中保存项目状态时，它主要对当时的全部文件制作一个快照并保存这个快照的索引。
为了高效，如果文件没有修改，Git 不再重新存储该文件，而是只保留一个链接指向之前存储的文件。 Git 对待数据更像是一个 快照流。

## 分布式版本控制系统

- 版本控制是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统，GIT是版本控制的一种产品。

### 常用命令
2个节点操作+4个分支操作+1个提交树操作 能覆盖90%日常工作。
### 节点操作
#### 1.1 提交本地修改
git commit;

#### 1.2 撤销提交
- 撤销本 地-撤销到某个具体提交的hash节点
git reset [hash]
- 撤销远程-撤销提交到远程的hash节点
git revert [hash]

### 分支操作
#### 2.1 新建分支bugFix
git branch bugFix;

#### 2.2 切换分支
git checkout bugFix;

#### 2.3 merge合并
把一个分支合并到另外一个分支
假设目的分支main
补充内容分支为bugFix
1. 切换到目的分支main git checkout main
2. 合并分支到bugFix,git merge bugfix;就会把bugFix上面的变更合并到main
本质：把别人的分支提交合并到自己的分支
rebase合并
1、 切换目的分支bugFix git rebase main
本质：是把别人分支作为自己的父节点，然后把自己的修改提交作为最新节点，提交到别人的分支

#### 2.4 移动分支与相对引用
分离HEAD,默认HEAD总是指向分支最新一次提交
git checkout [hash]
git checkout HEAD^
git checkout HEAD~3
移动分支-很重要
git beanch -f main HEAD

#### 3.1 自由修改提交树-整理提交记录
cherry-pick
1、 git checkout [branch] git cherry-pick [hash]、[hash]......
交互式rebase
2、 git rebase -i [hash] HEAD~[hash]之间的提交重新排序或者删除
思考：checkout HEAD brance三者之间的关系

git tag
标签的意义：分支总是被新的修改的提交移动，tag可以引用里程碑的提交，起到锚点作用
git tag v1 c1

git describe [branch]
describe:查看当前分支最新提交与最近锚点的距离

远程仓库相关命令
远程仓库通过网络通信来备份提交记录
#### 创建项目

- git init 切换至该目录下，该命令能够创建.git目录
- git clone *.git 克隆远程git仓库
- git fetch 下载数据
- git pull = git fetch + git merge 下载远程分支并合并到本分支

### 参考材料：
- 比较工具 
- 权威Git书籍 ProGit（中文版） https://www.progit.cn/
- 在线练习网站 https://learngitbranching.js.org/