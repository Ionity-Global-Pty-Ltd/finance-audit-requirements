# Finance & Audit Platform — Requirements Intake

Branded requirements-gathering form for the Finance & Audit software selection
and support project (REF **ION-SIN-2026** · DOC-2026-07-002 V1.0).

Static, single-file, no backend. Responses are emailed to
**[ai@ionity.today](mailto:ai@ionity.today)**
via [FormSubmit](https://formsubmit.co) (AJAX submit with plain-POST fallback).

**V4.8 updates:**

- **Submission reference ID** — every submission generates a unique `ION-XXXX-XXXX-XXXX` reference shown on the done screen with a one-click copy button. The reference is also included in the emailed data table for easy tracking.
- **Reply-To header** — if the respondent provides an email, it is forwarded to FormSubmit as `_replyto` so the audit team can reply directly from their inbox.
- **Submission timestamp** — ISO 8601 timestamp included in the emailed table.
- **Auto-save toast** — a brief "Progress saved" notification appears (max once per 5 s) when the form saves progress to localStorage, giving clear feedback on multi-device use.
- **Character counters** — live character counts on the five key open-text fields (`Biggest challenge`, `What is not working`, `Specific concerns`, `Problem-solving reasoning`, `Recommendations`).
- **Improved AJAX retry** — AJAX now retries up to 3 times with exponential back-off before falling back to a standard POST.

**V4.7 updates:**

- Custom monochrome **Ionity icon set** — hand-drawn cyan line icons (navy/cyan brand palette only, matching [www.ionity.co.za](https://www.ionity.co.za)) replacing all multicolour emojis.
- Brand-pure accents everywhere: backdrop signals, progress bar, confetti, live dots and completion tick now use only cyan/navy/white.

**V4.6 updates:**

- Fun, celebratory finish — confetti burst on completion, progress cheers and emoji department cards.
- Cross-platform ergonomics: notch/safe-area support, larger touch targets, focus-visible outlines and no-zoom inputs.
- Welcome-page quick link chip to [www.ionity.co.za](https://www.ionity.co.za), placed below the QR share card.

**V4.5 updates:**

- New **Audit Findings** step that asks respondents where to investigate, without giving away answers.
- Real, scannable landing-page **QR code + share URL** for `https://ionity.art` (www redirects to the apex domain).
- Neutral cross-department system questions covering current tools, preferences and Sage X3 familiarity without assuming Sage 200 usage.
- One-page **AI and problem-solving capacity check** with two short scenarios and private scoring in the submitted response.
- Compact **Future Readiness** step covering continuity, ownership, restore awareness, access changes, data-use approval, change governance, outcome priorities and adoption support without naming a preferred vendor or pathway.
- Public-form safety reminder that prevents respondents from entering credentials, client identifiers, health information, bank details or transaction-level data.
- Modern **living data-grid backdrop** with moving network signals, one-pass heading glints, card traces and subtle control reveals, with a static reduced-motion mode.
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
`https://ionity.art` — `www.ionity.art` forwards here (apex holds the TLS certificate).

## How global email delivery works

The form posts to **[ai@ionity.today](mailto:ai@ionity.today)** through
[FormSubmit](https://formsubmit.co). It works from any
device or country once the page is reachable (GitHub Pages, an embed/iframe,
or a local copy opened on a tablet/phone):

1. Browser sends the form data via AJAX to `https://formsubmit.co/ajax/ai@ionity.today`.
2. If that fails (network, CORS, ad-blocker), it falls back to a standard
   `POST` to the same endpoint.
3. FormSubmit emails a formatted table to **[ai@ionity.today](mailto:ai@ionity.today)**.

## ⚠️ Activate email delivery (one submission, one click)

FormSubmit requires a one-time activation per destination address:

1. Open the live page and submit one test entry.
2. FormSubmit sends an activation email to **[ai@ionity.today](mailto:ai@ionity.today)** — click **Activate**.
3. All submissions from then on arrive as formatted table emails at [ai@ionity.today](mailto:ai@ionity.today).

## Embed

Paste the contents of `embed-snippet.html` into the target page. Adjust the
iframe `height` if the host page clips the form.

## Customising

- Recipient: change both `action="https://formsubmit.co/…"` and the AJAX URL in the script.
- Subject line: hidden `_subject` field.
- Section refs `F-01…F-06` follow the intake ledger; add sections by copying a `<section class="card">` block.

---
© 2018–2026 Antwerp Designs | Ionity Global (Pty) Ltd · All rights reserved
Author: Johan Wilhelm van Antwerp · ORCID 0009-0005-7181-0347 · Policy AED 986
*Building Tomorrow, Today.*
