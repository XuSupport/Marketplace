# 个人 Trellis Spec Marketplace 设计

## 目标

为 XuSupport 建立一个可被 Trellis `--registry` 直接消费的 GitHub 模板仓库。新项目初始化时选择模板，随后在 Codex 中按 Trellis 工作流完成需求澄清、任务规划、实现、验证与规范沉淀。

## 选型

第一版以 Trellis 官方 Marketplace 的 `nextjs-fullstack` 为上游参考模板。它覆盖 Next.js、React、TypeScript、oRPC、Drizzle 与 PostgreSQL，是一份足够完整、同时容易裁剪的全栈基线。

不在第一版引入 Electron 或 Cloudflare Workers 模板；它们在需要对应技术栈时再从官方上游单独导入，避免让日常选择变得复杂。

## 仓库结构

- 根目录 `index.json`：Trellis Registry 清单，登记可选模板。
- `specs/nextjs-fullstack/`：官方参考模板的本地可维护副本。
- `README.md`：初始化命令、后续定制与同步上游的说明。
- `docs/superpowers/specs/`：本次设计记录。

## 使用流程

1. 新建 Git 仓库并安装 Trellis。
2. 执行 `trellis init -u <name> --codex --registry gh:XuSupport/Marketplace --template nextjs-fullstack`。
3. 在 Codex 说明产品、技术栈和本轮需求；要求先补齐或裁剪项目专属 Spec，再创建任务并按 Trellis 流程推进。
4. 经实践验证的通用规则以 PR 形式回写本仓库；只属于单一项目的规则保留在项目自身 `.trellis/spec/`。

## 安全与维护

- 模板中不包含密码、Token、真实环境地址或个人机器路径。
- 每次上游同步前先比较 diff；不会无差别覆盖本仓库的本地规则。
- 使用固定的 Registry URL，不依赖本机绝对路径。

## 验收标准

- `index.json` 能列出 `nextjs-fullstack` 模板。
- 从新目录运行 `trellis init ... --registry gh:XuSupport/Marketplace --template nextjs-fullstack` 可以下载该模板。
- README 提供可复制的初始化 Prompt 与维护方法。
