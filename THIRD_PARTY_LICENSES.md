# Third-Party Licenses & Attributions

This file is the formal license register for Project Omnilyth. It supplements:

- [`LICENSE`](LICENSE) — the GPL-3.0-or-later license that covers Omnilyth's original source code.
- [`workers/LICENSE`](workers/LICENSE) — the MIT license that covers the Cloudflare Worker proxy, carved out so other Path of Exile community tools may freely fork the proxy logic.
- [`NOTICE`](NOTICE) — short Apache-2.0-style attribution notice.

The information here is also surfaced in the in-app `/privacy` page; this file is the canonical, complete reference.

---

## 1. Direct npm dependencies

| Package | Version (range) | License | Notes |
|---|---|---|---|
| react | ^19.2.4 | MIT | Core framework |
| react-dom | ^19.2.4 | MIT | DOM renderer |
| react-router-dom | ^7.13.0 | MIT | Routing |
| vite | ^7.3.1 | MIT | Build tool |
| @vitejs/plugin-react | ^5.1.4 | MIT | Vite React integration |
| tailwindcss | ^4.1.18 | MIT | CSS framework |
| @tailwindcss/vite | ^4.1.18 | MIT | Tailwind Vite plugin |
| fuse.js | ^7.1.0 | Apache-2.0 | Fuzzy search — full attribution below |
| pako | ^2.1.0 | (MIT AND Zlib) | zlib compression |
| gh-pages | ^6.3.0 | MIT | Deploy tooling (devDep) |
| jsdom | ^27.0.1 | MIT | Dev-only DOM mock (devDep) |

All transitive dependencies surveyed at the time of this register were under MIT, Apache-2.0, BSD, ISC, or Zlib licenses. No GPL/AGPL/SSPL/CC-BY-SA in the npm dep graph. To verify the current state, run `npm ls --all --json` and audit any unfamiliar transitive against its upstream repo.

### Apache-2.0 deps — extended attribution

**Fuse.js** (`fuse.js@^7.1.0`) — Apache License 2.0. Copyright (c) Kiro Risk. Used in Omnilyth's gem browser fuzzy-search and in any other tool that pattern-matches user-typed strings against a known list. The Apache-2.0 NOTICE requirement is satisfied via [`NOTICE`](NOTICE) at the repo root.

Apache-2.0 license text: <https://www.apache.org/licenses/LICENSE-2.0.txt>.

### Zlib portion (pako)

`pako@^2.1.0` ships under the dual `MIT AND Zlib` license. Both are permissive and require attribution preservation only.

---

## 2. Bundled GPL-3.0 derivative work

### vilsol/timeless-jewels — Timeless Jewel Calculator

- **Upstream:** <https://github.com/Vilsol/timeless-jewels>
- **Upstream license:** GNU General Public License v3.0
- **Omnilyth files derived from upstream:**
  - `src/calculators/timelessJewel.js` — TinyMT32 PRNG + seed-search algorithm, ported from Go to JavaScript.
  - `src/workers/timelessSearch.js` — Web Worker entry point that drives the seed search.
  - `src/components/TimelessJewelCalculator.jsx` — UI wrapper that renders search controls + results.
  - `src/components/TimelessTreeView.jsx` — Passive-tree visualisation used by the calculator.
  - `src/pages/TimelessJewelPage.jsx` — Route container that mounts the calculator.
