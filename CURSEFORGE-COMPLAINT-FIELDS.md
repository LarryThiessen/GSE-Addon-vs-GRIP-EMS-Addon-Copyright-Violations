# CurseForge Copyright Claim — copy‑paste fields (for Timothy)

Fill CurseForge's **Copyright Claims** form and paste each block below into the matching field.
Form: https://forms.monday.com/forms/904d2c9fe157aca216d6a5bfaba85f7f

- Fields marked **[you fill]** are your personal details.
- The three big fields have a **2000‑character limit**; the counts below are within it.
- **Attach** the evidence zip at "Add any relevant files or screenshots" (README, START HERE.html, the exhibits, the Discord evidence, and the two LazyGrip screenshots).
- Verify the four **⚠ CONFIRM** items at the bottom before you submit.

---

## Your Project Name  *(max 255)*
```
GSE – Gnome Sequencer Enhanced (Advanced Macros)
```

## Your CurseForge User
```
[you fill — your CurseForge username]
```

## Full Name  *(required, legal)*
```
[you fill — your full legal name; the GSE LICENSE names "Timothy Minahan"]
```

## My Email address  *(required)*
```
[you fill — your contact email]
```

---

## Reported Copyrighted Project  *(1083 / 2000)*
```
My original work: GSE – Gnome Sequencer Enhanced, a World of Warcraft addon I have authored since ~2015–2016 — 12–13 years of prior art. I am its author (LICENSE: "Copyright (c) 2026 Timothy Minahan. All Rights Reserved.").

GSE is original creative expression: the addon's code and design, its signature "Priority" step-function algorithm, its !GSE3! export/serialization format and field vocabulary, and its GSE.Tools owner-identity system — a PlatformID that binds each sequence to its creator's account, a gse.tools HelpURL to the owner's listing, and an Ed25519 server Checksum that authenticates the published version.

Links:
- GSE (CurseForge): https://www.curseforge.com/wow/addons/gse-gnome-sequencer-enhanced-advanced-macros
- Source (GitHub): https://github.com/TimothyLuke/GSE-Advanced-Macro-Compiler
- GSE.Tools: https://gse.tools

License: All Rights Reserved. The LICENSE reads "Copyright (c) 2026 Timothy Minahan. All Rights Reserved." Redistribution, derivative works, and removal or alteration of the owner-identity are not permitted without my consent.
```

---

## Infringing Content  *(1928 / 2000)*
```
Reported as infringing: GRIP-EMS is a reverse-engineered functional & design clone of GSE that reproduces GSE's signature design, is built to read GSE's internal data, circumvents GSE's anti-scraping lock, and strips GSE's owner-identity — in independently-written code. (I do NOT claim GRIP copied GSE's source text; the claim is design/behavior appropriation, circumvention, and owner-ID removal.) All verifiable in GRIP's shipped Lua; full file/line detail in the attached exhibits.

1) Signature design reproduced. GSE's "Priority" step order expands to a triangular pattern — for a 3-step rotation, [1,1,2,1,2,3]. GRIP emits the byte-identical order from different code (GSE API/Storage.lua ~2155-2171; GRIP Engine/StepFunctions.lua ~248-262, ExpandPriority). Priority is GSE's original design, not anything WoW forces.

2) Reads GSE's internal format. GRIP's Import/LegacyMigrate.lua reads GSE's internal tables GSESequences and GSE.Library — GSE's own stored schema, not a public API.

3) Circumvents GSE's protection. GSE wraps its library "to deny in-memory scraping by third-party addons" (GSE API/Storage.lua ~9-16). GRIP documents and engineers a workaround to read GSE's raw saved data around that lock (Import/LegacyMigrate.lua ~92-99).

4) Strips GSE's owner-identity (CMI). GSE stamps each sequence with PlatformID + a gse.tools HelpURL + an Ed25519 Checksum (GSE API/Storage.lua ~704-745; API/Checksum.lua ~53-153). GRIP removes PlatformID (0 occurrences in its code) and drops the HelpURL and Checksum from what it shares — at addon import, and on its LazyGrip.net "decode" and "convert" web tools.

Proof of ownership: I author GSE (CurseForge + GitHub above), published All Rights Reserved; the PlatformID/Checksum owner-identity system GRIP strips is my own design. Not a graphical-asset claim. Full file/line citations: attached grip-vs-gse-forensic-comparison.md and grip-cmi-evidence-exhibit.md.
```

---

