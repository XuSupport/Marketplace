# XuSupport Trellis Marketplace

这是个人 Trellis Spec 模板库。目前提供两个可编辑基线：适合 Next.js 全栈应用的 nextjs-fullstack，以及适合 LangChain Deep Agents Python SDK 项目的 deepagents-python。

## 新项目使用

先在新项目目录初始化 Git，然后运行：

```bash
npm install -g @mindfoldhq/trellis@latest
trellis init -u <your-name> --codex --registry gh:XuSupport/Marketplace --template nextjs-fullstack
```

将 `<your-name>` 替换为你的稳定开发者标识，例如 `xusupport`。初始化完成后，在 Codex 中直接发送下面的 Prompt：

```text
我正在创建一个新项目。请先读取当前 Trellis 上下文和 `.trellis/spec/`，根据以下项目事实只补齐必要的项目专属 Spec；不要臆造未确认的技术决策。

项目目标：<填写>
目标用户：<填写>
技术栈：<填写>
本轮需求：<填写>

Spec 补齐后，请判断本轮工作是否应创建 Trellis task。若应创建，先与我澄清需求、生成 PRD；复杂任务再形成设计与实施计划，然后按 Trellis workflow 推进。
```

在 Codex 0.129+ 中，请确认 `~/.codex/config.toml` 的 `[features]` 已启用 `hooks = true`，再在 TUI 运行一次 `/hooks` 并批准 Trellis 的 hook；这样 `/start`、`/continue` 与 `/finish-work` 等入口才会出现在命令菜单。

### Deep Agents Python SDK

用于以 Python、uv、LangChain 和 LangGraph 构建 Deep Agents SDK 项目：

~~~bash
trellis init -u <your-name> --codex --registry gh:XuSupport/Marketplace --template deepagents-python
~~~

该模板覆盖 Agent 图组装、工具与中间件、子代理、虚拟文件系统权限、持久化状态、公开 API 兼容性，以及离线单元测试和 ruff/ty 质量检查。项目特有的模型、后端、部署和业务工具规则应在初始化后的 .trellis/spec/ 中补充。

## 如何定制

模板只是起点。项目唯一的架构决定、部署细节和业务规则，请保留在该项目的 .trellis/spec/ 中。只有已经在多个项目被验证、且确实可复用的规则，才应通过审阅提交到本仓库对应的 specs/<template-id>/ 目录。

例如，为项目加入 Redis、支付服务或特定的权限模型时，先在项目的 Spec 中说明；当这些约束成为你多数项目的长期选择时，再将通用部分提升到模板。

## 与官方模板同步

官方上游是 [mindfold-ai/marketplace](https://github.com/mindfold-ai/marketplace)。同步时，先在临时目录克隆官方仓库，再比较模板差异：

```bash
git clone https://github.com/mindfold-ai/marketplace.git /tmp/trellis-upstream
diff -ruN specs/nextjs-fullstack /tmp/trellis-upstream/specs/nextjs-fullstack
```

逐项挑选需要的改动并人工合并；不要直接覆盖本地模板，以免丢失已经验证过的个人规则。

## 添加更多模板

当你需要 Electron 或 Cloudflare Workers 项目时，可从官方 Marketplace 导入相应 Spec 目录，在根目录 `index.json` 新增一个 `type: "spec"` 条目，并为该模板补充一段使用说明。每个模板都应保持可独立初始化和维护。
