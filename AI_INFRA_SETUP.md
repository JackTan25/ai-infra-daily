# AI Infra Daily 配置

这个 Fork 已针对 AI Infrastructure 做了默认配置：

- 每天北京时间 01:30 自动运行（GitHub Actions 使用 UTC 17:30）。
- 默认抓取 `cs.DC, cs.AR, cs.PF, cs.OS, cs.NI`。
- 默认使用中文摘要和 `deepseek-chat`。
- 摘要提示词优先提炼训练、推理/Serving、分布式系统、编译器与 Kernel、加速器、网络、存储、调度、可观测性、可靠性与性价比。
- GitHub Actions 已获得向 `main` 和 `data` 分支写入每日结果所需的权限。

## 必需 Secrets

在仓库的 **Settings → Secrets and variables → Actions** 中配置：

- `OPENAI_API_KEY`: OpenAI-compatible API 密钥。
- `OPENAI_BASE_URL`: 对应服务的 API 地址，例如 DeepSeek 为 `https://api.deepseek.com`。

可选：

- `ACCESS_PASSWORD`: 给网页增加访问密码。
- `TOKEN_GITHUB`: 提高查询论文代码仓库信息时的 GitHub API 限额。

如需覆盖默认值，可在 Actions Variables 中设置 `CATEGORIES`、`LANGUAGE`、`MODEL_NAME`、`EMAIL` 和 `NAME`。
