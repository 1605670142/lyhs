# Git完整教程 - 从零开始上传到GitHub

## 第一步：安装Git

### 1.1 下载Git

访问官网下载：https://git-scm.com/download/win

或者使用国内镜像（更快）：https://registry.npmmirror.com/binary.html?path=git-for-windows/

**推荐下载**：`Git-2.43.0-64-bit.exe`（或最新版本）

### 1.2 安装Git

1. 双击下载的安装包
2. 一路点击 "Next"（使用默认设置即可）
3. 重要选项：
   - ✅ "Git Bash Here" - 右键菜单集成
   - ✅ "Git GUI Here" - 图形界面
   - ✅ 默认编辑器选择 "Vim" 或 "Notepad++"
4. 点击 "Install" 安装
5. 安装完成后点击 "Finish"

### 1.3 验证安装

打开 **PowerShell** 或 **命令提示符**，输入：

```bash
git --version
```

如果显示版本号（如 `git version 2.43.0`），说明安装成功！

---

## 第二步：配置Git

### 2.1 设置用户名和邮箱

打开 **PowerShell**，输入以下命令（替换为你的信息）：

```bash
# 设置用户名（你的GitHub用户名）
git config --global user.name "你的用户名"

# 设置邮箱（你的GitHub注册邮箱）
git config --global user.email "your.email@example.com"
```

**示例**：
```bash
git config --global user.name "zhangsan"
git config --global user.email "zhangsan@example.com"
```

### 2.2 验证配置

```bash
git config --global --list
```

应该看到：
```
user.name=你的用户名
user.email=your.email@example.com
```

### 2.3 配置中文显示（重要！）

```bash
# 让Git正确显示中文文件名
git config --global core.quotepath false

# 设置编码
git config --global gui.encoding utf-8
git config --global i18n.commit.encoding utf-8
git config --global i18n.logoutputencoding utf-8
```

---

## 第三步：创建GitHub仓库

### 3.1 登录GitHub

访问：https://github.com

如果没有账号，点击 "Sign up" 注册

### 3.2 创建新仓库

1. 点击右上角 "+" → "New repository"
2. 填写信息：
   - **Repository name**（仓库名）：如 `lyhs-research`
   - **Description**（描述）：如 `卵叶海桑种群基因组学研究`
   - **Public** 或 **Private**：选择公开或私有
   - ✅ 勾选 "Add a README file"
3. 点击 "Create repository"

### 3.3 获取仓库地址

创建后，你会看到仓库页面，点击绿色的 "Code" 按钮，复制HTTPS地址：

```
https://github.com/你的用户名/lyhs-research.git
```

**保存这个地址，后面会用到！**

---

## 第四步：初始化本地仓库

### 4.1 打开PowerShell

1. 按 `Win + X`，选择 "Windows PowerShell"
2. 或者在开始菜单搜索 "PowerShell"

### 4.2 进入项目目录

```bash
cd D:\yjs\lyhs\qunti
```

**验证**：输入 `pwd` 确认当前目录是 `D:\yjs\lyhs\qunti`

### 4.3 初始化Git仓库

```bash
git init
```

**输出**：
```
Initialized empty Git repository in D:/yjs/lyhs/qunti/.git/
```

这会在当前目录创建一个隐藏的 `.git` 文件夹。

### 4.4 连接远程仓库

```bash
# 添加远程仓库（替换为你的仓库地址）
git remote add origin https://github.com/你的用户名/lyhs-research.git
```

**示例**：
```bash
git remote add origin https://github.com/zhangsan/lyhs-research.git
```

**验证**：
```bash
git remote -v
```

应该看到：
```
origin  https://github.com/你的用户名/lyhs-research.git (fetch)
origin  https://github.com/你的用户名/lyhs-research.git (push)
```

---

## 第五步：添加文件到Git

### 5.1 查看文件状态

```bash
git status
```

会显示很多未跟踪的文件（红色）。

### 5.2 添加文献汇报文件夹

**方法A：只添加文献汇报文件夹**（推荐）

```bash
git add "文献/2025-2026植物重测序文献/文献汇报/"
```

**方法B：添加所有文件**（如果你想上传整个项目）

```bash
git add .
```

### 5.3 再次查看状态

```bash
git status
```

现在文件应该变成绿色（已暂存）。

---

## 第六步：提交更改

### 6.1 提交到本地仓库

```bash
git commit -m "添加Dipteronia活化石文献汇报"
```

