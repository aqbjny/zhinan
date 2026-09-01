# Git 分支 PR 实操笔记

本项目记录 Git 分支开发、PR 合并完整流程。

## 流程

1. 从 `master` 创建 `dev` 功能分支
2. 分支内修改文件，`commit` 本地提交，推送到远程
3. GitHub 创建 PR，`dev → master` 网页合并
4. 本地切回 `master`，`fetch` + `merge origin/master` 同步远程
5. 删除远程、本地 `dev` 分支，清理追踪记录

## 关键概念

- 分支：不新建磁盘文件夹，切换版本快照
- `fetch`：下载远程信息，**不修改本地文件**
- `pull` = `fetch + merge`：下载并直接合并
- PR：GitHub 网页合并，用于代码审核协作
- 删除分支：仅删除书签，**提交历史保留**
- 文件移动：Git 表现为「删旧路径 + 增新路径」，两者都要暂存

## 常用命令

```
git log --oneline --graph   # 图形化查看提交历史
git checkout -b dev         # 创建并切换分支
git checkout master         # 切换分支
git branch -d dev           # 安全删除本地分支
git fetch origin            # 获取远程更新，不改动文件
git status                  # 查看工作区状态
```

## 本次提交历史

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

## 踩坑要点

1. 文件移动，新旧路径都要加入暂存再提交
2. 网页删分支后，执行`fetch origin`清理本地残留追踪
3. PR 合并后本地 master 不会自动更新，需要手动同步
4. `git log` 界面按 `q` 退出