# Git 实践学习小组项目

欢迎来到 Git 实践学习小组！本项目旨在帮助大家掌握 Git 的基本操作流程。

## 操作步骤指南

### 1. Fork 本仓库
1. 点击页面右上角的 "Fork" 按钮
2. 选择你自己的 GitHub 账户作为目标
3. 等待 Fork 完成，你将拥有本仓库的一个副本

### 2. Clone 到本地
1. 在你的 GitHub 仓库页面点击 "Code" 按钮
2. 复制 HTTPS 或 SSH 链接
3. 在本地终端执行：
   ```
   git clone <你的仓库链接>
   cd team-git-good
   ```

### 3. 创建新分支
使用你的昵称创建一个新分支：
```
git checkout -b <你的昵称>
```
例如：`git checkout -b zhangsan`

### 4. 添加你的个人文件
1. 在仓库根目录下创建一个以你昵称为名的 Markdown 文件：
   ```
   touch <你的昵称>.md
   ```
2. 在文件中添加以下内容：
   ```
   # 我是 <你的名字>
   
   这是我第一次参与 Git 协作实践！
   
   ## 学习心得
   - 学会了如何 fork 仓库
   - 掌握了分支管理
   - 理解了 PR 流程
   ```

### 5. 提交更改
```
git add <你的昵称>.md
git commit -m "Add <你的昵称>.md with learning notes"
git push origin <你的昵称>
```

### 6. 发起 Pull Request
1. 访问你的 GitHub 仓库页面
2. 点击 "Compare & pull request" 按钮
3. 填写 PR 描述信息
4. 点击 "Create pull request"

### 7. 等待审核与合并
组长将审核你的 PR 并将其合并到主仓库中。

## 规范要求

1. 分支名称必须是你自己的昵称
2. 文件名必须与分支名一致（如：zhangsan.md）
3. 提交信息要简洁明了
4. PR 标题格式：`Add <昵称>'s learning notes`

## 练习完成确认

完成以上所有步骤后，请告知组长已完成练习。