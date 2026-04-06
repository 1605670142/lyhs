# GitHub上传指南

## 方法1：通过GitHub网页上传（最简单）

### 步骤：

1. **登录GitHub**，进入你的仓库

2. **创建文件夹结构**
   - 点击 "Add file" → "Create new file"
   - 在文件名处输入：`文献汇报/README.md`
   - 这会自动创建 `文献汇报` 文件夹

3. **上传Markdown文件**
   - 进入 `文献汇报` 文件夹
   - 点击 "Add file" → "Upload files"
   - 拖拽上传：
     - 汇报简版.md
     - 文献模板.md
     - README.md

4. **上传图片文件夹**
   - 在 `文献汇报` 文件夹中
   - 点击 "Add file" → "Upload files"
   - 拖拽整个 `images` 文件夹（包含5张图片）
   - 或者逐个上传图片到 `images` 文件夹

5. **提交更改**
   - 填写提交信息：如 "添加Dipteronia文献汇报"
   - 点击 "Commit changes"

## 方法2：通过Git命令行（推荐）

### 前提条件：
- 已安装Git
- 已配置GitHub账号

### 步骤：

```bash
# 1. 进入你的本地仓库目录
cd D:\yjs\lyhs\qunti

# 2. 初始化Git（如果还没有）
git init

# 3. 添加远程仓库（替换为你的仓库地址）
git remote add origin https://github.com/你的用户名/你的仓库名.git

# 4. 添加文件到暂存区
git add "文献/2025-2026植物重测序文献/文献汇报/"

# 5. 提交更改
git commit -m "添加Dipteronia活化石文献汇报"

# 6. 推送到GitHub
git push -u origin main
# 如果是master分支，使用：git push -u origin master
```

## 方法3：使用GitHub Desktop（最友好）

### 步骤：

1. **下载并安装** [GitHub Desktop](https://desktop.github.com/)

2. **打开仓库**
   - File → Add Local Repository
   - 选择 `D:\yjs\lyhs\qunti`

3. **查看更改**
   - 左侧会显示所有新增/修改的文件
   - 勾选 `文献汇报` 文件夹下的所有文件

4. **提交并推送**
   - 填写提交信息
   - 点击 "Commit to main"
   - 点击 "Push origin"

## 验证图片显示

上传后，在GitHub上打开 `汇报简版.md`，应该能看到：

✅ 图片1：基因组进化圈图
✅ 图片2：种群结构地图
✅ 图片4：种群历史曲线
✅ 图片5：遗传负荷分析

## 常见问题

### Q1: 图片不显示？
**原因**：路径错误或文件未上传

**解决**：
- 确认 `images` 文件夹与 `汇报简版.md` 在同一目录
- 确认图片文件名正确（图片1.png, 图片2.png等）
- 检查路径是否为：`./images/图片1.png`

### Q2: 中文文件名显示乱码？
**原因**：Git编码问题

**解决**：
```bash
git config --global core.quotepath false
```

### Q3: 文件太大无法上传？
**原因**：GitHub单文件限制100MB

**解决**：
- 压缩图片（使用TinyPNG等工具）
- 使用Git LFS（大文件存储）

## 推荐的仓库结构

```
你的仓库/
├── README.md
├── 文献/
│   └── 2025-2026植物重测序文献/
│       └── 文献汇报/
│           ├── README.md
│           ├── 汇报简版.md
│           ├── 文献模板.md
│           └── images/
│               ├── 图片1.png
│               ├── 图片2.png
│               ├── 图片3.png
│               ├── 图片4.png
│               └── 图片5.png
```

## 最佳实践

1. ✅ 使用英文文件夹名（如 `images` 而非 `缺失的图片`）
2. ✅ 使用相对路径（`./images/图片1.png`）
3. ✅ 添加README.md说明文件
4. ✅ 图片文件名简洁明了
5. ✅ 提交信息清晰描述更改内容

---

**提示**：如果你是第一次使用GitHub，推荐使用"方法1：网页上传"或"方法3：GitHub Desktop"。
