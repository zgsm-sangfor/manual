# Design: Update Purchased Credits Validity from 30 Days to One Year

## Context

The CoStrict documentation currently states that purchased Credits expire 30 days after purchase. The product team has decided to extend the validity period to **one year** for purchased Credits only. Giveaway Credits validity remains unchanged.

## Goal

Update all documentation references to purchased Credits validity from 30 days / 30 calendar days to one year, while leaving giveaway Credits validity untouched.

## Decisions

- **Scope**: Update all Billing-related docs that mention purchased Credits validity.
- **Wording**: Use "one year" / "一年" rather than "365 days" / "365天".
- **Giveaway Credits**: Keep existing rules (30 days for registration/Star/invite giveaways, cleared at month-end for weekly Monday giveaways).

## Affected Files

### English source

1. `docs/billing/purchase.md`
   - Plan table "Validity Period" column: `30 days` → `one year`
   - Section 3.1 "Validity Period": `30 calendar days` → `one year`
2. `docs/billing/usage.md`
   - "Credits Expiration" bullet: `30 days after purchase` → `one year after purchase`
   - "Important Notes About Expiration Dates" bullet: `30 days after purchase` → `one year after purchase`
3. `docs/billing/service.md`
   - Section 1.2 "Service Billing Cycle": `30 calendar days` → `one year`

### Chinese translation

1. `i18n/zh/docusaurus-plugin-content-docs/current/billing/purchase.md`
   - 套餐表“有效期”：`30天` → `一年`
   - 3.1 有效期：`30个自然日` → `一年`
2. `i18n/zh/docusaurus-plugin-content-docs/current/billing/usage.md`
   - “Credits 到期”购买的 Credits：`购买后 30 天` → `购买后一年`
   - “关于到期日期的重要说明”购买的 Credits：`购买后30天` → `购买后一年`
3. `i18n/zh/docusaurus-plugin-content-docs/current/billing/service.md`
   - 1.2 服务计费周期：`30个自然日` → `一年`

## Out of Scope

- Giveaway Credits validity rules remain unchanged.
- Document last-updated dates are not changed unless explicitly requested.
- No changes to product code, pricing, or packaging.

## Verification

After editing:

1. Run `npm run typecheck` to ensure TypeScript/Docusaurus config is valid.
2. Run `npm run build` to ensure the site builds without broken links.
3. Review the rendered pages to confirm wording is correct and giveaway rules are untouched.
