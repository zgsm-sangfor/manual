# Purchased Credits Validity One-Year Update Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Update all documentation references to purchased Credits validity from 30 days to one year, leaving giveaway Credits validity unchanged.

**Architecture:** This is a pure documentation content update across six Markdown files (three English source files and their Chinese translations under `i18n/zh/`). No code, components, or configuration change.

**Tech Stack:** Docusaurus 3, Markdown, npm scripts.

## Global Constraints

- Purchased Credits validity becomes **one year / 一年**.
- Giveaway Credits validity remains unchanged (30 days for registration/Star/invite giveaways, cleared at month-end for weekly Monday giveaways).
- English source files live in `docs/billing/`. Chinese translations live in `i18n/zh/docusaurus-plugin-content-docs/current/billing/`.
- `docs/` must contain English only; Chinese content belongs in `i18n/zh/` mirrors.
- After edits, `npm run typecheck` and `npm run build` must pass.
- Work on branch `feat/purchased-credits-validity-one-year`.

## File Structure

### Files to modify

| File | Language | What it contains |
|------|----------|------------------|
| `docs/billing/purchase.md` | English | Plan table and Section 3.1 validity period for purchased Credits. |
| `docs/billing/usage.md` | English | "Credits Expiration" and "Important Notes About Expiration Dates" sections. |
| `docs/billing/service.md` | English | Section 1.2 "Service Billing Cycle" definition. |
| `i18n/zh/docusaurus-plugin-content-docs/current/billing/purchase.md` | Chinese | 套餐表 and 3.1 有效期. |
| `i18n/zh/docusaurus-plugin-content-docs/current/billing/usage.md` | Chinese | "Credits 到期" and "关于到期日期的重要说明". |
| `i18n/zh/docusaurus-plugin-content-docs/current/billing/service.md` | Chinese | 1.2 服务计费周期. |

### Files unchanged

- Giveaway Credits tables and descriptions remain at 30 days / month-end clearance.
- `docusaurus.config.ts`, sidebars, and other site configuration are not touched.

---

### Task 1: Update English billing docs

**Files:**
- Modify: `docs/billing/purchase.md`
- Modify: `docs/billing/usage.md`
- Modify: `docs/billing/service.md`

**Interfaces:**
- Consumes: Approved design spec.
- Produces: Updated English documentation with purchased Credits validity set to one year.

- [ ] **Step 1: Update `docs/billing/purchase.md`**

  Replace the table validity values and Section 3.1 wording.

  ```markdown
  | Plan Name | Price | Credits Amount | Validity Period |
  |-----------|-------|----------------|-----------------|
  | Package 1 | ¥50 | 1000 Credits | one year |
  | Package 2 | ¥200 | 4,200 Credits | one year |
  | Package 3 | ¥500 | 10,800 Credits | one year |
  ```

  In Section 3.1:

  ```markdown
  - All purchased Credits are valid for **one year**
  - The validity period starts from the date when Credits are successfully recharged and credited
  - Credits that expire unused will automatically become invalid and will not be refunded
  ```

- [ ] **Step 2: Update `docs/billing/usage.md`**

  In the "Credits Expiration" bullet list:

  ```markdown
  - Purchased Credits are valid for one year after purchase
  - Giveaway Credits validity is determined by giveaway rules (30 days or cleared at month-end)
  - You can view specific expiration times in the Credits log
  ```

  In "Important Notes About Expiration Dates":

  ```markdown
  - **Purchased Credits**: The expiration date is a fixed date determined at the time of purchase (one year after purchase)
  ```

- [ ] **Step 3: Update `docs/billing/service.md`**

  In Section 1.2:

  ```markdown
  The Service billing cycle refers to the valid usage period of the Credits you purchase. It is calculated from the date of successful Credit purchase and is valid for one year.
  ```

- [ ] **Step 4: Commit English changes**

  ```bash
  git add docs/billing/purchase.md docs/billing/usage.md docs/billing/service.md
  git commit -m "docs: update purchased Credits validity to one year in English billing docs

  Co-Authored-By: Claude <noreply@anthropic.com>"
  ```

---

### Task 2: Update Chinese translations

