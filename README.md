# CoStrict 文档站点

本项目是基于 [Docusaurus](https://docusaurus.io/) 构建的 CoStrict 文档站点，提供 Plugin、CLI、CSC、私有化部署、Cloud 和 V3 相关文档，并支持中文和英文。

站点是静态文档应用，不提供后端 REST API。本文档中的“接口”指文档站点的访问入口和路由。

## 站点访问接口

### 文档入口

| 文档模块 | 源文件目录 | 路由前缀 | 默认入口 |
| --- | --- | --- | --- |
| Plugin | `docs/` | `/plugin` | `/plugin/guide/installation` |
| CLI | `docs-cli/` | `/cli` | `/cli/guide/introduction` |
| CSC | `docs-csc/` | `/csc` | `/csc/overview` |
| 私有化部署 | `docs-deployment/` | `/plugin/deployment` | `/plugin/deployment/foreword` |
| Cloud | `docs-cloud/` | `/cloud` | `/cloud` |
| V3 | `docs-v3/` | `/v3` | `/v3` |

中文是默认语言，访问默认路由时不需要添加语言前缀。生产构建后的英文页面在路由前添加 `/en`，例如：

```text
中文：/plugin/guide/installation
英文：/en/plugin/guide/installation
```

Cloud 和 V3 文档当前可以通过路由直接访问，但暂未作为顶部导航栏入口展示。

### 兼容入口

项目保留了部分旧路径的跳转规则：

- `/` 跳转到 `/plugin/guide/installation`；
- `/FAQ` 跳转到 `/plugin/FAQ`；
- Plugin 文档的旧路径（例如 `/guide/...`、`/billing/...`、`/product-features/...`）跳转到对应的 `/plugin/...` 路径。

## 环境要求

- Node.js `>= 18`
- pnpm `>= 9`（项目使用 `pnpm-lock.yaml`）
- Docker（仅在使用容器启动时需要）

检查本地环境：

```bash
node --version
pnpm --version
```

如果尚未安装 pnpm，可以执行：

```bash
npm install --global pnpm@9
```

## 本地启动

在项目根目录安装依赖：

```bash
pnpm install
```

### 中文开发模式

```bash
pnpm start
```

启动中文开发服务器，默认访问地址为 [http://localhost:3000](http://localhost:3000)。修改文档后页面会自动刷新。

### 英文开发模式

```bash
pnpm run start:en
```

启动英文开发服务器，默认访问地址同样为 [http://localhost:3000](http://localhost:3000)。中文和英文开发服务器不能同时使用同一个端口。

开发模式一次只服务一个语言，并且不会生成完整搜索索引。需要验证语言切换和搜索功能时，请使用生产模式。

## 生产构建和预览

先生成生产构建产物，再启动本地静态服务器：

```bash
pnpm run build
pnpm run serve
```

构建产物位于 `build/` 目录。生产预览可以验证多语言路由、搜索和静态资源是否正常。

## Docker 启动

项目使用多阶段 Dockerfile 构建静态站点，并通过 Nginx 提供服务。构建并启动容器：

```bash
docker build -t costrict-manual .
docker run --rm -p 8080:80 costrict-manual
```

启动后访问 [http://localhost:8080](http://localhost:8080)。容器内部监听 80 端口，Nginx 同时处理文档路由和旧路径跳转。

## 常用命令

| 命令 | 用途 |
| --- | --- |
| `pnpm start` | 启动中文开发服务器 |
| `pnpm run start:en` | 启动英文开发服务器 |
| `pnpm run build` | 构建生产版本到 `build/` |
| `pnpm run serve` | 预览生产构建结果 |
| `pnpm run typecheck` | 执行 TypeScript 类型检查 |
| `pnpm run clear` | 清理 Docusaurus 缓存和构建产物 |
| `pnpm run write-translations` | 生成或更新翻译文件 |
| `pnpm run write-heading-ids` | 生成文档标题锚点 |
| `pnpm run convert-images` | 将 PNG/SVG 转换为 WebP 并更新引用 |

提交修改前建议执行：

```bash
pnpm run typecheck
pnpm run build
```

## 项目结构

```text
.
├── docs/                  # Plugin 英文文档
├── docs-cli/              # CLI 英文文档
├── docs-csc/              # CSC 英文文档
├── docs-deployment/       # 私有化部署英文文档
├── docs-cloud/            # Cloud 英文文档
├── docs-v3/               # V3 英文文档
├── i18n/zh/               # 中文翻译及主题文本
├── src/                   # React 组件和全局样式
├── static/                # 全局静态资源
├── docusaurus.config.ts   # 站点、插件、路由和多语言配置
├── sidebars*.ts           # 各文档模块的侧边栏配置
├── Dockerfile             # Docker 构建配置
└── nginx.conf             # Nginx 路由和静态资源配置
```

新增或修改文档时，请同步维护对应的 `i18n/zh/` 中文文档，并在对应的 `sidebars*.ts` 中注册新的文档入口。

## 开发分支和提交

请基于最新的 `main` 创建开发分支，不要直接在 `main` 分支上修改：

```bash
git switch main
git pull --rebase origin main
git switch -c docs/your-branch
```

提交信息使用语义化前缀，例如：

```bash
git commit -m "docs: update readme"
```
