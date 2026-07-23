# Finance & Audit Platform — Requirements Intake

Branded requirements-gathering form for the Finance & Audit software selection
and support project (REF **ION-SIN-2026** · DOC-2026-07-002 V1.0).

Static, single-file, no backend. Responses are emailed to **ai@ionity.today**
via [FormSubmit](https://formsubmit.co) (AJAX submit with plain-POST fallback).

**V4.3 updates:**
- New **Audit Findings** step that asks respondents where to investigate, without giving away answers.
- Landing-page **QR code + share URL** so the form can be opened on phones/tablets and shared anywhere.
- Hardened global submission with AJAX retry and standard-POST fallback.

## Files

| File | Purpose |
| :--- | :--- |
| `index.html` | The form. Self-contained — fonts via Google Fonts, logo/favicon pulled live from the `ionity-assets` repo. |
| `embed-snippet.html` | Copy-paste iframe block for forums, Google Sites, SharePoint, WordPress, etc. |

## Publish (GitHub Pages) — one-time, ±3 minutes

```bash
# from inside this folder, using the GitHub CLI (gh auth login first)
gh repo create Ionity-Global/finance-audit-requirements --public \
  --source=. --push \
  --description "Ionity — Finance & Audit Platform requirements intake (ION-SIN-2026)"

# enable Pages on main branch root
gh api -X POST repos/Ionity-Global/finance-audit-requirements/pages \
  -f "source[branch]=main" -f "source[path]=/"
```

No `gh`? Web route: github.com → New repository (`Ionity-Global/finance-audit-requirements`,
Public) → upload these files → Settings → Pages → Source: `main` / root → Save.

**Public link once live:**
`https://ionity-global.github.io/finance-audit-requirements/`

## How global email delivery works

The form posts to **ai@ionity.today** through FormSubmit.co. It works from any
device or country once the page is reachable (GitHub Pages, an embed/iframe,
or a local copy opened on a tablet/phone):

1. Browser sends the form data via AJAX to `https://formsubmit.co/ajax/ai@ionity.today`.
2. If that fails (network, CORS, ad-blocker), it falls back to a standard
   `POST` to the same endpoint.
3. FormSubmit emails a formatted table to **ai@ionity.today**.

## ⚠️ Activate email delivery (one submission, one click)

FormSubmit requires a one-time activation per destination address:

1. Open the live page and submit one test entry.
2. FormSubmit sends an activation email to **ai@ionity.today** — click **Activate**.
3. All submissions from then on arrive as formatted table emails at ai@ionity.today.

## Embed

Paste the contents of `embed-snippet.html` into the target page. Adjust the
iframe `height` if the host page clips the form.

## Customising

- Recipient: change both `action="https://formsubmit.co/…"` and the AJAX URL in the script.
- Subject line: hidden `_subject` field.
- Section refs `F-01…F-06` follow the intake ledger; add sections by copying a `<section class="card">` block.

---
© 2018–2026 Antwerp Designs | Ionity (Pty) Ltd · All rights reserved
Author: Johan Wilhelm van Antwerp · ORCID 0009-0005-7181-0347 · Policy AED 986
*Building Tomorrow, Today.*
