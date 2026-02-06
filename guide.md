# 个人网站使用指南

> 基于 Jekyll + Academic Pages 模板的学术个人网站

## 一、项目简介

- **网站地址**：https://ztyf.github.io
- **技术栈**：Jekyll、GitHub Pages
- **模板**：Academic Pages（源自 Minimal Mistakes）

---

## 二、本地开发

### 环境准备

```bash
# macOS
brew install ruby
brew install node
gem install bundler

# Homebrew 安装的 Ruby 需加入 PATH（keg-only）
echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### 启动本地服务

```bash
cd zhoutyf.github.io

# 首次运行：配置本地 bundle 路径（避免权限问题）
bundle config set --local path 'vendor/bundle'

# 安装依赖
bundle install

# 启动服务
bundle exec jekyll serve -l -H localhost
```

访问：http://localhost:4000

---

## 三、目录结构说明

| 目录/文件 | 说明 |
|-----------|------|
| `_config.yml` | 网站全局配置（标题、作者、链接等） |
| `_includes/` | 可复用组件（如侧边栏、页脚） |
| `_layouts/` | 页面布局模板 |
| `_pages/` | 静态页面（关于、简历等） |
| `_posts/` | 博客文章 |
| `_publications/` | 论文/出版物 |
| `_talks/` | 演讲/报告 |
| `_teaching/` | 教学信息 |
| `_data/` | 数据文件（导航、简历 JSON 等） |
| `assets/` | CSS、JS、字体等静态资源；修改 `assets/js/_main.js` 后需运行 `npm run build:js` |
| `_sass/custom.scss` | 自定义样式（侧边栏、正文链接等） |
| `images/` | 图片资源（建议使用英文文件名） |
| `files/` | 可下载文件（PDF 等），CV 简历为 `files/cv.pdf` |
| `guide.md` | 本使用指南（已排除于 Jekyll 构建） |

---

## 四、常用修改

### 1. 修改个人信息

编辑 `_config.yml` 中的 `author` 部分：

```yaml
author:
  avatar: "avatar.jpg"    # 头像文件名，请使用英文命名避免编码问题
  name: "Your Name"
  # name_zh: "中文名"    # 显示在英文名下方（可选，取消注释启用）
  bio: "Your Title"
  emails:                            # 多个邮箱
    - address: "your@gmail.com"
      label: "Gmail"
    - address: "name@connect.hku.hk"
      label: "HKU"
  location:
    name: "Your Institution"
    url: "https://..."
  github: "your-username"
  orcid: "https://orcid.org/..."
```

### 2. 修改主页

编辑 `_pages/about.md`，可修改：
- **About Me**：个人简介
- **Research Interests**：研究方向
- **News**：近期动态
- **Links**：快捷链接

### 3. 添加博客文章

在 `_posts/` 下新建文件，命名格式：`YYYY-MM-DD-标题.md`

```markdown
---
title: "文章标题"
date: 2025-02-06
categories: [随笔]
tags: [标签1, 标签2]
---

正文内容...
```

### 4. 添加论文

在 `_publications/` 下新建 `.md` 文件，参考现有格式填写 front matter 和内容。

### 5. 修改导航菜单

编辑 `_data/navigation.yml`，增删或调整菜单项。注释掉某项即可从导航栏隐藏（页面仍可通过直接链接访问）：

```yaml
# 当前显示：Home、CV、Publications、Projects、Blog
# 当前已隐藏：Talks、Teaching、Guide
# 取消注释即可恢复显示
- title: "Home"
  url: /
- title: "CV"
  url: /files/cv.pdf
- title: "Publications"
  url: /publications/
- title: "Projects"
  url: /portfolio/
- title: "Blog"
  url: /year-archive/
# - title: "Talks"
#   url: /talks/
# - title: "Teaching"
#   url: /teaching/
# - title: "Guide"
#   url: /markdown/
```

---

## 五、常见问题

| 问题 | 解决方案 |
|------|----------|
| `zsh: command not found: bundle` | 确保已执行 `export PATH="/opt/homebrew/opt/ruby/bin:$PATH"` 或加入 `~/.zshrc` |
| `Gem::FilePermissionError` | 运行 `bundle config set --local path 'vendor/bundle'` 后重新 `bundle install` |
| `rdiscount` 编译失败 | 项目已移除该依赖，使用 kramdown 解析 Markdown |
| `Encoding::UndefinedConversionError` | 图片、文件名请使用英文，避免中文（如 `头像.jpg` → `avatar.jpg`） |

---

## 六、部署发布

推送到 GitHub 后自动构建发布：

```bash
git add .
git commit -m "更新说明"
git push origin master
```

**注意**：修改 `assets/js/_main.js` 后需运行 `npm run build:js` 重新生成 `main.min.js`。

---

## 七、其他

- **导航栏**：当前显示 Home、CV、Publications、Projects、Blog；已隐藏 Talks、Teaching、Guide
- **CV**：点击直接打开/下载 `files/cv.pdf`，替换该文件即可更新简历；当前版本更新至 2026 年 2 月
- **Publications**：已配置论文列表，可按年份分组展示；Projects、Blog 为占位页
- **上传 PDF**：放入 `files/` 目录，访问 `https://ztyf.github.io/files/文件名.pdf`
- **主题**：默认白色模式；在 `_config.yml` 中修改 `site_theme`（如 `default`、`air`）
- **正文链接**：保持文字颜色、仅下划线（见 `_sass/custom.scss`）
- **更多帮助**：https://academicpages.github.io/

**使用 ztyf.github.io 用户页**：需将 GitHub 仓库重命名为 `ztyf.github.io`（Settings → General → Repository name），然后更新本地 remote：`git remote set-url origin https://github.com/ztyf/ztyf.github.io.git`