## Reported Infringing Projects  *(1432 / 2000)*
```
Reported infringing project (primary): GRIP – Enhanced Macro Sequencer ("GRIP-EMS")
- CurseForge Project ID: 1489414
- URL: https://www.curseforge.com/wow/addons/grip-enhanced-macro-sequencer
- Author (CurseForge): sirsataana ("the GRIP addon family by Sataana")

GRIP-EMS reproduces GSE's signature design and behavior, is built to read GSE's internal data format, engineers a workaround around GSE's anti-scraping lock, and strips GSE's owner-identity (PlatformID + gse.tools link + Ed25519 Checksum) from imported/exported content. Its store page markets the GSE import directly — "got an old dusty GSE string laying around? Chances are, you can use that as well!" Present in every release, from v1.0.4 (2026-03-21) through the current **v2.3.18** (verified 2026-08-07; SHA-256 `ec590cc0f78db732…`) — including zero `PlatformID` occurrences across all 204 Lua files of that current build. File/line detail in the Infringing Content field and the attached exhibit.

Associated work by the same author (same conduct, in the browser): the companion website LazyGrip.net, whose public "Workshop" tools reproduce a submitted GSE sequence in full plaintext and strip the GSE.Tools owner identity on convert.
- https://lazygrip.net (Workshop tools: /workshop/decode and /workshop/convert)

Scope note: I am not alleging GRIP copied GSE's program source code. My claim is design/behavior appropriation of GSE, circumvention of GSE's protection, and removal of GSE's owner-identity information, contrary to my All-Rights-Reserved license and CurseForge's IP policy.
```

---

## Add any relevant files or screenshots
Attach the evidence zip (this repo). It contains START HERE.html, the exhibits (`grip-vs-gse-forensic-comparison.md`, `grip-cmi-evidence-exhibit.md`, `grip-1202-cmi-analysis.md`, `grip-vs-gse-functional-identity.md`, `grip-lazygrip-webtool-exhibit.md`), the Discord evidence + screenshots, and the two LazyGrip captures.

## What is the action you require from this claim?
```
Under CurseForge's IP/moderation policy, I ask that GRIP-EMS be required to, at minimum: (1) cease reproducing GSE's protected design/format and enabling redistribution of GSE-derived content without the owner's consent — specifically, gate or remove the GSE-import and re-export/share functionality; (2) cease removing the GSE owner-identity (PlatformID, the gse.tools HelpURL, and the Ed25519 Checksum) from imported/exported content; and (3) cease circumventing GSE's documented anti-scraping protection. Failing that, I request removal of the infringing functionality, or of the project, under CurseForge's IP-infringement policy.
```

## Checkboxes (tick both)
- ☑ "I have read the article on Copyright claims on CurseForge"
- ☑ "I make this report in good faith, and swear I am the Owner / Author of the reported content. All information I have provided is true."

---

## ✅ Pre-submission checks — all cleared 2026-07-29

1. **Personal fields** — *resolved; nothing outstanding on the package.* The three bracketed fields are entered on the form at submission time by whoever submits it. The legal name is already on record in GSE's own `LICENSE` ("Copyright (c) 2026 Timothy Minahan"); the CurseForge username and contact email are simply typed into the form.
2. **GRIP's current version** — *re-checked 2026-08-07.* **v2.3.18** (SHA-256 `ec590cc0f78db732739d600578b2d9dbd1fd8564fcdf9a4fc54c3c75dfcbfac9`). `PlatformID`, `HelpURL` and `gse.tools` all return **zero** across its 204 Lua files, and it still reads `GSESequences` / `GSE.Library`. Three releases have shipped since v2.3.5 was analysed (v2.3.16, .17, .18) and nothing has been remediated in any of them. **Re-check before submitting** — this project ships often.
3. **Exhibit line numbers** — *resolved.* Verified against both v2.3.5 and v2.3.16. `Engine/StepFunctions.lua:248-262` and `Import/LegacyMigrate.lua:92-99` are identical in both. `Import/LegacyImport.lua` grew, so its GSE-legacy blanking moved from `857-872` to `921-927` — cite the v2.3.16 numbers if you quote the current build. Details in `exhibits/grip-vs-gse-forensic-comparison.md`, Appendix A.
4. **Real-name decision** — *resolved.* Operator identity is established (`evidence/OPERATOR-IDENTITY-RESOLVED.md`); no scrubbed zip is needed. These form fields still deliberately use only the CurseForge handle `sirsataana`, because that is the identifier CurseForge acts on — the legal name adds nothing to a platform report.
