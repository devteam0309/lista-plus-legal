# Lista+ — legal pages

Public policy pages for the **Lista+** Android app (`com.jorres.listaplus`), served via
GitHub Pages.

| File | Purpose |
|---|---|
| `index.html` | Landing page linking to both policies |
| `privacy.html` | Privacy policy — required by Google Play |
| `delete-account.html` | Account & data deletion — required by Google Play |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is, without Jekyll processing |

**This repository must be public.** GitHub Pages only serves from a public repository on
a free account, and Play needs these URLs reachable by anyone without signing in. Nothing
here is sensitive: plain HTML, no keys, no source code.

The app source lives in a separate private repository. Keep it that way — that is the
whole reason these pages were split out.

## Publishing

1. Create a **public** repo named `lista-plus-legal` on GitHub.
2. From this folder:

   ```bash
   git init
   git add .
   git commit -m "Add Lista+ privacy and account deletion pages"
   git branch -M main
   git remote add origin https://github.com/devteam0309/lista-plus-legal.git
   git push -u origin main
   ```

3. In the repo: **Settings → Pages → Source = Deploy from a branch**, branch `main`,
   folder `/ (root)`. Save.
4. Wait a minute or two for the first build, then confirm all three URLs load.

## The URLs

```
https://devteam0309.github.io/lista-plus-legal/
https://devteam0309.github.io/lista-plus-legal/privacy.html
https://devteam0309.github.io/lista-plus-legal/delete-account.html
```

Where each one goes in Play Console:

- **Privacy policy** → App content → Privacy policy, and Store listing.
- **Account deletion** → App content → Data safety → *Data deletion* → the URL where users
  can request deletion. Declare that an in-app path also exists (More → Account → Delete
  cloud account), because Play asks whether deletion is available in-app as well.

## Do not host these on Render

The API is on Render's free tier, which sleeps when idle and has been suspended before
when free instance hours ran out. A policy URL that returns 503 during a Play review is a
rejection. GitHub Pages is static and always up.

## Keeping them accurate

These pages make specific factual claims — no analytics, only two permissions, PBKDF2
password hashing, data hosted in Singapore, and exactly which entities are backed up.
**If the app's behaviour changes, update the pages in the same session**, and bump the
"last updated" date at the top of each. An inaccurate privacy policy is a policy
violation in its own right, not just stale documentation.

The originals also live at `docs/` in the app repository. If you edit one copy, copy it
across so the two do not drift.
