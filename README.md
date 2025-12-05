# rendergit-cloudflare-pages
自动将代码仓库通过 `rendergit` 渲染为静态HTML，并部署到 Cloudflare Pages 的自动化工作流。

## 功能
- 代码推送到 `main/master` 分支时自动触发
- 用 `rendergit` 渲染仓库代码为单页HTML
- 一键部署到 Cloudflare Pages，全球CDN加速

## 快速开始
### 1. 前置准备
- 拥有 Cloudflare 账户，创建 Pages 项目（项目名：`rendergit-auto`，需和脚本中一致）
- 生成 Cloudflare API Token（权限：Account → Cloudflare Pages → Edit）

### 2. 配置GitHub Secrets
在仓库 → Settings → Secrets and variables → Actions 中添加：
| 名称                  | 说明                     |
|-----------------------|--------------------------|
| CLOUDFLARE_API_TOKEN  | Cloudflare Pages 部署令牌 |

### 3. 部署
- 将代码推送到 `main/master` 分支，自动触发部署
- 或手动触发：GitHub → Actions → 选择工作流 → Run workflow

### 4. 访问地址
部署成功后访问：`https://rendergit-auto.pages.dev`

## 自定义配置
- 修改脚本中 `--project-name=rendergit-auto` 为你的 Cloudflare Pages 项目名
- 编辑 `.rendergitignore` 调整需要排除的文件夹
- 修改 `rendergit` 命令参数（如 `--max-bytes` 调整渲染字节限制）

## 依赖
- Python 3.11+
- rendergit（来自 karpathy/rendergit）
- Cloudflare Wrangler 4.52.1

## 注意事项
- API Token 仅需 Pages 编辑权限，遵循最小权限原则
- 国内访问优先选择 Cloudflare Pages（CDN节点更多）
- 若部署失败，检查 Token 权限/有效期，或查看 Actions 日志
