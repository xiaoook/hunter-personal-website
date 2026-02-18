# hunter-personal-website

个人网站项目 - 使用 Vue 3、TypeScript 和 Tailwind CSS 构建

## 功能特点

- 📱 响应式设计，支持移动端和桌面端
- 🎨 现代化的 UI 设计
- 🚀 从 GitHub API 自动获取项目信息
- ⚡ 使用 Vite 进行快速开发和构建
- 💻 TypeScript 类型安全

## 快速开始

### 1. 安装依赖

```bash
pnpm install
```

### 2. 配置环境变量

复制 `.env.example` 文件并重命名为 `.env`：

```bash
cp .env.example .env
```

然后编辑 `.env` 文件，填入你的 GitHub 用户名：

```env
# GitHub 配置
VITE_GITHUB_USERNAME=your-github-username

# 要展示的仓库列表（用逗号分隔，留空则自动获取前6个star最多的仓库）
# 支持两种格式：
# 1. repo-name（使用上面配置的用户名）
# 2. owner/repo-name（指定组织或其他用户的仓库）
VITE_FEATURED_REPOS=my-repo,my-org/org-repo,another-user/public-repo

# 社交媒体链接
VITE_GITHUB_URL=https://github.com/your-username
VITE_LINKEDIN_URL=https://linkedin.com/in/your-profile
```

**配置说明：**

- `VITE_GITHUB_USERNAME`: 你的 GitHub 用户名（必填）
- `VITE_FEATURED_REPOS`: 要展示的仓库，支持以下格式：
  - `repo-name` - 你个人账号下的仓库
  - `org-name/repo-name` - 组织或其他用户的仓库
  - 留空 - 自动获取你的前 6 个星标最多的公开仓库
  - 示例：`my-project,my-org/team-project,friend/cool-repo`

### 3. 启动开发服务器

```bash
pnpm dev
```

在浏览器中打开 [http://localhost:5173](http://localhost:5173)

### 4. 构建生产版本

```bash
pnpm build
```

### 5. 预览生产版本

```bash
pnpm preview
```

## 项目结构

```
src/
├── components/         # Vue 组件
│   ├── NavBar.vue     # 导航栏
│   ├── HeroSection.vue     # 首页横幅
│   ├── AboutSection.vue    # 关于我
│   ├── ProjectsSection.vue # 项目展示（从 GitHub 获取）
│   ├── SkillsSection.vue   # 技能专长
│   ├── ContactSection.vue  # 联系方式
│   └── FooterSection.vue   # 页脚
├── router/            # 路由配置
├── App.vue            # 根组件
└── main.ts            # 入口文件
```

## 技术栈

- **框架**: Vue 3 (Composition API)
- **语言**: TypeScript
- **构建工具**: Vite
- **样式**: Tailwind CSS
- **路由**: Vue Router
- **API**: GitHub REST API

## 环境变量说明

所有环境变量必须以 `VITE_` 开头才能在客户端代码中访问（这是 Vite 的安全机制）。

### 配置选项

- **`VITE_GITHUB_USERNAME`**: 你的 GitHub 用户名（必填）
- **`VITE_FEATURED_REPOS`**: 要展示的仓库列表（选填）
  - 留空：自动获取前 6 个星标最多的仓库
  - 填写仓库：只展示指定的仓库，用逗号分隔
  - 支持格式：
    - `repo-name` - 你个人账号下的仓库
    - `org-name/repo-name` - 组织账号下的仓库
    - `username/repo-name` - 其他用户的公开仓库
  - 可以混合使用，例如：`my-repo,my-org/team-project,friend/cool-repo`
- **`VITE_GITHUB_URL`**: 你的 GitHub 主页链接（选填，用于页脚社交媒体图标）
- **`VITE_LINKEDIN_URL`**: 你的 LinkedIn 主页链接（选填，用于页脚社交媒体图标）

**重要提示**: 
- `.env` 文件已被添加到 `.gitignore`，不会被提交到版本控制
- `.env.example` 是模板文件，会被提交到版本控制
- 部署时请在部署平台配置相应的环境变量

## License

MIT

