# Git 提交签名验证配置指南

为了提高代码提交的安全性和可信度，建议配置 GPG 或 SSH 密钥对提交进行签名验证。

> 📝 **注意**：GPG 和 SSH 签名选择其一即可，两者都能实现提交签名验证功能。
> 我建议初学者先尝试 GPG 密钥，我感觉会简单一点。

## GPG 签名配置

### 1. 安装 GPG
- **Windows**: Git for Windows 自带 GPG 功能，无需额外安装其他软件

### 2. 在 git bash 中生成 GPG 密钥对 (git bash 如何启动 见第一项任务步骤文档)
```bash
gpg --full-gen-key
```
按照提示操作：
1. 选择密钥类型（默认 RSA 和 RSA）
2. 选择密钥长度（建议 4096）
3. 设置密钥有效期
4. 输入姓名和邮箱（建议使用 GitHub 绑定的邮箱）
5. 输入安全密码

### 3. 获取 GPG 密钥 ID
```bash
gpg --list-secret-keys --keyid-format LONG
```
输出**示例**：
```
sec   rsa4096/3AA5C34371567BD2 2021-01-01 [SC]
      CBDB23DDE8AA796FEC743BB23AA5C34371567BD2
uid                 [ultimate] Your Name <your_email@example.com>
ssb   rsa4096/42B3A2FCDAC87324 2021-01-01 [E]
```
其中 `3AA5C34371567BD2(示例)` 就是密钥 ID。

### 4. 导出公钥并添加到 GitHub
```bash
gpg --armor --export 3AA5C34371567BD2
```
直接在终端运行以下命令查看公钥内容：
```bash
gpg --armor --export 3AA5C34371567BD2
```
复制输出的所有内容（包括开头的 `-----BEGIN PGP PUBLIC KEY BLOCK-----` 和结尾的 `-----END PGP PUBLIC KEY BLOCK-----`）。

在 GitHub 的 Settings -> SSH and GPG keys -> New GPG key 中粘贴保存。

### 5. 配置 Git 使用 GPG 签名
```bash
git config --global user.signingkey 3AA5C34371567BD2
git config --global commit.gpgsign true
```
> 💡 **提示**：`3AA5C34371567BD2`替换为自己的

## SSH 签名配置

### 1. 生成 SSH 密钥对（如果还没有）
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
> 💡 **提示**：如果使用 Windows 系统并且有 Git Bash，需要启动 ssh-agent 以确保 SSH 签名正常工作：
> ```bash
> eval $(ssh-agent -s)
> ssh-add ~/.ssh/id_ed25519
> ```
> 这一步是为了将私钥加载到 ssh-agent 中，使得签名过程能够顺利进行。

### 2. 在 GitHub 中添加 SSH 公钥
直接在终端运行以下命令查看公钥内容：
```bash
cat ~/.ssh/id_ed25519.pub
```
复制输出的所有内容。

将复制的内容添加到 GitHub 的 Settings -> SSH and GPG keys -> New SSH key 中。

### 3. 配置 Git 使用 SSH 签名
```bash
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
git config --global commit.gpgsign true
```
> 📝 **说明**：`commit.gpgsign true` 配置会使 Git 在每次提交时自动签名，无需手动添加 `-S` 参数。

## 验证签名

提交更改后，可以通过以下方式验证签名：

### 方法一：使用命令行查看
```bash
git log --show-signature
```
> 📝 **说明**：此命令会显示提交历史及签名验证结果，如果配置正确且提交已签名，会显示验证成功的相关信息。

### 方法二：在 GitHub 上查看
1. 打开 GitHub 上的仓库页面
2. 进入 Pull Request 或 Commits 页面
3. 查看提交记录，如果提交已正确签名，会显示 "Verified"（已验证）标识

## 未签名提交的影响

如果提交没有进行签名验证，可能会导致以下问题：
1. 在一些开源项目或企业项目中，未签名的提交可能不被接受
2. 提交的真实性无法验证，存在安全风险
3. 在团队协作中，无法确认提交者的真实身份
4. 一些项目设置了分支保护规则，要求所有提交必须签名

## 注意事项

1. 保护好私钥文件，不要泄露给他人
2. 忘记密码时可以通过重新生成密钥对解决
3. 更换设备时需要导入原有的密钥对
4. 同一设备上的多个仓库可共享同一密钥对

## 实践练习

完成以上配置后，进行以下实践练习以验证配置是否成功：

1. 在之前创建的个人分支上进行修改(记得同步上游仓库)
2. 添加一个新文件 `signature-practice.md`
3. 在文件中添加以下内容：
   ```markdown
   # 签名练习
   
   这是我配置 Git 签名后的第一次练习提交。
   ```
4. 提交更改并推送到远程仓库：
   ```bash
   git add <你的昵称>-signature-practice.md
   git commit -m "Add signature practice file"
   git push origin <你的昵称>
   ```
5. 在 GitHub 上查看提交记录，确认是否有 "Verified"（已验证）标识

完成练习后，可以将此文件保留在仓库中，作为学习成果的一部分。