# GSE vs GRIP — Copyright / IP Violation Evidence Package

Evidence that **GRIP – Enhanced Macro Sequencer (GRIP-EMS)** and its associated public web service **LazyGrip.net** are a reverse-engineered functional/design clone of **GSE – Gnome Sequencer Enhanced**, built to ingest GSE content, that reproduces GSE's distinctive signature design, circumvents GSE's anti-scraping protection, and removes the GSE.Tools owner-identifier from ingested sequences.

**Primary rights holder for this package:** the GSE addon author (**Timothy Luke**) and the GSE / GSE.Tools project. Prepared by Larry A. Thiessen ("ScaryLarryGames", GSE United) as a downstream creator and evidence-gatherer; the GSE-side claims belong to the GSE author, who should take this to counsel.

> **NOT LEGAL ADVICE.** Two-sided, honesty-first (see "What we do NOT claim"). Every technical finding is line-cited and reproducible.

---

## The players & timeline (to be finalized with dates from the Discord/CurseForge record)

| | Party | Role |
|---|---|---|
| **GSE / GSE.Tools** | Timothy Luke (+ GSE United community) | Original addon, ~2015–2016. ~12–13 years of prior art. Signature "Priority" step function, the `!GSE3!` format, the PlatformID owner-identity system. |
| **GRIP-EMS** | **sirsataana / "Sataana"** *(to confirm via CurseForge project 1489414 ownership)* | 2026 addon that imports GSE libraries and strips the owner ID. |
| **LazyGrip.net** | **sirsataana / "Sataana"** (site owner) with **"Beard3d_Gamer"** & **"Slowdog"** | Public web "Workshop" that decodes GSE strings (reproducing the work in plaintext) and strips the owner IDs, server-side. |
| **House of Lazy Macros** (Discord) | the above individuals | The venue where — per the rights holders — this was discussed/coordinated over ~the last 4–5 months. **Record to be gathered (see `evidence/discord/`).** |

The single most important nexus fact: **the same operator (sirsataana/Sataana) is behind both the addon that strips owner-IDs and the website that strips owner-IDs.** Confirm and lock this down early.

---

## The core findings (all line-cited in `exhibits/`)

1. **Functional & design clone of GSE, derived one-way.** GSE predates GRIP by ~12–13 years; GRIP reads GSE's *internal* format and reproduces GSE's *non-platform-mandated* signature design. The clearest single proof: **GSE's distinctive "Priority" triangular `N·(N+1)/2` expansion is output-identical in GRIP** (`[1,1,2,1,2,3]` for N=3) despite independently structured code. There is no independent-invention defense given a decade of GSE as prior art. → `exhibits/grip-vs-gse-forensic-comparison.md`.

2. **Circumvention of GSE's content protection, with documented intent.** GSE wraps its runtime library in a proxy expressly to **"deny in-memory scraping by third-party addons"** (`GSE/API/Storage.lua:9-16`). GRIP engineered a raw-SavedVariables **workaround** *because* GSE locked it (`Import/LegacyMigrate.lua:92-99`). GRIP's own comments acknowledge GSE's protection and route around it. → forensic exhibit, Part 2.

3. **Removal of the GSE owner-identifier (CMI) at every stage.** GSE stamps each sequence with `PlatformID` (GSE.Tools server-record identity, the ownership handle GSE clears on copy so a duplicate "never resolves to the same server record"), a `HelpURL` gse.tools link, and an **Ed25519 server-signed `Checksum`**. GRIP: `PlatformID` **removed — 0 occurrences in its entire tree**; `HelpURL`/`Checksum` absent from the exported/shared artifact; the public LazyGrip decoder strips them too while reproducing the work in plaintext. → `exhibits/grip-1202-cmi-analysis.md`, `exhibits/grip-cmi-evidence-exhibit.md`, `exhibits/grip-lazygrip-webtool-exhibit.md`, forensic exhibit Part 3.

