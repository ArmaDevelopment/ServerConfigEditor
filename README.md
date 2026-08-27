# Arma Reforger Server Config Editor

A single-page, no-build-tools JSON editor for Arma Reforger dedicated server
config files. Everything lives in `index.html` — no server, no dependencies,
no install step.

## Features

- Structured editor for every section of the config (game settings, mods,
  admins, RCON, A2S, and everything else), plus a raw JSON view for direct
  editing.
- Mod search and dependency resolution against the [ModiScover](https://modiscover.eu)
  API — search by name, view mod details, and add a mod together with its
  full transitive dependency tree in one click.
- Compact, scrollable mod list built for large lists (200+ mods), with
  drag-and-drop reordering, bulk select/remove, and a dependency review that
  flags anything installed mods depend on but that isn't in your list yet.
- Export/import just the mod list as its own JSON file, separate from the
  full config.
- Auto-saves your work to the browser's local storage as you go, so a
  refresh or closed tab doesn't lose anything.
- Named "Saved Configs" slots — save multiple named snapshots in the
  browser, load any of them back, and a small status bar tracks whether your
  current edits have drifted from whichever saved slot you're working from,
  with a one-click Save back to that slot.

## Running it

Nothing to install. Open `index.html` directly in a browser, or host it
anywhere that serves static files (see below).

## Hosting on GitHub Pages

1. Create a new repository on GitHub (any name — e.g. `arma-config-editor`).
2. Upload `index.html` from this project to the repo (drag-and-drop on the
   GitHub web UI works fine, or `git push` if you're using Git locally).
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment", set the source to **Deploy from a branch**,
   pick the branch (usually `main`) and the `/ (root)` folder, then save.
5. GitHub will publish it at `https://<your-username>.github.io/<repo-name>/`
   within a minute or two.

Because it's a single static HTML file with no server-side component, any
other static host (Netlify, Cloudflare Pages, Vercel, Surge, Firebase
Hosting, etc.) works the same way — just upload `index.html`.

## Notes

- All data (your config edits, saved slots, admin cache) is stored in your
  browser's local storage, scoped to whatever domain you host this on.
  Local storage doesn't sync across different domains — if you host copies
  at multiple URLs, each keeps its own separate data.
- The ModiScover mod search/lookup features require the page to be able to
  reach `modiscover.eu` over the network from wherever it's hosted or
  opened.
