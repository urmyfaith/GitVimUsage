
又不会的git操作,查看

* [廖学峰git](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137396287703354d8c6c01c904c7d9ff056ae23da865a000)

# windows下git使用

文章概览：
* windows下git使用
* vim编码设置
  * git ls显示中文乱码问题


----

## windows下git使用

从网盘下载安装即可

* 使用git连接github

1）生成本机的密钥
```bat
ssh-keygen -C 'urmyfaith.qq.com' -t rsa
```
2）将生存的密钥添加到github网站中

a)登陆https://github.com/settings/ssh

b）Add an SSH Key

3）测试是否可以登录github使用，添加用户名和邮箱
```bat
$ ssh -T git@github.com
$ git config --global user.email "urmyfaith@qq.com"

$ git config --global user.name "urmyfaith"
$ git config --global push.default matching

```


4）本地git初始化
```bat
$    git init  
```


5） 拉取服务器项目
```bat
$ git pull  https://github.com/urmyfaith/NotesOfDjangoBook.git 
或者
$ git pull git@github.com:urmyfaith/NotesOfDjangoBook.git
```


6） 修改，添加文件,提交
```bat
git add filname_here

git commit -m "notes_here"
```



7） 提交更改到服务器


```bat
git remote add origin https://github.com/urmyfaith/NotesOfDjangoBook
# also:
# git remote add origin https://github.com/urmyfaith/NotesOfDjangoBook.git
# git remote add origin git@github.com:urmyfaith/NotesOfDjangoBook.git
git push -u origin

```

* 提交时候密码的问题：

如果不想每次提交都输入密码，可以更改“.git/config"文件中的url值格式为：
```
 url = git@github.com:[user_name]/[project_name].git
```

```bat
[core]
	repositoryformatversion = 0
	filemode = false
	bare = false
	logallrefupdates = true
	symlinks = false
	ignorecase = true
	hideDotFiles = dotGitOnly
[remote "origin"]
	url = git@github.com:urmyfaith/NotesOfDjangoBook.git
	fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
	remote = origin
	merge = refs/heads/master
```

---
## git ignore file 
To ignore file,edit:
```bat
.git\info\exclude
```
add the filetype you want to igonre to commit .
eg:
```
*.md~

```

## git 打tag

显示历史提交

```
git log --pretty=oneline --abbrev-commit
```

给某个提交打tag

```
git tag v0.9 4224935
```

更多参考[廖学峰-git-tag](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001376951758572072ce1dc172b4178b910d31bc7521ee4000)


## vim编码设置
(显示中文乱码问题，最后一行解决）
vimrc文件位置：
```
C:\Program Files\Git\share\vim
```

添加如下设置
```
set nocompatible
set number
filetype on
set history=1000
set background=dark
syntax on
set autoindent
set smartindent
set tabstop=4
set shiftwidth=4
set showmatch
set guioptions-=T
set vb t_vb=
set ruler
set nohls
set incsearch
if has("vms")
set nobackup
else
set backup
endif
set fileencodings=utf-8,gbk
```
## git ls显示中文乱码问题
编辑
```
C:\Program Files\Git\etc\git-completion.bash
```
添加：
```
alias ls="ls --show-control-chars"
```

----
## git view history

```bash
git log --pretty=oneline
```

```
alias git log="git log -- graph -- pretty = format : '%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%Creset' -- abbrev - commit -- date = relative"
```
----

## git rm file git删除文件
移动文件，然后从git里移除文件，再添加，最后提交。

```bash
mv file_form file_path_to
git rm file_from
git add file_path_to_full_name.
git commit -c "move file"
```
---
## git diff

HEAD commit 版本
Index staged版本

git diff	
git diff --cached	（add之后的不同）
git diff --staged	（add之后的不同）

git diff HEAD	（commit之后的修改本地后的不同）
git diff HEAD^ HEAD	（最后两次commit的不同）
----



```
# Git

alias gdiff="git diff HEAD^ HEAD"
alias gdiffCached="git diff --cached"
alias gps="git push"
alias gtm="git checkout master"
alias gtd="git checkout zxdev"
alias gl="git pull --rebase"
alias zxlog="git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%Creset' --abbrev-commit --date=relative"

```

## git whatchanged  显示每个commit更改了哪些文件

```bash
$ git whatchanged 
```

## 显示master昨天的更改。 

```bash
$ git show master@{yesterday}
```

## stash 暂存

```bash
$ git stash list                                            # 查看所有暂存

$ git stash show -p stash@{0}                               # 参考第一次暂存

$ git stash apply stash@{0}                                 # 应用第一次暂存
```

## git submodule 

```bash
 git submodule update --init --recursive
```

## git 创建与删除远程分支

```bash
$ git push origin test:master         # 提交本地 test分支 作为远程的 master分支
$ git push origin test:test           # 提交本地 test分支 作为远程的 test分支

# 如果想删除远程的分支呢？类似于上面，如果:左边的分支为空，那么将删除:右边的远程的分支。

$ git push origin :test             # 刚提交到远程的test将被删除，但是本地还会保存的，不用担心
```

## git 显示某个文件的修改历史

```bash
 git log --follow -p path/to/file
```

或者

```bash
gitk path/to/file
```

## git fork 别人的代码后，自己又有更改，怎么获取最新的呢？

1)fork 后的远程分支：

```bash
$ git remote -v
origin	https://git.coding.net/z2xy/git-from-the-inside-out.git (fetch)
origin	https://git.coding.net/z2xy/git-from-the-inside-out.git (push
```

2)添加 upstream 
 
```bash
$ git remote add   tvvocold  https://git.coding.net/tvvocold/git-from-the-inside-out.git

$ git remote -v 
origin	https://git.coding.net/z2xy/git-from-the-inside-out.git (fetch)
origin	https://git.coding.net/z2xy/git-from-the-inside-out.git (push)
tvvocold	https://git.coding.net/tvvocold/git-from-the-inside-out.git (fetch)
tvvocold	https://git.coding.net/tvvocold/git-from-the-inside-out.git (push)
```

3) 拉去fork的仓库更新

```bash
$ git pull tvvocold HEAD:HEAD    
From https://git.coding.net/tvvocold/git-from-the-inside-out
 * [new ref]                    -> HEAD
warning: refname 'HEAD' is ambiguous.
Already up-to-date.
```

4) merge／rabase 解决冲突

```bash
$ git reabse  tvvocold 
```

## 远程分支的删除

see http://blog.csdn.net/lxbwolf/article/details/53168066

查看

```bash
$ git remote show origin
```

删除

```bash
$ git push origin :remoteBranchToDelete
$ # or
$ git push origin --delete remoteBranchToDelete
```

删除缓存：

```bash
$ git remote prune origin
$ # or
$ git fetch -p
```

参考：

* [http://casparzhang.blog.163.com/blog/static/12662655820140705139542/](git安装和简单使用 "")

* [git总结](https://raw.githubusercontent.com/urmyfaith/NotesOfDjangoBook/master/Git%E7%AE%80%E6%98%8E%E6%89%8B%E5%86%8C.pdf "") 

* [git-tutorials](https://www.atlassian.com/git/tutorials/)
* [廖学峰git](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137396287703354d8c6c01c904c7d9ff056ae23da865a000)
* http://pic002.cnblogs.com/img/1-2-3/201007/2010072023345292.png
