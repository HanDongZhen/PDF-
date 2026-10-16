# 简页PDF工具 / Jianye PDF Tools 隐私政策

最终正文更新与生效日期：2026-10-16。开发者 谢婷，联系邮箱 2683326280@qq.com。
纯静态 HTML / CSS / JavaScript，中英双语正文无需 JavaScript 即可阅读。适配手机、平板、桌面；跟随系统主题。无需 npm、数据库、后端或付费资源。

## GitHub 上传

1. 解压上传包，新建 GitHub 仓库（例如 `pdf-tools-privacy`）。
2. 上传解压后全部内容：仓库根目录应直接包含 `README.md`、`privacy-content.json`、`public/`，不要多套一层文件夹。
3. 上传的是文件和目录，不能只把 ZIP 放进仓库。网页实际部署目录是 `public/`。
4. 使用 `main` 分支；不要上传应用工程、证书、签名文件、密钥、测试文档或手机日志。

## Cloudflare Pages 连接 GitHub

Cloudflare 控制台 → Workers & Pages → 创建应用 → Pages → 导入 Git 仓库 → 连接并选择上面的 GitHub 仓库。

| 选项 | 填写内容 |
|---|---|
| 产品 | Pages（Git 集成） |
| 框架预设 | None / 无 |
| 生产分支 | main |
| 构建命令 | `exit 0` |
| 构建输出目录 | `public` |
| 根目录 | 留空 |
| 环境变量 | 不需要 |

部署成功后使用 Cloudflare 实际分配的 HTTPS 地址（`*.pages.dev`）：根路径 `/` 是中文政策，`/en/` 是英文政策。`/privacy`、`/privacy-policy` 会转向中文正文。应用市场隐私政策 URL 填实际中文 HTTPS 地址；英文资料可填 `/en/`。无需购买域名。免费套餐仍以 Cloudflare 当期规则和用量限制为准。

不要启用 Web Analytics、Zaraz 或额外追踪脚本；当前政策说明网页没有此类分析。若开启新数据收集，应先同步修改政策。

## 更新与检查

`privacy-content.json` 保存中英文正文。修改后，在本目录运行 `python build_policy.py`，同步生成两个 HTML 正文及应用内政策；部署仍使用预生成的 public 目录，不需要云端构建。更新日期须与实际版本一致。发布前核对 `/`、`/en/` 手机阅读与语言切换，确认邮箱链接正确、无登录要求、正文无需脚本即可显示，并确认应用内政策一致。

本包附 `public/_headers` 安全头、`public/_redirects` 别名及独立 `404.html`。Cloudflare Pages 自动应用这两个配置文件。不要把项目改为需要 Worker 运行代码的模板。现有线上地址为 https://pdf-mrhan.pages.dev/ ，英文为 /en/。本次改名与主体修正需将本包更新到原 GitHub 仓库并触发部署，线上页面未随本地改动自动更新。

本地预览可在 `public` 目录运行 `python -m http.server 8788 --bind 127.0.0.1`，打开 `http://127.0.0.1:8788/`。也可直接打开 HTML 阅读正文。

官方说明：[Cloudflare 静态 HTML 部署](https://developers.cloudflare.com/pages/framework-guides/deploy-anything/) · [Git 集成](https://developers.cloudflare.com/pages/get-started/git-integration/) · [响应头](https://developers.cloudflare.com/pages/configuration/headers/) · [重定向](https://developers.cloudflare.com/pages/configuration/redirects/)
