# Tanka · Onboarding Demo

Interactive web onboarding mockup for [Tanka](https://tanka.ai), with two parallel builds illustrating different user perspectives.

| | Live URL | What it shows |
|---|---|---|
| **Main flow** | `<pages-url>/main/` | New user signing up without any invitations |
| **Invited user** | `<pages-url>/invited/` | User arriving via an invite link (3 mock invitations pre-populated) |

Landing page at `<pages-url>/` lets you pick between them.

> Both builds share the same code — only the initial state differs (3 lines of difference).

## Highlights

- **Email + 6-digit code** passwordless flow (with paste / auto-advance / shake-on-error)
- **QR sign-in** with brand-color viewfinder + scanning-line animation + center logo
- **Sign-in ↔ Sign-up toggle** with text-only differentiation (no flashy gradient/halo, just clear copy)
- **Create profile** with initial-based color avatar (no stock photo fallback)
- **Create team** with team-name initial avatar + image upload
- **Join team** with `Invite code | Community` tabs (grid-stacked, no layout shift on switch)
- **Apply to join** for restricted teams (textarea + char counter + info banner)
- **Invitation cards** (invited build only) with compact single-row design + inviter avatar
- **Get mobile app** popover with side-by-side iOS / Android QR codes
- **User menu** dropdown with Sign out (resets state to fresh)
- **Demo helpers**:
  - 📄 floating button (bottom-right) → design review notes for every decision
  - ⇥⇥ floating button → Jump menu to skip directly to any step with pre-filled state

## Deploy to GitHub Pages

After pushing to GitHub:

1. **Settings → Pages**
2. **Source**: Deploy from a branch
3. **Branch**: `main` / **Folder**: `/ (root)`
4. **Save** — live in ~30 seconds at `https://<user>.github.io/tanka-onboarding-demo/`

No build step. No dependencies. Pure static HTML.

## Local preview

```bash
# Open landing page (with both flows linked)
open index.html

# Or serve over HTTP (better for testing fetches / subpaths)
python3 -m http.server 8080
```

## Structure

```
tanka-onboarding-demo/
├── index.html      ← Landing page (chooser between the two flows)
├── main/
│   └── index.html  ← Main flow build (default: no invitations)
└── invited/
    └── index.html  ← Invited user build (3 mock invitations pre-populated)
```

Each `<flow>/index.html` is fully self-contained — CSS and JS inlined, no external requests.

## Diff between the two builds

```js
// main/index.html — Default: NO invitations
// invited/index.html — populateInvitations() pre-fills 3 mock invites
//   + same call inside resetAllState so Sign out → fresh invites
```

That's the entire difference. Same UI, same components, same JS — just different default state.
