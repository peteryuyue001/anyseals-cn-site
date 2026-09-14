# Anyseals 中国授权经销商 · 产品展示网站

单文件静态网站（原生 HTML/CSS/JS，hash 路由多页面），可直接推送至 GitHub Pages 免费托管，无需服务器与备案。

## 站点结构

| 路由 | 页面 |
|---|---|
| `#/home` | 首页（Hero、授权资质、产品总览、服务能力、行业应用、质量控制、CTA） |
| `#/products` | 产品中心（5 大分类：静密封、旋转密封件、液压密封件、气动密封件、挡圈，参考《anyseals 总样本》） |
| `#/category/{id}` | 产品分类页（5 大类 × 30 个子类分组，如 `#/category/static`） |
| `#/product/{type}` | 产品详情（153 个官网产品独立分页，如 `#/product/OR-10`、`#/product/CR-10`） |
| `#/compounds` | 材料中心（NBR/FKM/EPDM/HNBR/CR/FFKM 物性表） |
| `#/applications` | 行业应用（液压气动、食品、油气、化工流体、通用工业） |
| `#/downloads` | 技术资料下载（11 份 Anyseals 官方 PDF，含产品总样本，点击直接下载） |
| `#/about` | 关于我们（公司介绍、授权资质展示位） |
| `#/news` | 新闻动态（占位示例） |
| `#/contact` | 联系我们 + 询盘表单 |

## 部署到 GitHub Pages

### 方式一：个人 / 组织站点（username.github.io）

1. 注册 GitHub 账号（已有则跳过），新建仓库，仓库名必须为 `<你的用户名>.github.io`（公开仓库）。
2. 将本目录中的 `index.html` 与 `README.md` 上传到仓库根目录。
   - 网页端：仓库页 → Add file → Upload files，拖入文件后 Commit。
   - 或命令行：`git init && git add . && git commit -m "init" && git branch -M main && git remote add origin https://github.com/<用户名>/<仓库名>.git && git push -u origin main`
3. 等待 1~2 分钟，访问 `https://<你的用户名>.github.io/` 即上线。

### 方式二：项目站点（任意仓库名）

1. 新建公开仓库（如 `anyseals-site`），把文件推上去。
2. 仓库页 → Settings → Pages → Source 选择 `Deploy from a branch`，Branch 选 `main`，目录 `/ (root)` → Save。
3. 访问 `https://<你的用户名>.github.io/<仓库名>/`。

> 说明：本项目为单文件 + hash 路由，任何子路径都能正确加载，无需配置 404 页。

## 上线前必改的占位内容

在 `index.html` 中搜索 `【` 逐一替换：

- 【公司名称】【联系电话】【公司邮箱】【微信号】【公司地址】【ICP 备案号】——页面顶部信息条、页脚、联系页均有多处。
- 新闻动态 3 篇文章为「示例内容」，替换为真实动态。

## 询盘表单配置（必做）

GitHub Pages 无后端，询盘表单推荐接第三方服务：

1. **推荐：飞书表单** —— 在飞书创建表单（收集姓名/公司/电话/邮箱/产品/需求），发布后复制表单链接。
2. 打开 `index.html`，在文件顶部 `<script>` 的 `SITE` 配置中，把 `FORM_URL` 改为表单链接：
   ```js
   var SITE = { FORM_URL: "https://xxxx.feishu.cn/share/base/form/xxxx", ... };
   ```
3. 未配置前，用户提交表单会提示直接电话 / 邮件联系，不会丢单。

备选：Formspree（https://formspree.io，免费额度）等，把 `FORM_URL` 换成对应表单链接即可。

## 可选：绑定自定义域名

1. 在域名服务商处添加 CNAME 记录：`<子域名>` → `<用户名>.github.io`。
2. 仓库 Settings → Pages → Custom domain 填入域名 → Save。
3. 域名需 ICP 备案才能绑定中国大陆服务器解析的域名；GitHub Pages 本身免备案，国内访问速度取决于网络环境，建议上线后用国内网络实测。

## 统计与后续

- 统计：可在 `</body>` 前按需接入百度统计（`hm.baidu.com` 脚本），需自行申请站点 ID。
- 图片：已整合 Anyseals 官网授权素材（hero、5 大分类卡、153 个产品 3D/2D 图、5 个行业卡、质量区、关于页均替换为官网图）。产品分类参考《anyseals 总样本》：静密封（36 个，14 子类）、旋转密封件（41 个，6 子类）、液压密封件（64 个，5 子类，含防尘圈与导向元件）、气动密封件（9 个，2 子类）、挡圈（3 个，3 子类）。每个产品独立分页，参数（材料/温度/速度/压力）来自官网 API（°F 已换算 °C），各产品页挂载官网对应技术资料 PDF。
- 技术资料：已挂载 11 份官方 PDF——置顶为「产品总样本（中文全系列目录，24 页）」+ 10 份细分资料（O 型圈/V 型圈/油封/X 型圈/导向/轴修复套），更多资料在 `anyseals-materials/pdfs/`（63 份）可随时追加。
- 产品参数以 Anyseals 官方资料为准；上线前请补充授权书、证书扫描件（首页授权资质条与关于页展示位）。

## 文件说明

- `index.html` —— 站点全部代码（含内联样式与脚本），单文件自包含。
- `README.md` —— 本说明。
