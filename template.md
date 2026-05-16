# OpenStack Africa — Template Schema
 
This document defines the standard for every template in the registry. Maintainers use this to validate submissions. Contributors use this to know exactly what to include.
 
---
 
## Folder structure
 
```
templates/
  {category}/
    {template-slug}/
      workflow.json
      README.md
      preview.png
```
 
### Category values
`payments` | `messaging` | `banking` | `business-ops`
 
### Template slug format
- Lowercase, kebab-case
- Format: `{api-name}-{action}-{destination}`
- Examples: `paystack-webhook-slack`, `termii-otp-verification`, `flutterwave-reconciliation-sheets`
---
 
## workflow.json
 
The raw n8n workflow export. Must meet these rules:
 
| Rule | Detail |
|------|--------|
| Valid JSON | Parseable without errors |
| No credentials | All keys replaced with placeholders |
| Placeholder format | `YOUR_{SERVICE}_{KEY_TYPE}` e.g. `YOUR_PAYSTACK_SECRET_KEY` |
| No personal data | No real names, emails, phone numbers, account numbers |
| n8n version | Compatible with n8n v1.0+ |
| Node count | Minimum 3 nodes, no upper limit |
 
**Placeholder examples:**
```
YOUR_PAYSTACK_SECRET_KEY
YOUR_TERMII_API_KEY
YOUR_SLACK_WEBHOOK_URL
YOUR_FLUTTERWAVE_SECRET_KEY
YOUR_KUDA_CLIENT_SECRET
```
 
---
 
## README.md
 
Required fields — all must be present:
 
| Field | Required | Description |
|-------|----------|-------------|
| Template name (H1) | Yes | Clear, specific name |
| What this does | Yes | 1–2 sentences, plain language |
| APIs used | Yes | Name + link to docs + role in workflow |
| Prerequisites | Yes | Everything needed before setup |
| Setup steps | Yes | Numbered, complete, testable |
| How it works | Yes | Node-by-node or phase-by-phase explanation |
| Example use case | Yes | Real scenario, specific |
| Author | Yes | Name/handle + location minimum |
 
Optional fields:
- Limitations / known issues
- Alternative configurations
- Related templates
---
 
## preview.png
 
| Rule | Value |
|------|-------|
| Format | PNG |
| Minimum width | 1200px |
| Content | n8n workflow canvas, all nodes visible |
| Background | Default n8n canvas background |
| No overlays | No annotations, arrows, or text added on top |
| No credentials | Ensure no API key is visible in any node |
 
---
 
## registry.json entry
 
When a template is merged, maintainers add an entry to `registry.json` at the root. Schema:
 
```json
{
  "id": "paystack-webhook-slack",
  "title": "Paystack webhook to Slack notification",
  "description": "Sends a real-time Slack message when a Paystack payment is completed, failed, or refunded.",
  "category": "payments",
  "apis": ["paystack", "slack"],
  "path": "templates/payments/paystack-webhook-slack",
  "author": {
    "name": "Chukwukaidibia Onyekwere",
    "twitter": "chuukkaa_OG",
    "location": "Lagos, Nigeria"
  },
  "tags": ["webhook", "notifications", "paystack"],
  "n8n_version_min": "1.0.0",
  "created_at": "2025-01-15",
  "downloads": 0
}
```
 
### Field definitions
 
| Field | Type | Required | Notes |
|-------|------|----------|-------|
| `id` | string | Yes | Matches folder slug |
| `title` | string | Yes | Max 60 characters |
| `description` | string | Yes | Max 160 characters |
| `category` | string | Yes | One of the four categories |
| `apis` | array | Yes | Lowercase API names |
| `path` | string | Yes | Relative path from repo root |
| `author.name` | string | Yes | — |
| `author.twitter` | string | No | Without @ symbol |
| `author.location` | string | Yes | City, Country |
| `tags` | array | Yes | 2–5 tags, lowercase |
| `n8n_version_min` | string | Yes | Semver format |
| `created_at` | string | Yes | ISO 8601 date |
| `downloads` | number | Yes | Starts at 0, auto-incremented |
 
---
 
## Validation
 
Maintainers run this checklist on every PR before merging:
 
- [ ] Folder structure matches schema exactly
- [ ] `workflow.json` is valid JSON and imports cleanly into n8n
- [ ] No credentials or personal data in any file
- [ ] All README required fields present
- [ ] Preview PNG meets size requirements
- [ ] `registry.json` entry added with all required fields
- [ ] Template is functional — maintainer has imported and tested it
Templates that fail validation are returned to the contributor with specific feedback.
 
