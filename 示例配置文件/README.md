# 示例配置文件说明

本目录包含了零成本博客部署方案中需要用到的各种配置文件模板。

## 📁 文件清单

### 1. hexo-config-example.yml
**用途：** Hexo 博客的主配置文件  
**使用方法：**
```bash
# 在你的 Hexo 博客项目根目录
cp 此文件内容 _config.yml
# 然后根据实际情况修改域名、标题等信息
```

**主要配置项：**
- 网站基本信息（标题、描述、作者）
- URL 配置（域名、永久链接格式）
- 主题设置
- SEO、RSS、搜索等扩展功能

### 2. github-actions-deploy-example.yml
**用途：** GitHub Actions 自动部署脚本  
**使用方法：**
```bash
# 在你的 Hexo 博客项目根目录
mkdir -p .github/workflows
cp 此文件 .github/workflows/deploy.yml
# 修改最后的 cname 为你的域名
```

**功能：**
- 监听 main 分支的 push 事件
- 自动安装依赖并构建 Hexo
- 将生成的静态文件部署到 gh-pages 分支
- GitHub Pages 自动从 gh-pages 分支发布

### 3. vercel-config-example.json
**用途：** Vercel 部署配置  
**使用方法：**
```bash
# 在你的 Hexo 博客项目根目录
cp 此文件 vercel.json
# 可选，Vercel 通常能自动识别 Hexo 项目
```

**功能：**
- 指定 Node.js 版本
- 配置构建命令和输出目录
- 设置路由规则

## 🚀 快速使用流程

### 步骤 1：初始化 Hexo 项目
```bash
npm install -g hexo-cli
hexo init my-blog
cd my-blog
npm install
```

### 步骤 2：应用配置文件
```bash
# 复制并修改 Hexo 配置
# 编辑 _config.yml，填入你的域名和基本信息

# 复制 GitHub Actions 配置
mkdir -p .github/workflows
# 将 github-actions-deploy-example.yml 内容复制到
# .github/workflows/deploy.yml

# （可选）复制 Vercel 配置
# 将 vercel-config-example.json 内容复制到 vercel.json
```

### 步骤 3：安装常用插件
```bash
# SEO
npm install hexo-generator-sitemap --save
npm install hexo-generator-baidu-sitemap --save

# RSS
npm install hexo-generator-feed --save

# 搜索
npm install hexo-generator-searchdb --save

# Git 部署（如需本地部署）
npm install hexo-deployer-git --save
```

### 步骤 4：推送到 GitHub
```bash
git init
git add .
git commit -m "Initial blog setup"
git remote add origin https://github.com/你的用户名/你的仓库.git
git push -u origin main
```

### 步骤 5：配置 GitHub Pages
1. 进入仓库 Settings → Pages
2. Source 选择 `gh-pages` 分支
3. Custom domain 填写你的域名
4. 保存并等待部署完成

### 步骤 6：配置 Vercel（可选）
1. 访问 [vercel.com](https://vercel.com)
2. 导入你的 GitHub 仓库
3. Vercel 会自动识别 Hexo 项目并部署
4. 配置自定义域名（如需要）

## 📝 常见问题

### Q: 需要修改哪些配置？
**A:** 主要需要修改：
- `_config.yml` 中的 `url`（改为你的域名）
- `_config.yml` 中的网站信息（标题、描述、作者）
- `.github/workflows/deploy.yml` 中的 `cname`（改为你的域名）

### Q: 主题如何配置？
**A:** 
1. 下载主题到 `themes/` 目录
2. 修改 `_config.yml` 中的 `theme` 字段
3. 根据主题文档配置主题的 `_config.yml`

### Q: 如何测试配置是否正确？
**A:**
```bash
hexo clean
hexo generate
hexo server
# 访问 http://localhost:4000 查看效果
```

### Q: GitHub Actions 部署失败怎么办？
**A:**
1. 检查仓库 Actions 标签页的日志
2. 确认 package.json 文件存在
3. 确认所有依赖都在 package.json 中
4. 检查 Node.js 版本兼容性

## 🔗 相关链接

- [Hexo 官方文档](https://hexo.io/zh-cn/docs/)
- [GitHub Actions 文档](https://docs.github.com/cn/actions)
- [Vercel 文档](https://vercel.com/docs)
- [完整部署方案](../零成本博客部署方案.md)
