# zjui 每日论文推荐

- Zotero 范围：`zjui` 及全部子集合（VRP、OPF、OPF+VRP）。
- 时间：每天北京时间 08:00；GitHub Actions 可能排队延迟。
- 来源：arXiv，包含交叉分类。
- 分类：`cs.AI`、`cs.LG`、`cs.NE`、`cs.DS`、`math.OC`、`eess.SY`。
- 排序：在 Actions runner 上计算文本向量，按 Zotero 文献相关性推荐。
- 数量：最多 10 篇；没有新论文时不发邮件。
- 内容：中文一句话摘要、作者机构、论文及 PDF 入口。
- 摘要模型：`gpt-6-luna`，使用你指定的 OpenAI 兼容接口。
- 邮件：126 邮箱，SMTP SSL 465。

## 配置位置

`config/custom.yaml` 保存公开配置，Actions 的 `CUSTOM_CONFIG` 变量保存同样的内容。密码与 API key 使用仓库 Actions Secrets。

必需 Secrets：`ZOTERO_ID`、`ZOTERO_KEY`、`SENDER`、`RECEIVER`、`SENDER_PASSWORD`、`OPENAI_API_KEY`、`OPENAI_API_BASE`。

`LLM_MODEL` 是 Actions Variable，填写摘要接口支持的模型名；默认 `gpt-4o-mini`。`OPENAI_API_BASE` 使用 OpenAI 兼容接口的 API 根地址，通常以 `/v1` 结尾。

## 首次启用

1. 在 Zotero 设置的 Security/API 页面新建专用 key，授予个人文献库只读权限。配置 `ZOTERO_KEY`。
2. 配置摘要接口的 `OPENAI_API_KEY`、`OPENAI_API_BASE` 和模型名 `LLM_MODEL`。
3. 手动运行 `Test` 工作流，检查日志与收件箱。
4. 确认成功后启用 `Send emails daily` 工作流。

本次配置准备阶段暂时停用定时工作流，待凭据补齐、试发成功后启用。
