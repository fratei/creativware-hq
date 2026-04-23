# Customer Feedback Log

This directory tracks customer feedback, both positive and negative, to inform product decisions.

## How to Log Feedback

Agents (CS, Sales, Marketing) should create entries here or label GitHub issues with `customer-feedback` in the relevant product repo.

### Feedback Entry Format

```markdown
## [DATE] — [Source: Support / Sales / Review / Social]

**Customer:** (anonymous ID or segment)
**Product:** AudioText
**Sentiment:** Positive / Negative / Neutral
**Category:** Bug | Feature Request | UX | Performance | Pricing
**Summary:** One-line summary
**Detail:** Full feedback
**Action:** Linked to issue # or backlog item
```

## Feedback Labels

Use these labels on product repo issues for automatic standup pickup:
- `customer-feedback` — general feedback
- `customer-feedback:positive` — praise, success stories
- `customer-feedback:negative` — complaints, churn signals
- `customer-feedback:feature-request` — feature requests from customers
