# Phase 12 — Email Templates

## Trigger
Admin (Phase 11) is complete.

## Files to Read
- `docs/framework/internal/14_email_system.md` — email system rules

## What to Build

### Auth Emails
- Email verification
- Password reset
- Team invite
- Magic link (if applicable)

### Billing Emails
- Payment receipt
- Subscription confirmation
- Plan change confirmation
- Payment failed / past due warning

### Onboarding Emails
- Welcome email (post-signup)
- Activation nudge (if user hasn't completed first value event)
- Onboarding completion confirmation

### Product Emails
- Notification digest (if applicable)
- Activity alerts (if applicable)

### Email Standards (from `14_email_system.md`)
- Single-column layout, 600px max width
- One primary CTA per email
- Plain text fallback for every email
- Dark mode compatible
- Mobile responsive
- Unsubscribe link on marketing/product emails
- No unsubscribe on transactional (auth, billing)

### Verify
- All email types render correctly in major clients
- CTAs link to correct routes
- Plain text fallbacks are readable
- Dark mode doesn't break layout or readability

## Exit Condition
Email templates are complete. Summarize and ask user to continue to **Phase 13**.
