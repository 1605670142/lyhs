# 如何查询GitHub用户名和邮箱

## 方法1：在GitHub网站查看（推荐）

### 步骤1：登录GitHub

访问：https://github.com

如果还没有账号，点击 "Sign up" 注册一个。

### 步骤2：查看用户名

登录后，有3种方法查看：

**方法A：看右上角**
1. 点击右上角你的头像
2. 会显示：`Signed in as 你的用户名`

**方法B：看地址栏**
1. 点击右上角头像
2. 点击 "Your profile"（你的个人资料）
3. 浏览器地址栏显示：`https://github.com/你的用户名`
   - 例如：`https://github.com/zhangsan`
   - 用户名就是：`zhangsan`

**方法C：看个人主页**
1. 点击右上角头像 → "Your profile"
2. 页面顶部大字显示的就是你的用户名

### 步骤3：查看邮箱

1. 点击右上角头像
2. 点击 "Settings"（设置）
3. 左侧菜单点击 "Emails"
4. 看到 "Primary email address"（主邮箱地址）
   - 例如：`zhangsan@qq.com`

---

## 方法2：如果已经配置过Git

### 查看当前配置

打开PowerShell，输入：

```bash
git config --global --list
```

**输出示例**：
```
user.name=zhangsan
user.email=zhangsan@qq.com
core.quotepath=false
```

### 单独查看用户名

```bash
git config --global user.name
```

**输出**：`zhangsan`

### 单独查看邮箱

```bash
git config --global user.email
```

**输出**：`zhangsan@qq.com`

---

## 方法3：如果忘记了GitHub账号

### 找回用户名

1. 访问：https://github.com/login
2. 点击 "Forgot username?"
3. 输入注册邮箱
4. GitHub会发送用户名到你的邮箱

### 找回密码

1. 访问：https://github.com/login
2. 点击 "Forgot password?"
3. 输入邮箱或用户名
4. 按提示重置密码

---

## 完整配置示例

### 示例1：使用QQ邮箱

```bash
git config --global user.name "zhangsan"
git config --global user.email "123456789@qq.com"
git config --global core.quotepath false
```

### 示例2：使用163邮箱

```bash
git config --global user.name "lisi"
git config --global user.email "lisi@163.com"
git config --global core.quotepath false
```

### 示例3：使用Gmail

```bash
git config --global user.name "wangwu"
git config --global user.email "wangwu@gmail.com"
git config --global core.quotepath false
```

---

## 验证配置是否成功

### 方法1：查看所有配置

```bash
git config --global --list
```

应该看到：
```
user.name=你设置的用户名
user.email=你设置的邮箱
core.quotepath=false
```

### 方法2：分别查看

```bash
# 查看用户名
git config --global user.name

# 查看邮箱
git config --global user.email
```

---

## 常见问题

### Q1: 用户名和邮箱必须和GitHub一致吗？

**用户名**：
- ✅ 建议一致，但不强制
- 主要用于显示提交者信息

**邮箱**：
- ⚠️ 建议使用GitHub注册邮箱
- 这样GitHub可以关联你的提交记录
- 如果不一致，提交记录不会显示你的头像

### Q2: 可以修改配置吗？

可以！重新运行配置命令即可覆盖：

```bash
git config --global user.name "新用户名"
git config --global user.email "新邮箱"
```

### Q3: 配置保存在哪里？

Windows系统保存在：
```
C:\Users\你的用户名\.gitconfig
```

可以用记事本打开查看。

### Q4: 为什么要配置 core.quotepath false？

这是为了让Git正确显示中文文件名，否则中文会显示为乱码：
```
# 不配置时：
\346\226\207\347\214\256/...

# 配置后：
文献/...
```

---

## 快速检查清单

在配置前，准备好以下信息：

- [ ] GitHub用户名：`_______________`
- [ ] GitHub邮箱：`_______________`

然后在PowerShell中执行：

```bash
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱"
git config --global core.quotepath false
```

验证：

```bash
git config --global --list
```

---

## 实际操作演示

### 假设你的信息是：
- GitHub用户名：`zhangsan`
- GitHub邮箱：`zhangsan@qq.com`

### 完整操作步骤：

1. **打开PowerShell**
   - 按 `Win + X`
   - 选择 "Windows PowerShell"

2. **输入配置命令**（一行一行输入，每行按回车）

```bash
git config --global user.name "zhangsan"
```
按回车，没有输出是正常的

```bash
git config --global user.email "zhangsan@qq.com"
```
按回车，没有输出是正常的

```bash
git config --global core.quotepath false
```
按回车，没有输出是正常的

3. **验证配置**

```bash
git config --global --list
```

**应该看到**：
```
user.name=zhangsan
user.email=zhangsan@qq.com
core.quotepath=false
...（可能还有其他配置）
```

4. **配置成功！** ✅

---

## 下一步

配置完成后，继续执行上传步骤：

1. 进入项目目录：`cd D:\yjs\lyhs\qunti`
2. 初始化Git：`git init`
3. 添加远程仓库：`git remote add origin https://github.com/你的用户名/仓库名.git`
4. 添加文件：`git add "文献/2025-2026植物重测序文献/文献汇报/"`
5. 提交：`git commit -m "添加文献汇报"`
6. 推送：`git push -u origin main`

详细步骤见：[快速上传指南.md](./快速上传指南.md)

---

**需要帮助？**

如果还有疑问，可以：
1. 查看 [Git完整教程_从零开始.md](./Git完整教程_从零开始.md)
2. 访问GitHub帮助：https://docs.github.com/cn
