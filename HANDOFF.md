# Handoff — GSE vs GRIP-EMS package (for Timothy Luke)

Two uses for this file: (1) a **notes area you can add to** (bottom), and (2) a **prompt to paste into a fresh Claude Code / AI session** to continue the work (the fenced block below). Prepared by Larry Thiessen (ScaryLarryGames); the GSE-side claims are yours to take to counsel.

---

## Where to start (human)
1. **`START HERE.html`** — open in any browser. The whole chain of events + what GRIP is + the honest proven/not-proven section. Self-contained.
2. **`README.md`** — the map (Part A companion response / Part B IP case).
3. **`evidence/companion-app/COMPANION-APP-FIX.md`** — the one thing to actually fix on the Companion app.

---

## Paste-into-a-fresh-session prompt

```
I'm continuing work on a local git repo — an IP/copyright + defensive package. READ FIRST:
  - README.md (the map), then START HERE.html, then the files under exhibits/ and evidence/.
  (Two folders in the path literally begin with a backtick: "`Larry's Crap" and "`Admin Creators" — in bash, escape the backticks.)

WHAT THIS IS
A package prepared by Larry Thiessen ("ScaryLarryGames") for Timothy Luke (author of GSE — Gnome
Sequencer Enhanced). Two parts:
  PART A (defensive): rebuts a public "GSE Companion spies on / deletes your data" video + disclosure.
  PART B (offensive): the IP case — the competing addon GRIP-EMS (CurseForge 1489414, author
  "Sataana"/JesperLive) and its site LazyGrip.net clone & scrape GSE.

PART B — FACTS ESTABLISHED (do not re-derive or contradict; all line-cited in exhibits/):
1. GRIP is a FUNCTIONAL/DESIGN CLONE of GSE, not a source-code copy. GSE's signature "Priority" step
   function expands to a triangular pattern (N=3 => [1,1,2,1,2,3]); GRIP's output is byte-identical from
   different code. GRIP reads GSE's INTERNAL stored format (GSESequences/GSE.Library).
2. GRIP engineered a WORKAROUND around GSE's documented anti-scrape lock ("deny in-memory scraping by
   third-party addons") — reads GSE's raw SavedVariables when the runtime table is locked. Knowledge + intent.
3. GRIP STRIPS the owner-ID at three stages (addon import, LazyGrip "decode", LazyGrip "convert"):
   PlatformID (0 occurrences anywhere in GRIP), the gse.tools HelpURL, and the Ed25519 Checksum.
4. False marketing: GRIP advertises "holds on a failed cast" — not implemented; its engine advances every
   press (step = step % N + 1), like GSE.
DO NOT CLAIM: source-code copying; the AI-transpilation METHOD as established fact (it's an allegation for
   discovery — the shipped code can't prove method); DMCA §1201 anti-circumvention (SavedVars are plaintext
   on disk); that LazyGrip HOSTS a library of the sequences (checked — 0 matches; excluded).
§1202/CMI (PlatformID removal) is a SUPPORTING count — get an IP lawyer's read (exhibits/grip-1202-cmi-analysis.md).
Precedence: GSE ~2015-2016 (12-13 yrs prior art); PlatformID introduced 2026-04-25; cite GRIP v2.3.5 as operative.

PART A — FACTS ESTABLISHED (companion app):
- Examined the shipped GSE Companion 0.4.22 (app.asar SHA-256 27716e71...4cd6e1 = the discloser's own hashes.txt).
- "Deletes your data" is REFUTED: the delete ran only under `restricted && enforce`; the discloser's OWN
  captured `access-policy` shows "enforce": false on all three dates he recorded (2026-06-20/-06-21/-07-09);
  it never armed and is REMOVED from 0.4.22.
- "Paywall/EULA" and "surveils & bans" are MISFRAMED (addon is free; human moderation of a documented group).
- THE ONE REAL FIX: an UNSIGNED diagnostic upload (companion:request -> zo() -> /diagnostic/upload) that can
  gather WoW-folder files and is not ed25519-signed or enforce-gated. See evidence/companion-app/COMPANION-APP-FIX.md.
- TWO THINGS ONLY TIM CAN CONFIRM before Part A goes public: (a) `enforce` was never set true server-side;
  (b) the diagnostic upload was never used to pull a user's files. Tim is the server operator/author = the authority.

HONESTY RULES: never overclaim. The package's credibility depends on conceding what is NOT claimed. If the
code doesn't support it, say so.

SHARED EVIDENCE: the Discord record (evidence/discord/: THE-STORY.md, captures.md, message-screenshots/) is
shared with Larry's own repo "GRIP-IP-Complaint" — relevant to both cases. Timestamps are decoded from each
Discord message-ID snowflake (authoritative, timezone-independent).

OPERATOR IDENTITY (confirm before any filing): "Sataana"/sirsataana authors GRIP-EMS and runs LazyGrip.net;
his own publicly-linked accounts resolve to Jesper Driessen (GitHub JesperLive, etc.). LazyGrip.net registrant
is privacy-redacted (NameCheap).

STILL OPEN: confirm CurseForge project 1489414 ownership + WHOIS for lazygrip.net + real identities;
Tim to confirm the two Part A server-side facts and ship the COMPANION-APP-FIX.md change.

When done, commit to the repo (git add -A && commit) with a clear message. Do not push anywhere unless asked.

WHAT I WANT YOU TO ADD: <describe your change here>
```

---

## Notes / additions from Timothy (add anything here)

- _(empty — add corrections, extra evidence, dates, filing details, or the confirmations noted above)_
