# Project Omnilyth

> *"One tool to rule them all, one tool to find them, one tool to bring them all, and in the darkness... calculate their chromatic costs."*

---

**Project Omnilyth** is an evolving, all-in-one toolkit for Path of Exile — built for exiles who are tired of having 47 browser tabs open just to play a game.

We're combining crafting calculators, atlas tools, economy utilities, and more into a single, unified dark-mode interface. Because spreadsheets are for accountants, not gamers. *(No offense to accountants who also play PoE — we know you exist.)*

**Live at:** [etherealcarnivore.github.io/omnilyth-core-public](https://etherealcarnivore.github.io/omnilyth-core-public/)

---

## What's Live

### Crafting — Coloring
- **Chromatic Calculator** — Vorici bench vs raw chromes, with live poe.ninja prices
- **Tainted Chromatic** — For when you've already bricked your item and need to cope
- **Omen of Blanching** — White socket probability with cost breakdowns
- **Jeweller's Method** — The crafting bench socket trick most people learn about too late

### Crafting — Linking & Socketing
- **Fusing Calculator** — How many fusings until 6-link? Spoiler: more than you think. Includes Omen of Connections support
- **Socket Calculator** — Jeweller's Orb math so you don't waste 300 on a 4-socket

### Crafting — Items & Jewels
- **Item Mod Regex** — Generate regex patterns to find items with specific mods in your stash
- **Cluster Jewel Calculator** — Find compatible middle notables for Large Cluster Jewels, with PoE Trade link generation

### Atlas / Mapping
- **Map Mod Regex Generator** — Because typing regex by hand is a war crime

### External Tools
- **Timeless Jewel Calculator** — Interactive skill tree for timeless jewel seed searching, keystone/small node toggles *(currently links to external app)*

---

## Roadmap

> We have... *plans*. Big plans. The kind of plans that make you whisper "no way" at 3 AM.

| Status | Task |
|--------|------|
| :construction: | **Mobile UI Optimization** — Currently partially broken, needs responsive pass |
| :construction: | **Timeless Jewel Calculator Improvements** — Possibly remove manual seed entry page (doesn't make sense to exist), deeper integration into Omnilyth |
| :pushpin: | **Pinning Functionality** — Pin favorite tools to center UI dashboard, cookie-based |
| :art: | **Better Category Split** — Reorganize module categories for clarity |
| :art: | **Additional Category Coloring** — More visual distinction between module types |
| :bug: | **Fix Calculator Bugs** — Omen of Connections missing price info, misc issues |
| :chart_with_upwards_trend: | **Deeper poe.ninja API Integration** — More live price data across tools |
| :scroll: | **Vendor Recipes** — Reference tool for vendor recipe outcomes |
| :handshake: | **Add Bushido Sponsorship** — Sponsored by Bushido |
| :coffee: | **Support Skeleton** — Buy Me a Coffee / Patreon page *(will remain inactive for now — we do this for the culture)* |

---

## Tech

React + Tailwind CSS 4 + Vite. Dark theme only — we're not animals.

Live prices from [poe.ninja](https://poe.ninja). Shoutout to the real MVP.

## Credits

Originally built on [Siveran's chromatic calculator](https://github.com/Siveran/siveran.github.io). Extended and evolved by [EtherealCarnivore](https://github.com/EtherealCarnivore) into something... more.

Timeless Jewel Calculator based on [vilsol/timeless-jewels](https://github.com/vilsol/timeless-jewels).

---

*If this tool saved you even one Exalted Orb worth of bad crafting decisions, it was worth it.*

*If it didn't — skill issue.*
