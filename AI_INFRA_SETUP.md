# AI Infra Daily 配置

这个 Fork 已针对 AI Infrastructure 做了默认配置：

- 每天北京时间 01:30 自动运行（GitHub Actions 使用 UTC 17:30）。
- 默认抓取 `cs.DC, cs.AR, cs.PF, cs.OS, cs.NI`。
- 默认使用中文摘要和 GitHub Models 中的 `openai/gpt-4.1-mini`，无需另配 API 密钥。
- 摘要提示词优先提炼训练、推理/Serving、分布式系统、编译器与 Kernel、加速器、网络、存储、调度、可观测性、可靠性与性价比。
- GitHub Actions 已获得向 `main` 和 `data` 分支写入每日结果所需的权限。

## 可选的自定义模型

默认配置直接使用工作流自带的短期 `GITHUB_TOKEN` 调用 GitHub Models。若要改用 DeepSeek 或其他 OpenAI-compatible 服务，可在仓库的 **Settings → Secrets and variables → Actions** 中配置：

- `OPENAI_API_KEY`: 服务的 API 密钥。
- `OPENAI_BASE_URL`: 服务的 API 地址，例如 DeepSeek 为 `https://api.deepseek.com`。
- Actions Variable `MODEL_NAME`: 例如 `deepseek-chat`。

可选：

- `ACCESS_PASSWORD`: 给网页增加访问密码。
- `TOKEN_GITHUB`: 自定义查询论文代码仓库信息所用的 GitHub Token；不配置时使用工作流自带 Token。

如需覆盖默认值，可在 Actions Variables 中设置 `CATEGORIES`、`LANGUAGE`、`MODEL_NAME`、`EMAIL` 和 `NAME`。
