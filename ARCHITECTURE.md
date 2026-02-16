# Project Omnilyth - Architecture Document

> **Last Updated:** 2026-02-16
> **Version:** 1.0.0
> **Author:** EtherealCarnivore
> **Status:** Active Development

---

## Table of Contents

1. [System Overview](#1-system-overview)
2. [Architecture Principles](#2-architecture-principles)
3. [Technology Stack](#3-technology-stack)
4. [Project Structure](#4-project-structure)
5. [Component Architecture](#5-component-architecture)
6. [Design System](#6-design-system)
7. [Data Flow & Integration](#7-data-flow--integration)
8. [Build & Deployment](#8-build--deployment)
9. [Development Workflow](#9-development-workflow)
10. [Quality & Standards](#10-quality--standards)
11. [Roadmap & Evolution](#11-roadmap--evolution)
12. [References & Credits](#12-references--credits)

---

## 1. System Overview

### 1.1 Mission Statement

**Project Omnilyth** is an all-in-one toolkit for Path of Exile players, consolidating crafting calculators, atlas tools, and economy utilities into a unified dark-mode interface.

**Problem Solved:** Eliminates the need for 47+ browser tabs by providing integrated, real-time game utilities in one place.

### 1.2 Repository Architecture

**This repository (`omnilyth-core-public`)** contains the **production build** and deployment artifacts.

```
┌─────────────────────────────────────────────────┐
│ Private Source Repo (project-omnilyth)         │
│ - React/TypeScript source code                 │
│ - Vite configuration                           │
│ - Component development                        │
└────────────────┬────────────────────────────────┘
                 │ npm run build
                 ↓
┌─────────────────────────────────────────────────┐
│ Public Deployment Repo (omnilyth-core-public)  │ ← YOU ARE HERE
│ - Built/compiled assets only                   │
│ - index.html entry point                       │
│ - Minified JS/CSS bundles                      │
└────────────────┬────────────────────────────────┘
                 │ GitHub Pages
                 ↓
┌─────────────────────────────────────────────────┐
│ Live Site                                       │
│ https://etherealcarnivore.github.io/           │
│       omnilyth-core-public/                    │
└─────────────────────────────────────────────────┘
```

**Deployment Model:** Build artifacts are pushed to this public repo, then served via GitHub Pages.

### 1.3 Live Environment

- **URL:** https://etherealcarnivore.github.io/omnilyth-core-public/
- **Deployment Path:** `/the-omilyth/` (subdirectory)
- **Hosting:** GitHub Pages (automatic deployment from `gh-pages` branch)

---

## 2. Architecture Principles

### 2.1 Core Principles

1. **Dark-First Design** - PoE-themed dark mode is primary, light mode optional
2. **Modular Tools** - Each calculator/utility is self-contained
3. **Live Data Integration** - Real-time pricing from poe.ninja
4. **Performance Optimized** - Minified production builds with content hashing
5. **Community Focused** - Transparent development, proper attribution
6. **Mobile Ready** - Responsive design (in progress)

### 2.2 Design Philosophy

- **"As simple as possible, but no simpler"** - Complex game calculations made accessible
- **No Authentication** - Public tools, no user accounts needed
- **Privacy First** - Cookie-based preferences only, no tracking
- **PoE Community Tone** - Humor, honesty, and game culture references

---

## 3. Technology Stack

### 3.1 Frontend Framework

| Technology | Version | Purpose |
|------------|---------|---------|
| **React** | 18+ | UI component framework |
| **Vite** | Latest | Build tool & dev server |
| **Tailwind CSS** | 4.x | Utility-first styling |
| **TypeScript** | Latest | Type-safe development (source) |

### 3.2 Build & Deployment

- **Bundler:** Vite (module preloading, content hashing)
- **Minification:** Production optimized (CSS: 379KB, JS: 390KB)
- **Hosting:** GitHub Pages
- **CI/CD:** Automated deployment from main branch

### 3.3 External Integrations

- **poe.ninja API** - Live price data for currency/items
- **PoE Trade Links** - Direct trade search integration

---

## 4. Project Structure

### 4.1 Repository Structure (Production Build)

```
omnilyth-core-public/
├── .git/                          # Git repository metadata
├── assets/                        # Compiled build artifacts
│   ├── index-{HASH}.css          # Tailwind CSS bundle (379KB)
│   └── index-{HASH}.js           # React app bundle (390KB)
├── README.md                      # User-facing documentation
├── ARCHITECTURE.md                # THIS FILE - Technical documentation
├── index.html                     # Entry point (691B)
├── Chromatic_Orb.png             # Favicon (8KB)
├── Omen_of_Blanching.png         # Feature image (14KB)
└── banner.png                    # Hero banner (922KB)
```

**Note:** Content hashes (`{HASH}`) change with each build for cache busting.

### 4.2 Source Repository Structure (Inferred)

```
project-omnilyth/ (Private)
├── src/
│   ├── components/               # React components
│   │   ├── calculators/         # Calculator modules
│   │   ├── layout/              # Layout components
│   │   └── ui/                  # Reusable UI elements
│   ├── utils/                   # Helper functions
│   ├── api/                     # poe.ninja integration
│   ├── hooks/                   # Custom React hooks
│   ├── styles/                  # Tailwind config & custom CSS
│   └── App.tsx                  # Main application
├── public/                       # Static assets
├── vite.config.ts               # Vite configuration
├── tailwind.config.js           # Tailwind configuration
├── tsconfig.json                # TypeScript config
└── package.json                 # Dependencies
```

---

## 5. Component Architecture

### 5.1 Feature Modules

#### Crafting - Coloring (Socket Color Modification)
- **Chromatic Calculator** - Vorici bench vs raw chromes
- **Tainted Chromatic** - Corrupted item coloring
- **Omen of Blanching** - White socket probability
- **Jeweller's Method** - Socket trick calculator

#### Crafting - Linking & Socketing
- **Fusing Calculator** - 6-link probability with Omen of Connections
- **Socket Calculator** - Jeweller's Orb math

#### Crafting - Items & Jewels
- **Item Mod Regex Generator** - Stash search patterns
- **Cluster Jewel Calculator** - Notable compatibility checker

#### Atlas / Mapping
- **Map Mod Regex Generator** - Map modifier search patterns

#### External Tools
- **Timeless Jewel Calculator** - Skill tree seed searching

### 5.2 Component Patterns

**Calculator Component Structure:**
```
Calculator Module
├── Input Fields (socket count, colors, item type)
├── Cost Calculation Logic (real-time)
├── poe.ninja Price Fetching (async)
├── Results Display (comparison table)
└── Export/Copy Functionality
```

**Common UI Components:**
- `.calc-input` - Styled input fields
- `.calc-button` - Action buttons with hover states
- `.glass-card` - Card containers with backdrop blur
- `.result-row` - Table row styling with alternating colors

---

## 6. Design System

### 6.1 Color Palette

#### Dark Theme (Primary)
```css
--bg-primary: #0a0a0a        /* Main background */
--bg-card: #222324           /* Card/container background */
--bg-input: #444444          /* Input field background */
--border: #555555            /* Border color */
--text-primary: #f0f0f0      /* Main text */
--text-muted: #999999        /* Secondary text */
--poe-gold: #daa520          /* PoE-specific accent */
```

#### Light Theme (Optional)
```css
--bg-primary: #f0f0f0
--bg-card: #ffffff
--bg-input: #e8e8e8
--text-primary: #1a1a1a
--text-muted: #666666
```

### 6.2 Typography

**Font Stacks:**
- **Sans-serif:** System UI, Inter, Segoe UI, Roboto, Arial
- **Monospace:** UI Monospace, SFMono, Menlo, Monaco

**Font Sizes:** `.75rem` to `2.25rem` (12px to 36px)
**Font Weights:** Medium (500), Semibold (600), Bold (700)

### 6.3 Responsive Design

**Breakpoints:**
- `sm` - 640px (40rem) - Mobile landscape
- `lg` - 1024px (64rem) - Desktop

**Status:** Mobile optimization currently in progress (partially functional)

### 6.4 Animation & Effects

- **Default Transition:** 150ms cubic-bezier(0.4, 0, 0.2, 1)
- **Hover Effects:** Brightness 110-125%, transform scale
- **Glass Effect:** `backdrop-blur(8px)` + gradient + transparency
- **Pulse Animation:** 2s infinite for loading states

---

## 7. Data Flow & Integration

### 7.1 poe.ninja API Integration

**Purpose:** Real-time pricing for currency items

**Flow:**
```
Component Mount
    ↓
Fetch poe.ninja API
    ↓
Parse JSON Response
    ↓
Update State (currency prices)
    ↓
Calculate Costs
    ↓
Display Results
```

**Endpoints Used:**
- `/api/data/currencyoverview?league={league}&type=Currency`
- `/api/data/itemoverview?league={league}&type=DivinationCard` (if needed)

**Error Handling:** Fallback to cached prices or default values

### 7.2 State Management

**Pattern:** React Hooks (useState, useEffect, custom hooks)

**State Hierarchy:**
```
App State (Global)
├── Theme (dark/light)
├── League Selection (current PoE league)
└── Pinned Tools (cookie-based)

Calculator State (Local)
├── Input Values
├── Fetched Prices
├── Calculated Results
└── UI State (loading, errors)
```

### 7.3 Regex Library System

**Purpose:** Cookie-based storage for saving and managing regex patterns across all tools

**Architecture:**

```
┌──────────────────────────────────────────────────────┐
│ Regex Tools (Map Mods, Gems, Scarabs, etc.)        │
│ - Generate regex patterns                           │
│ - SaveRegexButton component                         │
└────────────────┬─────────────────────────────────────┘
                 │
                 ↓ useRegexLibrary hook
┌──────────────────────────────────────────────────────┐
│ Cookie Storage Layer (src/utils/regexLibrary.js)    │
│ - CRUD operations (add, update, delete, clearAll)   │
│ - Storage validation (4KB limit)                    │
│ - Pattern deduplication                             │
│ - Auto-generated UUIDs                              │
└────────────────┬─────────────────────────────────────┘
                 │
                 ↓ Browser Cookies
┌──────────────────────────────────────────────────────┐
│ Cookie: omnilyth_regex_library                      │
│ - Max size: ~4KB (~50 patterns)                     │
│ - Max age: 365 days                                 │
│ - SameSite: Strict                                  │
│ - Structure: {version: 1, patterns: [...]}         │
└──────────────────────────────────────────────────────┘
```

**Data Schema:**
```javascript
{
  version: 1,
  patterns: [
    {
      id: "uuid-v4",
      name: "User-provided name",
      pattern: "regex pattern string",
      tool: "tool-id",              // e.g., "map-mods", "gem-regex"
      toolLabel: "Display name",    // e.g., "Map Mod Regex"
      createdAt: "ISO timestamp",
      updatedAt: "ISO timestamp"
    }
  ]
}
```

**Components:**
- **SaveRegexButton** (`src/components/SaveRegexButton.jsx`) - Reusable save button with modal
- **RegexLibraryPage** (`src/pages/RegexLibraryPage.jsx`) - Library management interface
- **useRegexLibrary** (`src/hooks/useRegexLibrary.js`) - React hook for state management

**Features:**
- 80% storage capacity warnings
- Duplicate pattern detection
- Real-time search and filtering
- Tool-based categorization
- One-click copy to clipboard
- Confirmation dialogs for destructive actions
- WCAG 2.1 AA accessibility compliance

**Storage Limits:**
- Maximum cookie size: 4KB (browser limit)
- Estimated capacity: 50-60 patterns
- Warning threshold: 80% (3.2KB)
- Pattern name limit: 50 characters

### 7.3 Data Persistence

**Client-Side Only:**
- **Cookies** - Theme preference, pinned tools
- **Local Storage** - Calculator history (future)
- **No Backend** - No server-side storage

---

## 8. Build & Deployment

### 8.1 Build Process

**Source Repo → Build → Deploy Repo:**

```bash
# In private source repo (project-omnilyth)
npm run build

# Vite builds to dist/
dist/
├── assets/
│   ├── index-{HASH}.css
│   └── index-{HASH}.js
├── index.html
└── [static assets]

# Push dist/ contents to omnilyth-core-public repo
git add .
git commit -m "Deploy: project-omnilyth@{COMMIT_HASH}"
git push origin main

# GitHub Pages automatically deploys from gh-pages branch
```

### 8.2 Deployment Configuration

**GitHub Pages Settings:**
- **Source Branch:** `gh-pages`
- **Build Tool:** None (pre-built files)
- **Custom Domain:** Not configured
- **HTTPS:** Enforced

**Base Path:** `/the-omilyth/` (configured in Vite)

### 8.3 Versioning Strategy

**Content Hash Versioning:**
- Vite generates unique hashes for each build
- `index-DPCNhmp3.js` → `index-{NEW_HASH}.js`
- Ensures browser cache invalidation on updates

**Git Tagging:** Not currently used (consider for releases)

### 8.4 Rollback Procedure

**To Rollback Deployment:**
```bash
# From omnilyth-core-public repo
git log --oneline  # Find previous working commit
git revert {COMMIT_HASH}  # Or git reset --hard {COMMIT_HASH}
git push origin main --force  # Force push if using reset
```

---

## 9. Development Workflow

### 9.1 Development Environment

**Source Repo Setup:**
```bash
git clone <private-repo-url>
cd project-omnilyth
npm install
npm run dev  # Vite dev server at localhost:5173
```

**Hot Module Replacement:** Enabled via Vite for instant updates

### 9.2 Local Development

**Commands:**
- `npm run dev` - Start dev server with HMR
- `npm run build` - Production build
- `npm run preview` - Preview production build locally
- `npm run lint` - Run ESLint (if configured)

### 9.3 Git Workflow

**Branch Strategy:**
- **main** - Production-ready code
- **feature/{name}** - New features
- **fix/{name}** - Bug fixes

**Commit Convention:**
```
feat: Add new calculator module
fix: Correct Omen of Connections pricing
docs: Update README with new features
deploy: EtherealCarnivore/project-omnilyth@{HASH}
```

### 9.4 Testing Strategy

**Current:** Manual testing only
**Planned:**
- Unit tests for calculation logic
- Integration tests for API calls
- Visual regression testing for UI components

---

## 10. Quality & Standards

### 10.1 Code Standards

**TypeScript (Source):**
- Strict mode enabled
- No implicit any
- Explicit return types for functions

**React:**
- Functional components with hooks
- PropTypes or TypeScript interfaces
- Consistent file naming (PascalCase for components)

**CSS:**
- Tailwind utility classes preferred
- Custom CSS only for complex animations
- BEM naming for custom classes (if any)

### 10.2 Performance Standards

**Bundle Size:**
- CSS: 379KB (acceptable for utility framework)
- JS: 390KB (includes React + all calculators)
- **Target:** Keep under 500KB combined

**Lighthouse Scores (Target):**
- Performance: 90+
- Accessibility: 95+
- Best Practices: 100
- SEO: 100

### 10.3 Accessibility

**Current Implementation:**
- Semantic HTML (`<button>`, `<input>`, `<label>`)
- Focus states for keyboard navigation
- Color contrast ratios (AA standard)
- Alt text for images

**To Improve:**
- ARIA labels for complex interactions
- Screen reader testing
- Keyboard shortcuts for power users

### 10.4 Browser Support

**Target Browsers:**
- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Mobile Safari (iOS 14+)
- Chrome Android (latest)

**Not Supported:**
- Internet Explorer (deprecated)
- Opera Mini (limited JS support)

---

## 11. Roadmap & Evolution

### 11.1 Current Status (v1.0)

**Live Features:**
- ✅ 4 Coloring calculators
- ✅ 2 Linking/Socketing calculators
- ✅ 2 Item/Jewel tools
- ✅ 1 Atlas/Mapping tool
- ✅ 1 External tool integration
- ✅ poe.ninja live pricing
- ✅ Dark theme
- ✅ GitHub Pages deployment

### 11.2 In Progress

| Priority | Feature | Status | ETA |
|----------|---------|--------|-----|
| HIGH | Mobile UI Optimization | 🚧 In Progress | Q1 2026 |
| HIGH | Fix Calculator Bugs | 🚧 In Progress | Q1 2026 |
| MEDIUM | Timeless Jewel Improvements | 📋 Planned | Q2 2026 |

### 11.3 Planned Features

**Near-Term (Q1-Q2 2026):**
- Pinning Functionality (cookie-based dashboard favorites)
- Better Category Split & Visual Organization
- Additional Category Coloring
- Deeper poe.ninja API Integration

**Mid-Term (Q3-Q4 2026):**
- Vendor Recipes Reference Tool
- Trade Macro Integration
- Build Planner Integration
- Community Presets/Sharing

**Long-Term (2027+):**
- User Accounts (optional)
- Saved Calculator Configurations
- Historical Price Charts
- Mobile App (React Native?)

### 11.4 Technical Debt

**Known Issues:**
- Mobile responsiveness needs refactor
- Omen of Connections missing price info
- No automated testing
- Bundle size could be optimized (code splitting)
- No error boundary implementation

**Refactoring Priorities:**
1. Extract calculator logic to shared utilities
2. Implement proper TypeScript interfaces
3. Add unit tests for calculation functions
4. Optimize bundle with dynamic imports
5. Implement error boundaries

---

## 12. References & Credits

### 12.1 Original Sources

**Base Project:**
- **Siveran's Chromatic Calculator**
  - Repository: https://github.com/Siveran/siveran.github.io
  - License: MIT (assumed)
  - Used: Chromatic calculation algorithms

**Timeless Jewel Calculator:**
- **vilsol/timeless-jewels**
  - Repository: https://github.com/vilsol/timeless-jewels
  - License: MIT
  - Used: Skill tree integration

### 12.2 External APIs & Services

- **poe.ninja** - Currency and item pricing data
  - API Documentation: https://poe.ninja/api
  - Rate Limits: Unknown (use caching)
  - Attribution: Required in UI

- **PoE Trade** - Official trade site integration
  - URL: https://www.pathofexile.com/trade

### 12.3 Design Inspiration

- **Path of Exile UI** - Color palette and theming
- **PoE Overlay** - Tool organization patterns
- **Awakened PoE Trade** - Pricing display format

### 12.4 Community Resources

- **r/pathofexile** - User feedback and feature requests
- **PoE Discord** - Community testing and bug reports

---

## Appendix A: Environment Variables

**Not Currently Used** - All configuration is build-time constants.

**Future Consideration:**
```env
VITE_POE_NINJA_API_URL=https://poe.ninja/api/data
VITE_DEFAULT_LEAGUE=Necropolis
VITE_ANALYTICS_ID=UA-XXXXXX-X (optional)
```

---

## Appendix B: Monitoring & Analytics

**Current:** None
**Planned:** Google Analytics or privacy-focused alternative (Plausible)

**Metrics to Track:**
- Page views per calculator
- Average session duration
- Most used tools
- Error rates
- API response times

---

## Appendix C: Security Considerations

**Current Security Model:**
- No user authentication → No password vulnerabilities
- Client-side only → No server-side attacks
- No sensitive data storage → No data breaches
- HTTPS enforced → Man-in-the-middle protection

**Potential Risks:**
- XSS via user input (mitigated by React's built-in escaping)
- API rate limiting (poe.ninja could block excessive requests)
- Supply chain attacks (npm dependencies)

**Best Practices:**
- Regular dependency updates (`npm audit`)
- Content Security Policy headers
- Subresource Integrity for CDN assets
- Regular security audits

---

## Document Change Log

| Date | Version | Changes | Author |
|------|---------|---------|--------|
| 2026-02-16 | 1.0.0 | Initial architecture document | EtherealCarnivore |

---

## Contact & Maintenance

**Maintainer:** EtherealCarnivore
**Repository:** https://github.com/EtherealCarnivore/omnilyth-core-public
**Issues:** GitHub Issues (for bug reports)
**Contributions:** Open to pull requests (source repo only)

---

*"One architecture document to rule them all, one document to find them, one document to bring all the devs together, and in the markdown bind them."*
