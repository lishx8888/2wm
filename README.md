# 项目介绍

这是一个纯静态资源项目，包含基本的网站结构和必要的资源文件。

## 项目结构

```
├── css/
│   ├── font-awesome.min.css
│   └── tailwind.css
├── fonts/
│   ├── fontawesome-webfont.eot
│   ├── fontawesome-webfont.ttf
│   ├── fontawesome-webfont.woff
│   └── fontawesome-webfont.woff2
├── js/
│   ├── qrcode.js
│   └── qrcode.min.js
└── index.html
```

## 本地运行

1. 直接在浏览器中打开 `index.html` 文件
2. 或者使用本地服务器运行（推荐）：

   ```bash
   # 使用Python内置服务器
   python -m http.server 8000
   
   # 或使用Node.js的http-server
   npx http-server -p 8000
   ```

3. 访问 `http://localhost:8000` 查看网站

## 部署到Cloudflare

### 方法一：使用Cloudflare Pages

1. **准备工作**：
   - 确保你有一个Cloudflare账户
   - 将项目代码上传到GitHub或GitLab仓库

2. **创建Cloudflare Pages项目**：
   - 登录Cloudflare控制台
   - 导航到「Pages」部分
   - 点击「Create a project」按钮
   - 选择你的代码仓库

3. **配置构建设置**：
   - **Framework preset**：选择「None」（因为这是纯静态项目）
   - **Build command**：留空（不需要构建步骤）
   - **Build output directory**：留空（默认为根目录）
   - 点击「Save and Deploy」

4. **部署完成**：
   - Cloudflare会自动部署你的网站
   - 部署完成后，你会获得一个 `*.pages.dev` 域名
   - 你可以在「Custom domains」部分添加自定义域名

### 方法二：使用Cloudflare Workers Sites

1. **安装Wrangler CLI**：
   ```bash
   npm install -g @cloudflare/wrangler
   ```

2. **初始化项目**：
   ```bash
   wrangler init --site
   ```

3. **配置wrangler.toml**：
   ```toml
   name = "your-project-name"
type = "webpack"

   account_id = "your-account-id"
   workers_dev = true
   route = "your-domain.com/*"

   [site]
   bucket = "."
   entry-point = "workers-site"
   ```

4. **部署项目**：
   ```bash
   wrangler publish
   ```

## 技术栈

- HTML5
- Tailwind CSS
- Font Awesome
- QRCode.js

## 注意事项

- 这是一个纯静态项目，没有后端服务
- 所有资源文件都已包含在项目中，无需额外安装依赖
- 部署到Cloudflare后，网站会自动获得CDN加速和SSL证书