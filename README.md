# Git 实践学习小组项目

欢迎来到 Git 实践学习小组！本项目旨在帮助大家掌握 Git 的基本操作流程。

> ⚠️ **重要提醒**：本教程中的所有命令都需要在终端（命令行界面）中运行。请确保你的电脑已安装 Git。
>
> 如果你尚未安装 Git，请访问 [Git 官网](https://git-scm.com/downloads) 下载 Windows 版本并安装。
> 
> 📢 **过程中遇到任何问题，请随时在群里 @组长 获取帮助。**

## 操作步骤指南

### 如何打开终端
在 Windows 系统中有多种方式可以打开终端：

1. **使用 Git Bash（推荐）**
   - 在桌面或开始菜单找到并点击 "Git Bash"
   - 这是一个专为 Git 设计的终端工具，提供类 Unix 命令环境

2. **使用 CMD（命令提示符）**
   - 按 `Win + R` 键，输入 `cmd` 并回车
   - 或者在开始菜单搜索 "命令提示符" 并打开

3. **使用 PowerShell**
   - 按 `Win + R` 键，输入 `powershell` 并回车
   - 或者在开始菜单搜索 "PowerShell" 并打开

4. **在文件资源器中打开**
   - 打开项目文件夹
   - 在地址栏输入 `bash` 或 `cmd` 并回车

建议使用 Git Bash，因为它专为 Git 设计，兼容性最好。

### 1. 注册 GitHub 账号
如果你还没有 GitHub 账号，需要先注册一个：
1. 访问 [GitHub 官网](https://github.com/)
2. 点击 "Sign up" 按钮
3. 按照提示填写用户名、邮箱和密码
4. 完成邮箱验证

### 2. Fork 本仓库
Fork 是复制一个仓库到你自己的账户下，这样你就可以自由修改而不影响原仓库：
1. 点击页面右上角的 "Fork" 按钮
2. 选择你自己的 GitHub 账户作为目标
3. 等待 Fork 完成，你将拥有本仓库的一个副本

### 3. Clone 到本地
Clone 是将远程仓库下载到本地计算机，以便在本地进行开发工作：
1. 在你的 GitHub 仓库页面点击 "Code" 按钮
2. 复制 HTTPS 或 SSH 链接
3. 打开终端（参考上方说明）并执行以下命令：
   ```
   git clone <你的仓库链接>
   cd team-git-good
   ```
   - `git clone`: 将远程仓库复制到本地
   - `cd team-git-good`: 进入项目目录

### 4. 创建新分支
分支是 Git 中非常重要的概念，它允许你在不影响主线代码的情况下进行开发：
```
git checkout -b <你的昵称>
```
- `git checkout -b`: 创建并切换到新分支
- `<你的昵称>`: 分支名称，替换为你自己的昵称

例如：`git checkout -b zhangsan`

### 5. 添加你的个人文件
1. 在仓库根目录下创建一个以你昵称为名的 Markdown 文件：
   ```
   touch <你的昵称>.md
   ```
   > 💡 **提示**：Windows 用户如果没有 `touch` 命令，可以使用以下任一替代方法：
   > - 使用 `echo. > <你的昵称>.md` 创建空文件
   > - 直接使用文本编辑器创建文件
   > - 使用 `copy nul <你的昵称>.md` 命令
   
   - `touch`: 创建一个新的空文件
   
2. 在文件中添加以下内容：
   ```
   # 我是 <你的名字>
   
   这是我第一次参与 Git 协作实践！
   
   ## 学习心得
   - 学会了如何 fork 仓库
   - 掌握了分支管理
   - 理解了 PR 流程
   ```

### 6. 提交更改
将你的修改保存到本地仓库并推送到远程仓库：
```
git add <你的昵称>.md
git commit -m "Add <你的昵称>.md with learning notes"
git push origin <你的昵称>
```
- `git add`: 将文件添加到暂存区，准备提交
- `git commit`: 将暂存区的更改保存到本地仓库
- `git push`: 将本地提交推送到远程仓库

### 7. 发起 Pull Request
Pull Request（PR）是用来向原仓库贡献代码的方式：
1. 访问你的 GitHub 仓库页面
2. 点击 "Compare & pull request" 按钮
3. 填写 PR 描述信息
4. 点击 "Create pull request"

### 8. 等待审核与合并
组长将审核你的 PR 并将其合并到主仓库中。

## 规范要求

1. 分支名称必须是你自己的昵称
2. 文件名必须与分支名一致（如：zhangsan.md）
3. 提交信息要简洁明了
4. PR 标题格式：`Add <昵称>'s learning notes`

## 练习完成确认

完成以上所有步骤后，请告知组长已完成练习。

## 欣赏最终成果

可以到 https://github.com/luobochuanqi/team-git-good 仓库页面查看自己的分支。