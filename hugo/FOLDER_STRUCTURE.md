# Hugo 文件夹结构说明

## 📁 文件夹作用详解

### ✅ **必需文件夹（核心）**

#### 1. `content/` - 内容源文件
**作用**: 存储所有 Markdown 内容文件
- `content/blogs/` - 博客文章
- `content/work/` - 工作经历页面
- `content/education/` - 教育经历页面
- **修改方式**: 直接编辑 Markdown 文件

#### 2. `data/` - 数据文件
**作用**: 存储 YAML 格式的结构化数据
- `work.yml` - 工作经历数据
- `education.yml` - 教育经历数据
- `projects.yml` - 项目数据
- `biography.yml` - 传记数据
- `activities.yml` - 活动数据
- `teaching.yml` - 教学数据
- `news.yml` - 新闻数据
- **修改方式**: 编辑 YAML 文件，这是**主要的内容修改位置**

#### 3. `layouts/` - 模板文件
**作用**: HTML 模板，控制页面如何渲染
- `layouts/index.html` - 首页模板
- `layouts/work/single.html` - 工作经历页面模板
- `layouts/education/single.html` - 教育经历页面模板
- `layouts/partials/` - 可复用的组件（导航、页脚等）
- **修改方式**: 修改 HTML 模板来改变页面结构

#### 4. `static/` - 静态资源（源文件）
**作用**: 存储 CSS、JS、图片、PDF 等静态文件
- `static/assets/css/` - CSS 样式文件
- `static/assets/js/` - JavaScript 文件
- `static/assets/data/` - PDF、图片等资源
- **重要**: 这是**源文件**，Hugo 构建时会复制到 `public/`
- **修改方式**: 直接编辑这些文件

#### 5. `config.yaml` - 配置文件
**作用**: 网站配置（菜单、个人信息、参数等）
- **修改方式**: 编辑 YAML 文件

---

### ⚠️ **重复文件夹（构建输出）**

#### 6. `public/` - 构建输出（⚠️ 重复，自动生成）
**作用**: Hugo 构建后生成的完整静态网站
- **内容**: 包含所有 HTML、CSS、JS、图片（从 `static/` 复制）
- **大小**: ~13MB（与 `static/` 相同）
- **状态**: 
  - ✅ 已在 `.gitignore` 中（不会被提交到 Git）
  - ✅ 每次运行 `hugo` 命令时自动重新生成
  - ❌ **不要手动修改**，会被覆盖
- **用途**: 
  - 本地预览
  - GitHub Actions 部署时使用
  - **可以删除**，运行 `hugo` 会重新生成

**与 `static/` 的关系**:
```
static/assets/css/style.css  (源文件)
         ↓ (Hugo 构建时复制)
public/assets/css/style.css  (输出文件，内容相同)
```

---

### 📝 **可选文件夹**

#### 7. `themes/` - 主题文件夹
**作用**: 存储 Hugo 主题（如果有使用）
- **当前状态**: 空文件夹
- **说明**: 本项目使用自定义模板，不使用主题
- **建议**: 可以删除（空文件夹）

#### 8. `archetypes/` - 内容模板
**作用**: 创建新内容时的模板
- **当前状态**: 可能为空
- **说明**: 用于 `hugo new` 命令生成新页面
- **建议**: 可以保留（如果使用 `hugo new` 命令）

---

## 🔍 重复内容分析

### 重复项 1: `static/assets/` ↔ `public/assets/`
- **原因**: `public/assets/` 是 Hugo 从 `static/assets/` 复制生成的
- **大小**: 两者都是 ~13MB
- **处理**: 
  - ✅ `public/` 已在 `.gitignore` 中
  - ✅ 只需维护 `static/` 中的文件
  - ✅ `public/` 会自动同步

### 重复项 2: `public/` 中的 HTML 文件
- **原因**: 由 `content/` + `layouts/` + `data/` 生成
- **处理**: 
  - ✅ 不要手动编辑 `public/` 中的 HTML
  - ✅ 修改源文件（`content/`, `layouts/`, `data/`）后重新构建

---

## 📊 文件夹大小对比

```
static/    13MB  (源文件，需要版本控制)
public/    13MB  (构建输出，已忽略)
```

---

## 🗑️ 可以删除的文件夹/文件

### 可以删除（不影响功能）:
1. ✅ `public/` - 可以删除，运行 `hugo` 会重新生成
2. ✅ `themes/` - 空文件夹，可以删除
3. ✅ `.hugo_build.lock` - 锁定文件，可以删除（会自动重新生成）

### 不能删除（必需）:
- ❌ `content/` - 内容源文件
- ❌ `data/` - 数据文件
- ❌ `layouts/` - 模板文件
- ❌ `static/` - 静态资源源文件
- ❌ `config.yaml` - 配置文件

---

## 🔄 工作流程

```
1. 编辑源文件:
   ├── content/*.md        (Markdown 内容)
   ├── data/*.yml          (数据文件) ⭐ 主要修改位置
   ├── layouts/*.html     (模板)
   └── static/assets/*     (CSS, JS, 图片)

2. 运行构建:
   hugo

3. 生成输出:
   public/                 (自动生成，包含所有文件)

4. 部署:
   GitHub Actions 自动部署 public/ 到 GitHub Pages
```

---

## 💡 最佳实践

1. **只修改源文件**:
   - ✅ `data/*.yml` - 修改内容
   - ✅ `static/assets/*` - 修改样式和资源
   - ✅ `layouts/*.html` - 修改模板
   - ❌ 不要修改 `public/` 中的文件

2. **清理构建文件**:
   ```bash
   # 删除 public/ 文件夹（可选）
   rm -rf hugo/public
   
   # 重新构建
   cd hugo && hugo
   ```

3. **版本控制**:
   - ✅ 提交: `content/`, `data/`, `layouts/`, `static/`, `config.yaml`
   - ❌ 忽略: `public/` (已在 .gitignore 中)

---

## 📝 总结

| 文件夹 | 作用 | 是否重复 | 需要维护 |
|--------|------|---------|---------|
| `content/` | Markdown 内容 | ❌ | ✅ |
| `data/` | YAML 数据 | ❌ | ✅ ⭐ |
| `layouts/` | HTML 模板 | ❌ | ✅ |
| `static/` | 静态资源源文件 | ❌ | ✅ |
| `public/` | 构建输出 | ✅ (与 static 重复) | ❌ |
| `themes/` | 主题（空） | ❌ | ❌ 可删除 |
| `archetypes/` | 内容模板 | ❌ | ⚠️ 可选 |

**核心要点**: 
- `static/` 是源文件，需要维护
- `public/` 是输出文件，自动生成，可以删除
- 主要修改位置: `data/*.yml` 文件

