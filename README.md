# 东南亚风情餐厅网站 - 部署指南

![东南亚风情餐厅](https://space.coze.cn/api/coze_space/gen_image?image_size=landscape_16_9&prompt=Southeast%20Asian%20restaurant%20interior%20warm%20lighting%20wooden%20furniture%20traditional%20decorations&sign=d6d63a4b689e14636517b29f4fcc1430)

## 项目介绍
东南亚风情餐厅网站是一个基于React 18和TypeScript构建的现代化单页应用，展示泰国、缅甸和台湾美食，提供菜单浏览、联系信息和管理员后台功能。

## 部署指南：使用GitHub Pages

### 前提条件
- Git已安装
- Node.js (v14.0.0+) 和pnpm已安装
- GitHub账号

### 步骤1：准备项目

1. **克隆仓库**（如尚未创建）
   ```bash
   git clone https://github.com/你的用户名/你的仓库名.git
   cd 你的仓库名
   ```

2. **安装依赖**
   ```bash
   pnpm install
   ```

3. **测试本地运行**
   ```bash
   pnpm dev
   ```
   访问 http://localhost:3000 确认网站正常运行

### 步骤2：配置GitHub仓库

1. **创建GitHub仓库**
   - 登录GitHub，点击右上角"+"图标，选择"New repository"
   - 填写仓库名称（如"southeast-asian-restaurant"）
   - 添加描述（可选）
   - 选择"Public"
   - 点击"Create repository"

2. **关联本地项目到GitHub仓库**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/你的用户名/你的仓库名.git
   git push -u origin main
   ```

### 步骤3：配置部署环境

1. **安装部署依赖**
   ```bash
   pnpm add -D gh-pages
   ```

2. **修改package.json**
   添加以下字段（替换为你的GitHub信息）：
   ```json
   "homepage": "https://你的用户名.github.io/你的仓库名",
   "scripts": {
     "predeploy": "pnpm build",
     "deploy": "gh-pages -d dist"
   }
   ```

3. **修改vite.config.ts**
   添加base配置（替换为你的仓库名）：
   ```typescript
   export default defineConfig({
     base: '/你的仓库名/',
     // 其他配置...
   })
   ```

### 步骤4：部署到GitHub Pages

1. **执行部署命令**
   ```bash
   pnpm deploy
   ```

2. **配置GitHub Pages**
   - 在GitHub仓库页面，点击"Settings"
   - 在左侧导航栏中选择"Pages"
   - 在"Source"部分，选择"gh-pages"分支，然后点击"Save"
   - 等待几分钟，页面会显示你的网站URL

3. **访问你的网站**
   部署完成后，访问: https://你的用户名.github.io/你的仓库名

### 步骤5：更新网站（后续维护）

每次修改代码后，执行以下命令更新网站：
```bash
git add .
git commit -m "描述你的修改"
git push
pnpm deploy
```

### 管理员登录信息
- 默认用户名: admin
- 默认密码: admin123
- 登录后可管理菜单、查看订单和更新餐厅信息

### 故障排除

1. **部署后页面空白**
   - 检查浏览器控制台是否有错误
   - 确认vite.config.ts中的base配置正确
   - 确保package.json中的homepage配置正确

2. **资源加载失败**
   - 检查文件路径是否使用相对路径
   - 确认图片等静态资源引用正确

3. **部署命令失败**
   - 确保gh-pages已安装
   - 检查GitHub仓库权限
   - 确认dist目录已正确生成

## 技术栈
- React 18
- TypeScript
- Tailwind CSS
- Vite
- React Router v7
- Font Awesome