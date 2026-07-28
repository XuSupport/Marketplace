# Personal Trellis Marketplace Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Publish a personal Trellis Registry containing an editable copy of the official `nextjs-fullstack` Spec template.

**Architecture:** The GitHub repository is a standard Trellis Marketplace: root `index.json` exposes `specs/nextjs-fullstack`. The files are a vendored official baseline; README documents consumption and safe maintenance.

**Tech Stack:** Git, JSON, Markdown, Trellis CLI Registry format.

## Global Constraints

- The public Registry address is `gh:XuSupport/Marketplace`.
- The first template ID is exactly `nextjs-fullstack`.
- No secrets, tokens, machine-local absolute paths, or production settings may enter the repository.
- The upstream baseline is `https://github.com/mindfold-ai/marketplace` fetched on 2026-07-28.

---

### Task 1: Import the official Spec baseline and publish the manifest

**Files:**

- Create: `index.json`
- Create: `specs/nextjs-fullstack/**`

**Interfaces:**

- Consumes: Trellis Registry source `gh:XuSupport/Marketplace`.
- Produces: `index.json.templates[0]` with ID `nextjs-fullstack`, type `spec`, and path `specs/nextjs-fullstack`.

- [ ] Verify the upstream tree contains `index.json` and `specs/nextjs-fullstack/README.md`.
- [ ] Copy only `specs/nextjs-fullstack` into this repository as `specs/nextjs-fullstack`.
- [ ] Create this exact manifest:

```json
{
  "version": 1,
  "templates": [
    {
      "id": "nextjs-fullstack",
      "type": "spec",
      "name": "Next.js + oRPC + PostgreSQL (XuSupport baseline)",
      "description": "Editable personal baseline derived from the official Trellis Next.js full-stack Spec template.",
      "path": "specs/nextjs-fullstack",
      "tags": ["nextjs", "react", "typescript", "orpc", "drizzle", "postgresql", "xusupport"]
    }
  ]
}
```

- [ ] Validate it with:

```bash
node -e 'const fs=require("fs"); const x=JSON.parse(fs.readFileSync("index.json", "utf8")); if (x.version !== 1 || x.templates.length !== 1 || x.templates[0].id !== "nextjs-fullstack" || !fs.existsSync(x.templates[0].path)) process.exit(1); console.log("Registry valid")'
```

Expected: `Registry valid`.

- [ ] Commit with `git commit -m "feat: add Next.js full-stack Trellis template"`.

### Task 2: Document consumption, prompting, and maintenance

**Files:**

- Create: `README.md`

**Interfaces:**

- Consumes: Registry ID `nextjs-fullstack`.
- Produces: a copyable Trellis initialization command and Codex prompt.

- [ ] Document this initialization command:

```bash
npm install -g @mindfoldhq/trellis@latest
trellis init -u <your-name> --codex --registry gh:XuSupport/Marketplace --template nextjs-fullstack
```

- [ ] Include a Chinese starter prompt requiring the AI to read `.trellis/spec/`, add only confirmed project-specific rules, then determine whether to create a Trellis task and follow its workflow.
- [ ] Explain that project-only rules remain in that project's `.trellis/spec/`; repeated and verified rules are promoted here through review.
- [ ] Explain upstream sync: compare the official template diff and manually apply selected changes; never blindly overwrite personal rules.
- [ ] Verify with `rg -n 'gh:XuSupport/Marketplace|nextjs-fullstack|\\.trellis/spec' README.md`.
- [ ] Commit with `git commit -m "docs: explain Trellis marketplace usage"`.

### Task 3: Push and verify the public Registry source

**Files:**

- Modify: Git remote `origin` (already `https://github.com/XuSupport/Marketplace.git`)

**Interfaces:**

- Consumes: commits from Tasks 1 and 2.
- Produces: branch `main` on `XuSupport/Marketplace`.

- [ ] Confirm `git status --short` is empty and `git log --oneline --max-count=3` shows the Marketplace commits.
- [ ] Run `git push -u origin main`.
- [ ] Run `git ls-remote --heads origin main`; expect a non-empty SHA and `refs/heads/main`.

