# AI 工具年鉴 · The AI Atlas

一份免登录、纯静态的 AI 工具导航站：聚合 **59 款热门 AI 工具**，九大分类（九卷）、编辑精选、即时检索、定价筛选与本地收藏（点击卡片右上角的「藏」字朱印即完成收藏）。

整个网站就是 **一个 `index.html`**（全部样式与脚本内联），零依赖、零构建，可直接托管到任何静态网站服务。

## 本地预览

直接双击 `index.html` 即可；或起一个本地服务：

```bash
python -m http.server 8080   # 打开 http://localhost:8080
```

## 免费部署方案对比

| 方案 | 费用 | 大陆直连访问 | 上手难度 | 备注 |
|---|---|---|---|---|
| **GitHub Pages**（推荐） | 免费 | 一般，不稳定时可绑自定义域名 | ★★☆ | 有 GitHub 账号即可；本项目自带部署文档 |
| Vercel | 免费 | `*.vercel.app` 默认域名时好时坏 | ★★☆ | 全球 CDN，与 Git 仓库集成顺滑 |
| Netlify | 免费 | 类似 Vercel | ★☆☆ | 打开网页拖拽文件夹即可发布，最快 |
| Cloudflare Pages | 免费 | 一般 | ★★☆ | 带宽不限量，自带全球边缘网络 |
| 腾讯 EdgeOne Pages | 免费 | **好（国内节点）** | ★★☆ | 需腾讯云账号，国内访问体验首选 |

> 提示：大陆访问 `github.io` / `vercel.app` / `netlify.app` 等默认域名速度不稳定；绑定自定义域名，或选择 EdgeOne Pages，可显著改善。

## 部署到 GitHub Pages（推荐）

### 方式 A：命令行（已安装 GitHub CLI 并登录）

在本文件夹内依次执行：

```bash
git init -b main
git add .
git commit -m "feat: AI 工具年鉴创刊号"
gh repo create ai-atlas --public --source=. --push
gh api -X POST repos/{owner}/ai-atlas/pages -f "source[branch]=main" -f "source[path]=/"
# 稍等 1–2 分钟，访问 https://<你的用户名>.github.io/ai-atlas/
```

> 首次使用 gh 需先登录：`gh auth login`（按提示走浏览器授权即可）。

### 方式 B：网页操作（无需命令行）

1. 打开 github.com → 右上角 **New repository**，命名 `ai-atlas`，选 **Public**，创建；
2. 在新仓库页点 **uploading an existing file**，把本文件夹的 `index.html`、`README.md`、`.nojekyll` 三个文件拖进去，点 **Commit changes**；
3. 进入 **Settings → Pages**，Source 选 **Deploy from a branch**，分支选 `main` / `(root)`，点 **Save**；
4. 稍等 1–2 分钟，访问 `https://<你的用户名>.github.io/ai-atlas/`。

## 其他平台要点

- **Netlify**：打开 `app.netlify.com/drop`，把整个文件夹拖进网页，10 秒后得到一个 `*.netlify.app` 网址，无需注册即可先发布。
- **Vercel / Cloudflare Pages**：注册后 Import Git 仓库（或直接上传），框架预设选 **Other**，构建命令留空，输出目录为根目录 `/`。
- **EdgeOne Pages**：腾讯云控制台创建站点，上传 `index.html` 或绑定 Git 仓库，默认分配 `*.edgeone.app` 域名。

## 自定义

- **增改工具**：编辑 `index.html` 里的 `TOOLS` 数组（名称 / 域名 / 一句话简介 / 分类 / 定价 / 是否力荐），分类在 `CATS` 中调整；
- **换主题色**：改 CSS 变量 `--red`（朱红）与 `--paper`（纸色）即可整站换肤；
- **收藏数据**：仅存于浏览器 localStorage（键：`ai-atlas-favs`），不上传服务器。