**Files:**
- Modify: `i18n/zh/docusaurus-plugin-content-docs/current/billing/purchase.md`
- Modify: `i18n/zh/docusaurus-plugin-content-docs/current/billing/usage.md`
- Modify: `i18n/zh/docusaurus-plugin-content-docs/current/billing/service.md`

**Interfaces:**
- Consumes: Updated English source wording from Task 1.
- Produces: Updated Chinese translations consistent with English source.

- [ ] **Step 1: Update Chinese `purchase.md`**

  Table:

  ```markdown
  | 套餐名称 | 价格 | Credits数量 | 有效期 |
  |---------|------|-------------|--------|
  | 流量套餐1 | ¥50 | 1000 Credits | 一年 |
  | 流量套餐2 | ¥200 | 4,200 Credits | 一年 |
  | 流量套餐3 | ¥500 | 10,800 Credits | 一年 |
  ```

  Section 3.1:

  ```markdown
  - 所有购买的Credits有效期为**一年**
  - 有效期自Credits成功充值到账之日起开始计算
  - 到期未使用的Credits将自动失效，不予退还
  ```

- [ ] **Step 2: Update Chinese `usage.md`**

  In "Credits 到期":

  ```markdown
  - 购买的 Credits 有效期为购买后一年
  - 赠送的 Credits 有效期根据赠送规则确定（30天或月底清零）
  - 你可以在 Credits 日志中查看具体的到期时间
  ```

  In "关于到期日期的重要说明":

  ```markdown
  - **购买的 Credits**：到期日期为购买时确定的固定日期（购买后一年）
  ```

- [ ] **Step 3: Update Chinese `service.md`**

  Section 1.2:

  ```markdown
  服务计费周期是指您购买Credits的有效使用期限。从您成功购买Credits之日起计算，有效期为一年。
  ```

- [ ] **Step 4: Commit Chinese changes**

  ```bash
  git add i18n/zh/docusaurus-plugin-content-docs/current/billing/purchase.md \
          i18n/zh/docusaurus-plugin-content-docs/current/billing/usage.md \
          i18n/zh/docusaurus-plugin-content-docs/current/billing/service.md
  git commit -m "docs: update purchased Credits validity to one year in Chinese translations

  Co-Authored-By: Claude <noreply@anthropic.com>"
  ```

---

### Task 3: Verify build and typecheck

**Files:**
- Test command output only.

**Interfaces:**
- Consumes: Updated Markdown files from Tasks 1 and 2.
- Produces: Confirmed passing quality gates.

- [ ] **Step 1: Run typecheck**

  ```bash
  npm run typecheck
  ```

  Expected: exits with code 0, no errors.

- [ ] **Step 2: Run production build**

  ```bash
  npm run build
  ```

  Expected: builds successfully to `build/`. Warnings about broken links are acceptable because `onBrokenLinks: 'warn'`; no errors.

- [ ] **Step 3: Optional spot-check of rendered output**

  ```bash
  npm run serve
  ```

  Then visit:
  - `http://localhost:3000/plugin/billing/purchase`
  - `http://localhost:3000/plugin/billing/usage`
  - `http://localhost:3000/plugin/billing/service`

  Confirm purchased Credits show "one year" / "一年" and giveaway rules still show 30 days / month-end.

- [ ] **Step 4: Final status check**

  ```bash
  git status
  git log --oneline -5
  ```

  Expected: working tree clean, commits present on `feat/purchased-credits-validity-one-year`.

---

## Self-Review

### Spec coverage

- Purchased Credits in plan table → Task 1 Step 1 / Task 2 Step 1.
- Purchased Credits validity section → Task 1 Step 1 / Task 2 Step 1.
- Purchased Credits expiration in usage details → Task 1 Step 2 / Task 2 Step 2.
- Service billing cycle definition → Task 1 Step 3 / Task 2 Step 3.
- Giveaway Credits unchanged → explicitly noted in Task 1 Step 2 / Task 2 Step 2.
- Build verification → Task 3.

### Placeholder scan

- No "TBD", "TODO", or vague instructions.
- Every step includes exact replacement Markdown text.
- Exact file paths are specified.

### Consistency

- English uses "one year" throughout.
- Chinese uses "一年" throughout.
- Giveaway rules are not modified in any step.