- **Currently disabled** in `src/modules/registry.js` (the registry entry is commented out and Vite's tree-shaker drops the chunks from `dist/`). When re-enabled, the bundle becomes a derivative work of vilsol/timeless-jewels — this is **the load-bearing reason the entire project is licensed GPL-3.0-or-later** rather than something more permissive.
- **License text:** see [`LICENSE`](LICENSE) at repo root (the project license is GPL-3.0-or-later, so the same file satisfies the requirement to ship the upstream license alongside the derivative work).

### `src/data/timeless/*.json` — upstream license verification pending

The three JSON files under `src/data/timeless/` (`alternatePassiveSkills.json`, `alternatePassiveAdditions.json`, `translations.json`) are produced by `Nifth/TimelessCalcPreprocess` (<https://nifth.github.io/TimelessCalc/>). Upstream license is currently unverified. Before re-enabling the calculator, contact the upstream maintainer to confirm — these are flagged in `scripts/update-timeless-data.js` and should be revisited in the same commit that re-enables the registry entry.

---

## 3. Bundled CC BY-NC-SA 3.0 data — Path of Exile Wiki

- **Source:** <https://www.poewiki.net/>
- **License:** Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported (<https://creativecommons.org/licenses/by-nc-sa/3.0/>)
- **Omnilyth files that derive from the wiki:**
  - `src/data/leveling/acts1-data.js` through `acts4-data.js` (and any further `actsN-data.js` files) — composite of HeartofPhos/exile-leveling + poe-leveling.com + poewiki.net for act/zone/quest data.
  - `src/data/leveling/gemAvailability.js` — quest-reward and gem-vendor metadata sourced from <https://www.poewiki.net/wiki/Quest_Rewards> and <https://www.poewiki.net/wiki/Skill_gem>.
  - `src/data/leveling/trials-data.js` — Trial of Ascendancy zone metadata sourced from <https://www.poewiki.net/wiki/Trial_of_Ascendancy>.
  - `src/calculators/colorChances.js` — cross-references the Item Socket page (<https://www.poewiki.net/wiki/Item_socket>) for socket-coloring weights; the algorithm itself is independent.
- **Each file carries an in-source attribution header.** Do not strip those headers when refactoring.

### CC BY-NC-SA 3.0 — NonCommercial clause callout

The wiki license forbids **commercial use** of derivative data. As of 2026-05-07, Omnilyth has no monetisation. Donations / Patreon are generally accepted as non-commercial for hobby projects and remain defensible. **Ads, paid features, sponsorships, or paid premium tiers would cross the line** and would require either replacing the wiki-derived data with a permissively-licensed alternative or restricting the commercial deployment to data that isn't wiki-derived. Re-evaluate before introducing any monetisation surface.

### CC BY-NC-SA 3.0 — ShareAlike clause

If you fork Omnilyth's wiki-derived data files, you must license your derivative *of those files* under the same CC BY-NC-SA 3.0 (or compatible) terms. The ShareAlike clause does not propagate to the rest of the project — the project license (GPL-3.0) covers Omnilyth's original source code and the wiki data sits alongside it under its own license.

### Composite source — HeartofPhos/exile-leveling

- **Upstream:** <https://github.com/HeartofPhos/exile-leveling>
- The `src/data/leveling/acts*-data.js` files are a composite that includes structure originally from HeartofPhos/exile-leveling. Check the upstream repo for the current license posture; the in-source attribution header in each file names HeartofPhos as a contributing source.

---

## 4. Bundled CC0 / public-domain data

### Siveran's chromatic calculator

- **Upstream:** <https://siveran.github.io/calc.html> · <https://github.com/Siveran/siveran.github.io>
- **License:** CC0 (public domain dedication) — no attribution legally required; we credit anyway because it's the right thing to do.
- **Used in:** `src/calculators/chromaticCalc.js`. Siveran's original probability calculations form the foundation of Omnilyth's chromatic / coloring tools.

---

## 5. Game data and assets — fair use of GGG IP

The following files contain Path of Exile game data compiled from public sources (the official client, poedb.tw, the wiki, and grindinggear/* GitHub exports). The data, item names, skill names, mod text, sprite icons, and related content remain the intellectual property of [Grinding Gear Games](https://www.grindinggear.com/) and are used here under their [fan content policy](https://www.pathofexile.com/legal-rules/general-rules) for the purpose of building community tools.

| File | Probable source |
|---|---|
| `src/data/itemMods.js` (~3.08 MB) | poedb.tw / GGG client export |
| `src/data/clusterJewelData.json` (~692 KB) | GGG cluster jewel data |
| `src/data/gemData.js` | poedb.tw / scripts/generateGemData.js |
| `src/data/vendorLevelingStats.js` | GGG item bases |
| `src/data/mapModsRegular.js`, `src/data/mapModsT17.js` | poedb.tw / GGG map mod export |
| `src/data/scarabData.js` | poedb.tw / GGG scarab export |
| `src/data/passive/passiveTreeData_*.json` | grindinggear/skilltree-export |
| `src/data/atlas/atlasTreeData.json` | grindinggear/atlastree-export |
| `src/data/timeless/alternatePassiveSkills.json` | GGG timeless-jewel data dump |
| `src/data/timeless/alternatePassiveAdditions.json` | GGG timeless-jewel data dump |
| `src/data/timeless/translations.json` | GGG localisation export |
| Sprite icons rendered via `web.poecdn.com` | Hot-linked from GGG's CDN, never bundled |

If you are a Grinding Gear Games rights holder and believe any of this content is incorrectly attributed or should be removed, please open an issue at <https://github.com/EtherealCarnivore/project-omnilyth/issues> or contact the maintainer directly via that repo. Omnilyth is not affiliated with, endorsed by, or connected to Grinding Gear Games.

---

## 6. Bundled visual assets (`public/`)

| Asset | Origin | License |
|---|---|---|
| `public/Chromatic_Orb.png`, `Omen_of_Blanching.png`, etc. | Path of Exile game assets (GGG IP) | Used under GGG fan content policy |
| `public/favicon-*.svg`, `public/banner.png` | Custom Omnilyth branding | Project license (GPL-3.0) |
| `public/poe-resources/drawing*.png`, `image_*.jpg` | Origin currently being audited (may be user-created or wiki-screenshots) | TBD — see Phase 4 of the licensing plan |
| `public/downloads/omnilyth-watcher-*.exe` | Tauri desktop binary, separate project | Out of scope here — the Watcher repo carries its own license |

If the `public/poe-resources/` audit determines those files are wiki-derived, a `public/poe-resources/CREDITS.md` will be added with the appropriate CC BY-NC-SA 3.0 attribution. Until that audit completes, treat them as ambiguous.

---

## 7. Community APIs (runtime data, not bundled)

These are not licensed with the project — they are public APIs Omnilyth queries at runtime. Listed for completeness:

- **poe.ninja** (<https://poe.ninja/api>) — economy data, fetched via the Cloudflare Worker proxy.
- **pathofexile.com** — official trade and league APIs, fetched via the same proxy.
- **poewiki.net MediaWiki API** — patch notes discovery, fetched via the same proxy.
- **web.poecdn.com** — GGG's CDN for gem and item sprite icons; hot-linked from the browser, never bundled.

---

## How to keep this register current

When you add a new dependency or bundled asset:

1. Add the entry to the appropriate section above.
2. If it's a new dep, verify its license via `npm view <pkg> license` and add the row to §1.
3. If it's a non-permissively licensed dep (anything other than MIT / Apache-2.0 / BSD / ISC / Zlib / CC0), open a discussion before merging — it may force a license change on the project.
4. Update [`NOTICE`](NOTICE) if the new dep requires NOTICE-file attribution (Apache-2.0 deps, anything with explicit attribution clauses).
5. If a wiki-derived data file is added, add an in-source attribution header to the file and a row to §3.

---

*Last updated: 2026-05-07 — initial post-public-flip register. Supersedes the earlier human-readable [`ATTRIBUTIONS.md`](ATTRIBUTIONS.md) as the formal source of truth.*