4. **Marketing misrepresentation.** GRIP/LazyGrip publicly positions itself as a *different, superior* engine ("holds on failed cast instead of skipping"). That differentiator **is not implemented in GRIP's engine code** (its step advance is `step = step % N + 1`, every press, exactly like GSE; no cast-success gate exists). → `exhibits/grip-vs-gse-functional-identity.md`.

---

## Contents

| Path | What it is |
|---|---|
| `exhibits/grip-vs-gse-forensic-comparison.md` | **Primary code exhibit** — full 5-subsystem source-to-source diff; functional/design clone, lock circumvention, owner-ID removal. Precedence + "what disproves a source copy" + "what to plead." |
| `exhibits/grip-vs-gse-functional-identity.md` | Functional identity + the false "holds on failed cast" marketing claim vs the code. |
| `exhibits/grip-cmi-evidence-exhibit.md` | Code-cited import→export path across all 64 GRIP releases; PlatformID omission. |
| `exhibits/grip-1202-cmi-analysis.md` | Two-sided DMCA §1202 / CMI legal memo (take to an IP lawyer). |
| `exhibits/grip-lazygrip-webtool-exhibit.md` | The public LazyGrip web tools: on-demand plaintext reproduction + server-side owner-ID stripping. |
| `exhibits/SLG-Sequences-LICENSE-downstream-creator-example.txt` | A downstream creator's All-Rights-Reserved license (ScaryLarryGames) — example of the licensed content the pipeline ingests. |
| `evidence/lazygrip-webtool/` | Reproducible decode evidence (original + decoded; before/after convert). |
| `evidence/discord/` | **TO GATHER** — House of Lazy Macros Discord record of coordination/intent (last ~4–5 months). |
| `data/grip_version_scan.csv` | Per-version scan of all 64 GRIP releases. |

---

## Relationship to the ScaryLarryGames case

There are **two separate cases** on overlapping facts:
- **This repo (GSE / Timothy Luke):** GRIP's derivation from *GSE itself* — GSE's format, GSE's signature design, GSE's PlatformID system, GSE's anti-scrape protection, and GSE's trademark/branding if applicable. GSE is the primary rights holder.
- **The `GRIP-IP-Complaint` repo (ScaryLarryGames / Larry Thiessen):** GRIP's reproduction/derivation of *one downstream creator's* All-Rights-Reserved sequences, routed through the same pipeline. A content-creator's copyright + license case, aimed at CurseForge.

They share the same technical exhibits (copied here so this package is self-contained) but are distinct legal claims with distinct rights holders. Larry's case is included as a **concrete downstream-harm example**, not the centerpiece.

---

## What we do NOT claim (credibility discipline)

- **Not source-code copying.** A full 5-subsystem diff found no copied source, and found affirmative *disproof* of a "copied-then-renamed" theory: GSE's ChaCha20 encryption codec and its CBOR delta/sync engine are **absent** from GRIP; GRIP's ReversePriority/Random modes diverge. This is a **reverse-engineered functional/design clone**, not a file copy — a distinct and defensible claim. Do not overstate it.
- **Not an established "they used an AI to transpile" method.** Recorded as an allegation for discovery, not a fact provable from the shipped binaries.
- **Not §1201 DRM circumvention** for the SavedVariables read (plaintext on disk); the point there is intent and non-consent.

## Still to gather
- **Discord record** (House of Lazy Macros): statements showing knowledge of GSE's licenses/protection and intent — the coordination evidence — over the last ~4–5 months. See `evidence/discord/`.
- **GSE's own rights basis:** GSE's license terms, any trademark on "GSE"/"Gnome Sequencer Enhanced", and GSE.Tools terms — the GSE author to provide.
- **Confirmed operator identity:** CurseForge project 1489414 ownership + WHOIS for lazygrip.net + Discord handles → real identities.
- **Dates:** first GRIP release, first GSE-import feature, PlatformID introduction (2026-04-25 per the SLG package), and the Discord timeline.
