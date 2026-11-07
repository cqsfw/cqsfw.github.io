# 传奇发布网 · 静态站点

一套可直接部署到 GitHub Pages 的纯静态网站，主题词为「传奇发布网」。全部文件平铺在根目录，不依赖任何后端、数据库、构建工具或外部 CDN，打开即用。

- 站点地址（部署后）：https://cqsfw.github.io
- 首页标题：传奇发布网_新开传奇开服表_传奇版本资讯与攻略大全
- 首页关键词：传奇发布网、传奇开服表、新开传奇、传奇版本、传奇攻略、1.76复古传奇、合击传奇、单职业传奇、冰雪传奇、传奇资讯、传奇评测
- 首页描述：传奇发布网每日整理传奇开服表与新区信息，按 1.76 复古、1.80 合击、单职业、冰雪、迷失等分类呈现；同时提供版本评测、职业打法、打宝路线与攻城攻略，帮助玩家进区之前把该知道的事弄清楚。

## 文件清单（全部位于根目录）

| 文件 | 说明 |
| --- | --- |
| `index.html` | 首页：今日开区速览、版本分类、最新资讯、玩法攻略、版本评测 |
| `kaifu.html` | 传奇开服表：今日 / 明日 / 后日三个时间维度 |
| `news.html` | 游戏资讯列表（含版本评测） |
| `guide.html` | 玩法攻略列表（职业、打宝、装备、攻城、经济） |
| `search.html` | 站内搜索，支持标题、摘要、标签与正文关键词匹配 |
| `about.html` | 关于本站、内容说明、免责声明 |
| `404.html` | 404 页面（GitHub Pages 会自动使用根目录的 404.html） |
| `n1.html` ~ `n24.html` | 24 篇文章详情页，各自独立、可单独打开 |
| `style.css` | 全站样式（移动端优先，768 / 1024 两档断点） |
| `sitemap.xml` | 站点地图，包含全部 30 个页面 |
| `robots.txt` | 爬虫规则，已指向 sitemap |
| `favicon.svg` | 站点图标（红底金框「传」字印章） |
| `.nojekyll` | 告诉 GitHub Pages 不要用 Jekyll 处理，避免静态文件被忽略 |

## 部署到 cqsfw.github.io

1. 在 GitHub 新建仓库，仓库名必须是 `cqsfw.github.io`（这样才能用一级域名 `https://cqsfw.github.io` 访问）。
2. 把本目录下**所有文件**上传到仓库根目录（不要多套一层文件夹）。
3. 进入仓库 `Settings → Pages`，Source 选择 `Deploy from a branch`，Branch 选 `main`、目录选 `/ (root)`，保存。
4. 等待 1～3 分钟，访问 `https://cqsfw.github.io` 即可。
5. 后续更新：直接替换或新增 HTML 文件，提交后自动发布。

> 若使用自定义域名，需在根目录增加 `CNAME` 文件，并在域名服务商处解析。本套文件默认按 `cqsfw.github.io` 生成 canonical 与 sitemap 链接。

## 页面之间怎么连

- 顶部导航：首页 / 开服表 / 游戏资讯 / 玩法攻略 / 关于本站，全站每页一致。
- 开服表每一行的「版本详情」都指向对应版本的评测文章，不存在空链接。
- 每篇文章底部有「上一篇 / 下一篇」「相关阅读」（同栏目优先）与标签。
- 首页、列表页、文章页都会指回对应栏目与首页，形成完整的内链闭环。

## 百度 SEO 已做的处理

- 每个页面独立的 `title` / `keywords` / `description`，核心词前置。
- 每页唯一 `h1`，正文用 `h2` / `h3` 分层，语义化标签（`header` / `main` / `article` / `time`）。
- 全站 `canonical` 绝对地址，`applicable-device=pc,mobile`，移动端自适应。
- 纯静态 HTML，无 JS 渲染正文，首屏内容直接写在 HTML 里；CSS 只有一个文件，无外部字体与第三方脚本。
- `robots.txt` + `sitemap.xml`，站点地图含全部页面与更新时间。
- 文章页内嵌 JSON-LD 结构化数据（Article），首页为 WebSite。
- 图片仅一个 SVG 图标，不依赖外部图床，加载快、无裂图风险。

### 提交百度收录（部署后操作）

1. 百度搜索资源平台添加站点 `https://cqsfw.github.io`，完成验证（可用 HTML 标签验证或文件验证）。
2. 「普通收录 → 资源提交」里提交 `https://cqsfw.github.io/sitemap.xml`。
3. 若要主动推送，可用接口（需替换为自己站点的 token）：

```bash
curl -H 'Content-Type:text/plain' --data-binary @urls.txt \
  "http://data.zz.baidu.com/urls?site=https://cqsfw.github.io&token=你的token"
```

`urls.txt` 每行一个完整 URL。GitHub Pages 不支持服务端脚本，因此推送需在本地或 CI 中执行。

## 内容维护

- 新增文章：复制任意 `n*.html`，改标题、描述、正文与内链，再把链接加进 `index.html` / 列表页 / `sitemap.xml`。
- 修改开服表：直接编辑 `kaifu.html` 中三张表格的 `<tr>`，每行五个单元格（开区时间、区服、版本、线路、版本详情链接）。
- 修改站点信息：`index.html` 的 title/description、页脚版权在各页 `.foot` 区块中。

## 说明

本站为资讯型静态站点，不运营游戏，不提供下载、充值、账号交易等服务。开区信息仅作整理参考，具体以对应游戏官方公告为准。