**输出示例**：
```
[main (root-commit) abc1234] 添加Dipteronia活化石文献汇报
 15 files changed, 2856 insertions(+)
 create mode 100644 文献/2025-2026植物重测序文献/文献汇报/汇报简版.md
 ...
```

### 6.2 查看提交历史

```bash
git log --oneline
```

---

## 第七步：推送到GitHub

### 7.1 首次推送

```bash
git push -u origin main
```

**如果提示分支名是 master**，使用：
```bash
git push -u origin master
```

### 7.2 输入GitHub凭据

**第一次推送时**，会弹出登录窗口：

1. 选择 "Sign in with your browser"（浏览器登录）
2. 在浏览器中登录GitHub
3. 授权Git访问
4. 返回PowerShell，推送会自动继续

**或者使用Personal Access Token**（如果浏览器登录失败）：

1. 访问：https://github.com/settings/tokens
2. 点击 "Generate new token (classic)"
3. 勾选 `repo` 权限
4. 生成并复制token
5. 在PowerShell中输入：
   - Username: 你的GitHub用户名
   - Password: 粘贴token（不是密码！）

### 7.3 推送成功

看到类似输出：
```
Enumerating objects: 20, done.
Counting objects: 100% (20/20), done.
Delta compression using up to 8 threads
Compressing objects: 100% (15/15), done.
Writing objects: 100% (20/20), 1.50 MiB | 500.00 KiB/s, done.
Total 20 (delta 2), reused 0 (delta 0)
To https://github.com/你的用户名/lyhs-research.git
 * [new branch]      main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
```

---

## 第八步：验证上传

### 8.1 访问GitHub仓库

打开浏览器，访问：
```
https://github.com/你的用户名/lyhs-research
```

### 8.2 检查文件

1. 点击进入 `文献/2025-2026植物重测序文献/文献汇报/`
2. 应该看到：
   - ✅ 汇报简版.md
   - ✅ 文献模板.md
   - ✅ README.md
   - ✅ images/ 文件夹（包含5张图片）

### 8.3 查看Markdown文件

1. 点击 `汇报简版.md`
2. GitHub会自动渲染Markdown
3. **检查图片是否正常显示**

---

## 常见问题解决

### ❌ 问题1：git命令不存在

**原因**：Git未安装或未添加到环境变量

**解决**：
1. 重新安装Git
2. 安装时勾选 "Add Git to PATH"
3. 重启PowerShell

### ❌ 问题2：fatal: not a git repository

**原因**：不在Git仓库目录中

**解决**：
```bash
cd D:\yjs\lyhs\qunti
git init
```

### ❌ 问题3：remote origin already exists

**原因**：已经添加过远程仓库

**解决**：
```bash
# 删除旧的
git remote remove origin

# 重新添加
git remote add origin https://github.com/你的用户名/仓库名.git
```

### ❌ 问题4：图片不显示

**原因**：路径错误或文件未上传

**解决**：
1. 确认 `images` 文件夹已上传
2. 检查路径：`./images/图片1.png`
3. 刷新页面

### ❌ 问题5：中文文件名乱码

**解决**：
```bash
git config --global core.quotepath false
```

### ❌ 问题6：推送失败 - Authentication failed

**原因**：GitHub不再支持密码登录

**解决**：使用Personal Access Token（见第七步7.2）

### ❌ 问题7：文件太大

**原因**：单个文件超过100MB

**解决**：
- 压缩图片
- 或使用Git LFS

---

## 后续更新文件

### 修改文件后推送

```bash
# 1. 查看更改
git status

# 2. 添加更改
git add .

# 3. 提交
git commit -m "更新文献汇报"

# 4. 推送
git push
```

### 拉取远程更改

```bash
git pull
```

---

## 快速命令参考

```bash
# 查看状态
git status

# 添加文件
git add 文件名
git add .                    # 添加所有

# 提交
git commit -m "提交信息"

# 推送
git push

# 拉取
git pull

# 查看历史
git log
git log --oneline           # 简洁版

# 查看远程仓库
git remote -v

# 查看分支
git branch
```

---

## 🎉 完成！

现在你已经成功将文献汇报上传到GitHub了！

**下一步**：
- 分享你的GitHub仓库链接给导师或同学
- 继续添加更多研究内容
- 使用GitHub进行版本管理

**需要帮助？**
- GitHub官方文档：https://docs.github.com/cn
- Git教程：https://www.liaoxuefeng.com/wiki/896043488029600

---

**制作时间**：2026年4月6日
**适用对象**：Git初学者
