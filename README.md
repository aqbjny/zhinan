# Git 使用方法总结
> 实操学习笔记，包含安装、提交、分支、PR合并、删除分支，分为GUI图形界面与Bash命令行两种方式。

## 📁 项目目录说明
所有实操文档存放于 `ai用git提示词/` 文件夹
- `git安装及首次使用指南.md`：Git安装、账号配置、仓库初始化
- `git本地提交方法bash和GUI.txt`：本地提交，Git‑GUI图形界面 + bash命令两种操作
- `创建分支branch及合并pr.md`：创建分支、推送远程、GitHub PR合并完整流程
- `删除分支.md`：远程分支、本地分支删除操作
- `bash查看历史并且让ai做README.txt`：git log 查看提交历史实操记录

## 🚀 标准分支开发工作流
1. 在 `master` 主分支基础上创建功能分支 `dev`
2. 在功能分支修改文档，本地执行 `commit` 保存改动
3. 将分支推送到GitHub远程仓库
4. GitHub网页创建 Pull Request，发起 `dev → master` 合并请求
5. 审核通过，网页端合并PR
6. 本地切回 `master`，执行 `fetch` + `merge origin/master` 同步远程最新代码
7. 合并完成，清理无用分支：删除GitHub远程dev、电脑本地dev分支

## 💡 核心概念
- **分支**：不会新建磁盘文件夹，只是版本快照指针，切换分支即切换快照
- `fetch`：拉取远程仓库信息，**不修改本地文件**，用于刷新本地远程记录
- `pull` = `fetch + merge`：拉取远程数据并且直接合并更新本地文件
- `merge`：把其他分支的更改合并到当前所在分支
- **PR(Pull Request)**：GitHub网页协作工具，支持代码审核后再合并分支
- 删除分支：只删除分支指针，**全部提交历史完整保留，不会丢失**
- 文件移动/重命名：Git识别为「删除旧路径 + 新增新路径」，新旧文件都需要加入暂存区

## ⌨️ Bash 高频命令
```bash
git status                    # 查看工作区状态
git log --oneline --graph     # 简洁图形化查看提交历史，按 q 退出日志界面
git checkout -b dev           # 创建并切换到 dev 分支
git checkout master           # 切换到 master 主分支
git add .                     # 将全部改动加入暂存区
git commit -m "提交说明"      # 生成本地提交
git push origin dev           # 将dev分支推送到远程GitHub
git fetch origin              # 获取远程更新，不改动本地文件
git branch -d dev             # 安全删除已经合并完成的本地分支
```

## 🖱️ Git‑GUI 图形界面关键操作
1. Rescan：扫描项目文件夹改动
2. Stage Changed：将改动加入暂存区
3. Commit：本地提交
4. Remote → Fetch from origin：刷新远程仓库记录
5. Branch → Delete：删除本地分支

## ⚠️ 实操踩坑记录
1. 文件移动重命名，旧路径删除、新路径新增都要进入暂存区再commit，否则会丢失文件。
2. GitHub网页删除远程分支后，本地残留`origin/dev`，执行`fetch origin`自动清理该追踪记录。
3. PR在网页合并完成，**本地master不会自动更新**，需要手动 `fetch + merge origin/master` 同步。
4. `git log` 日志界面，按 `q` 退出。

## 📜 项目提交历史
```
* ca304d1 整理文档，移动文件到子文件夹
* 78f82c8 添加git安装使用md
*   eb334c8 Merge pull request #1 from aqbjny/dev
|\
| * cf143ab dev 添加gitGUI使用方法
|/
* 6ea3ca4 再次更新README.md
* d9b23bd 完善README.md
* fff326a 第二次 添加了readme
* 0b8e1a4 first up
```
