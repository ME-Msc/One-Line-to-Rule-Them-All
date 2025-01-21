---
title: "Git"
nav_order: 3
---

# Git

{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## 基础

- `git init`：仓库本地初始化
- `git status`：仓库状态查看
- `git add *.txt`：添加所有 txt 文件
- `git commit -m "add test.txt" -s`：提交注释说明，并签名
- `git commit --amend`：修改说明信息
- `git reset HEAD <file>`：撤回已经 add 的 file 文件
- `git checkout -- <file>`：将已修改未 add 的 file 文件回滚到未修改状态
- `git log --graph --decorate`：查看 git 记录，显示分支图和名称
- `git diff test.txt`：查看编辑区与已 add 部分的区别

## 分支

- `git checkout [commit id]`：切换 commit 版本
- `git checkout -b debug`：创建 debug 新分支，并切换
- `git merge debug`：在 main 分支上，将 debug 分支合并进来
- `git rebase -onto main next debug`：将 next 分支上的 debug 分支变基到 main 分支上

## 远程仓库

- `git remote`：显示远程仓库信息
- `git remote add <本地仓库名> <远程仓库url>`：基于本地仓库建立远程仓库
- `git push <远程主机名> <本地分支名>：<远程分支名>`
- `git branch --set-upstream-to=<远程仓库名>/<远程分支名>`：将本地仓库与远程仓库构建关联
- `git fetch`：下拉远程仓库
- `git pull`：下拉远程仓库，并合并到本地
- `git clone`：从远程仓库下载

## 高阶

- `git blame <file>`：查看 file 文件每一行的贡献人
- `git stash push/pop/list`：将当前临时修改压入 git 临时存储栈
- .gitignore

## [Trouble shooting](https://ohshitgit.com/zh)

- 回退到已删除的 commit
  - `git reflog`
  - `git reset HEAD@{index}`
- 在刚提交的本地分支 commit 上添加小改动
  - 继续改动你的文件
  - `git add .`
  - `git commit --amend --no-edit`
- 修改刚刚提交的 commit 信息：`git commit --amend`
- 错把本应在新分支上提交的东西提交到了 master
  - `git branch new_branch_name`基于当前 master 新建分支
  - `git reset HEAD~ --hard`在 master 上删除最近的那次 commit
  - `git checkout new_branch_name`此时只有新分支上有最新的 commit
- commit 提交错分支了
  - `git checkout name-of-the-correct-branch`抓取 master 分支上最新的那个 commit
  - `git cherry-pick master`然后删掉 master 上的那个 commit
  - `git checkout master`
  - `git reset HEAD~ --hard`
