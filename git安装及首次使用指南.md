# 访问下载

[https://git-scm.com/install/windows](https://git-scm.com/install/windows)

## 最推荐的配置（直接照着调）

- 不勾：`On the Desktop`（不要桌面图标）
- 保留：`Open Git Bash here`，**可以取消**`Open Git GUI here`**（几乎没人用 GUI）**
- ✅**勾选：Add a Git Bash Profile to Windows Terminal**（把这个打上勾）
- 其余保持现状，直接点`Next`下一步即可。

# 安装完验证是否成功

git --version
输出版本号就代表安装成功。

> 接下来建议配置用户名邮箱（提交代码必须）：

```
git config --global user.name "你的名字"
git config --global user.email "你的github邮箱"
```

# 本地文件夹上传到 GitHub 完整步骤

1.GitHub，点左边绿色 **New**，新建远程仓库
**不要勾选 Add a README file**（本地已经有文件，不要在网页初始化）
2.进入你的本地文件夹，空白处右键 → **Open Git Bash here**（就是你安装 git 勾选的右键菜单）

# 解决终端复制问题

### ｜改成熟悉的 Ctrl+Shift+C / V（永久设置）

1. 在 MINGW64 窗口最**顶部标题栏**右键 → `Options`（选项）
2. 切换到 `Keys`（按键）标签
3. 勾选：`Ctrl+Shift+letter shortcuts`
4. 点 Apply、保存。

设置完之后：

- 复制：`Ctrl+Shift + C`
- 粘贴：`Ctrl+Shift + V`

## 1.初始化git，把这个文件夹变成git仓库

git init

## 2.把文件夹里所有文件加入暂存

git add .

## 3.提交，引号内写提交备注

git commit -m "第一次上传全部文件"

## 4.关联远程github仓库，粘贴你刚才复制的.git地址

git remote add origin [https://github.com/aqbjny/你的仓库名.git](https://github.com/账号/你的仓库名.git)

## 5.推送到github

git push -u origin master

# Git 弹窗登录界面

现在这个弹窗是新版 Git 的浏览器授权登录，**不用手动填 token 了，更简单**。

### 操作步骤

1. 点击蓝色按钮：`Sign in with your browser`**（使用浏览器登录）**
2. 会自动打开你的浏览器，跳转到 GitHub 授权页面
3. 浏览器上登录你的 `aqbjny` GitHub 账号，点 **Authorize（授权）**

浏览器页面显示 `Authentication Succeeded` = **授权成功**
看终端输出关键信息：

```
[new branch]      master -> master
branch 'master' set up to track 'origin/master'.
```

# 现在做什么
打开你的 github `aqbjny/zhinan` 仓库网页，**刷新页面**，就能看到本地那 4 个 txt 文件全部出现在网页上。

## 以后更新文件的极简命令（记住这 3 条）

以后修改本地文件夹里面的文件，想同步到 GitHub，在这个文件夹右键打开 Git Bash，依次运行：

```
git add .
git commit -m "写你这次修改做了什么"
git push
```

> 不用再写 remote、不用 - u，直接 git push 就推送。



# 》问题原因

你现在进入了**多行输入模式**，看到 `>` 符号，Git 以为你还在继续输入 commit 的备注，没有执行命令。

> 原因：你输入 commit 那一行，**引号用了中文双引号 “ ”**，不是英文引号 `" "`，Git 识别不到结束引号，卡在等待输入。



### 解决步骤

按键盘：`Ctrl + C`，退出这个卡住的输入状态，回到正常 `$` 提示符。


