# Hugo 快速开始指南

## 1. 安装 Hugo

```bash
# macOS
brew install hugo

# 验证安装
hugo version
```

## 2. 测试本地运行

```bash
# 进入 Hugo 目录
cd hugo

# 启动开发服务器
hugo server

# 访问 http://localhost:1313
```

## 3. 复制静态资源

确保 `assets` 文件夹在 `hugo/static/` 目录下：

```bash
# 从项目根目录
cp -r assets hugo/static/
```

## 4. 构建网站

```bash
cd hugo
hugo

# 构建的文件在 public/ 目录
```

## 5. 部署到 GitHub Pages

### 选项 A: 使用 GitHub Actions（推荐）

已经创建了 `.github/workflows/hugo.yml`，只需：

1. 确保 GitHub Pages 设置中 Source 选择 "GitHub Actions"
2. 推送代码到 master 分支
3. GitHub Actions 会自动构建和部署

### 选项 B: 手动部署

```bash
# 构建
cd hugo
hugo

# 将 public/ 内容复制到根目录
cp -r public/* ../

# 提交
cd ..
git add .
git commit -m "Deploy Hugo site"
git push
```

## 修改内容

### 个人信息
编辑 `hugo/config.yaml` 的 `params` 部分

### 新闻
编辑 `hugo/data/news.yml`

### 项目
编辑 `hugo/data/projects.yml`

### 其他内容
- `hugo/data/biography.yml`
- `hugo/data/teaching.yml`
- `hugo/data/activities.yml`

## 优势

✅ **无需 Ruby/Node.js** - 只需要 Hugo 单文件  
✅ **构建速度快** - 通常 < 1 秒  
✅ **易于修改** - 编辑 YAML 和 Markdown  
✅ **GitHub Pages 支持** - 通过 Actions 自动部署  

## 下一步

1. 安装 Hugo: `brew install hugo`
2. 测试: `cd hugo && hugo server`
3. 配置 GitHub Pages 使用 GitHub Actions
4. 开始使用！

