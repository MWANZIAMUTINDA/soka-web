# soka-web changelog

## 2026-10-30 — Console-football theme for all pages

Visual redesign only. Legal and informational wording is unchanged (checked sentence by sentence
against the previous pages: privacy 33/33, terms 22/22, account deletion 18/18, 404 4/4).

### Added
- `theme.css`: one shared stylesheet with the design tokens (deep navy background with glows and a
  grid, glass cards with a 4 px neon accent strip, neon yellow / cyan / pink accents, red for
  destructive actions), Teko headings and Inter body text (Google Fonts, with system-font fallbacks),
  skewed badges and buttons, hover lift and glow, focus styles, a solid fallback where
  `backdrop-filter` is unsupported, `prefers-reduced-motion` support, and small-screen rules.
- Skip link, `header` / `main` / `footer` / `nav` landmarks and `aria-current` on every page.
- `docs/screenshots/before/` and `docs/screenshots/after/`: every page at 1280 and 390 px wide
  (plus the invite variant of the 404 page).

### Changed, per page
- **index.html**: SOKA wordmark and "FC League Manager" pill in the header; "Run your FC league"
  hero; four feature cards (Match Days, Live Tables, Rivalries & XP, Fair Fixtures); links as glass
  pill buttons; Electronic Arts disclaimer kept.
- **privacy.html**: "SOKA App" badge, cyan "Last updated" date, sections grouped into cards in the
  order Who we are → What we collect → Why we use it → Who can see it → How long we keep it + Your
  choices and rights → Children + Security → Changes; pink ◆ list markers; "18+ Only" tag on the
  stakes item.
- **terms.html**: same layout, angled yellow ribbon, cyan list markers.
- **account-deletion.html**: "SOKA Account Center" badge; numbered steps with a "Fastest" tag for
  the in-app option; red gradient email button (same prefilled `mailto:`); "What is deleted" (red)
  and "What is kept, and why" (gold) side by side, stacked under 600 px.
- **404.html**: angled-corner card, "Out of Bounds" badge, gradient "404", "Return to SOKA Home"
  button. Invite links (`/soka-web/join/CODE`) still turn it into a "Join with code" page that opens
  the app.

### Decisions
- Kept `account-deletion.html` (not renamed to `delete-account.html`): the app and the Play Store
  listing link to `/account-deletion`.
- Kept every legal heading word for word (for example "Liability", not "Liability Waivers"), because
  renaming would change the legal text. Decorative labels ("SOKA App", "18+ Only", "Fastest") are
  `aria-hidden`, so screen readers read exactly the original text.
- 404.html uses site-root links (`/soka-web/...`): GitHub Pages serves it at any depth, where
  relative links break.
- No "eFootball" wording (a third-party trademark); the theme borrows the style only.

### Bugs fixed or checked
- The brief's `file:///D:/GIT/soka-web/...` links, `url?id=1` link and `translateY(-2deg)` hover
  were not in this repo (links were already relative; there were no hover styles). The new CSS uses
  `px` throughout.
- Background glow no longer stops partway down long pages (no `background-attachment: fixed`).
- All 21 internal links checked on every page, including from the invite page: none broken.

### Not verified
- Only Chromium was tested (headless, at 390 and 1280 px). Firefox, Safari and older Android
  WebViews were not tested; the `backdrop-filter` fallback is coded but not seen in a browser
  without support.
- Google Fonts loads from Google's servers, which see visitors' IP addresses. Self-host the two
  fonts if you want to avoid that third-party request.
