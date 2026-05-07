# omnilyth-core-public — compiled deployment

This repository hosts the **compiled production deployment** of [Project Omnilyth](https://github.com/EtherealCarnivore/project-omnilyth) — a Path of Exile 1 & 2 companion toolkit (crafting calculators, regex generators, atlas/leveling planners, build utilities).

This is **not the source code repo.** Files here are the output of `npm run build` plus the static GitHub Pages SPA shell.

- **Live site:** [omnilyth.app](https://omnilyth.app/)
- **Source repo:** [github.com/EtherealCarnivore/project-omnilyth](https://github.com/EtherealCarnivore/project-omnilyth)
- **Deploy pipeline:** GitHub Actions on the source repo builds and pushes to this repo's `gh-pages` branch on every commit to `master`.

## License

This deployment is licensed under the **GNU General Public License v3.0 or later** — the same terms as the source. See [`LICENSE`](LICENSE) for the full text.

A short scope note (also at the top of LICENSE):
- The GPL-3.0 covers Omnilyth's original source code.
- The `workers/poe-ninja-proxy.js` Cloudflare Worker (which is **not** part of this deployment — it lives at `api.omnilyth.app` and is sourced from the source repo's `workers/` directory) is separately licensed under MIT. See [`workers/LICENSE`](https://github.com/EtherealCarnivore/project-omnilyth/blob/master/workers/LICENSE) in the source repo.
- Path of Exile sprites, item names, skill names, mod text, atlas tree, passive tree, and other GGG-owned assets bundled or referenced here remain the property of Grinding Gear Games and are used under [GGG's fan content policy](https://www.pathofexile.com/legal-rules/general-rules). Path of Exile is a trademark of Grinding Gear Games.
- Some bundled data derives from the Path of Exile Wiki under CC BY-NC-SA 3.0; see [`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md).

## Corresponding source

GPL-3.0 §6 requires the corresponding source for the distributed binary to be available. The complete corresponding source for this deployment is the source repo at [github.com/EtherealCarnivore/project-omnilyth](https://github.com/EtherealCarnivore/project-omnilyth), checked out at the commit recorded in this repo's most recent commit message (the deploy workflow includes the source SHA). Anyone receiving this deployment is entitled to that source under the GPL-3.0 terms.

## Issues / contributions

Please **don't open issues or PRs against this repo.** It's a write-only deploy mirror — any changes made here are wiped on the next push from the source-side CI.

For bugs, feature requests, contributions:
- Bugs / features: [project-omnilyth/issues](https://github.com/EtherealCarnivore/project-omnilyth/issues)
- Security vulnerabilities: see [`SECURITY.md`](https://github.com/EtherealCarnivore/project-omnilyth/blob/master/SECURITY.md) in the source repo.
- Pull requests: source repo only; this repo accepts no manual changes.

## Disclaimer

Omnilyth is a fan-made tool and is not affiliated with, endorsed by, or connected to Grinding Gear Games. Path of Exile and all related content, names, and imagery are trademarks and copyrights of Grinding Gear Games.
