# GSE Companion App — Forensic Findings

**Purpose:** independent verification of the claims in `JesperLive/gse-companion-disclosure` and the *TheKephas* video ("We Need to Talk About the GSE Addon Community"), checked against the **actual shipped GSE Companion 0.4.22 build**. Reproducible and hash-anchored. These are the receipts behind `RESPONSE-to-companion-disclosure.html` and `RESPONSE-brief-for-Tim.html`.

> **Two honesty caveats, up front.** (1) Two facts could only be confirmed by **the GSE author**, as server operator: that the access-policy `enforce` flag was never set true server-side, and what the diagnostic upload actually pulled. **Both are now answered on the record — see §1a below.** (2) This analysis was performed with AI assistance and revised as evidence arrived; treat it as a **strong, reproducible draft** — verify the hashes and the `enforce` captures yourself.

---

## 1a. The author's statement — the server-side facts, from the only person who has them

**Timothy Luke (GSE author and operator of `api.gse.tools`), Discord, 2026-07-29 10:30 PM, verbatim.** Source capture: [`claim-screenshots/11_tim-operator-statement.png`](claim-screenshots/11_tim-operator-statement.png) (2039×265, SHA-256 `87c4e8590b5406feee512ed188bc393bf0c2396ad1bbe105443540c0a0683a2a`, no metadata chunks). The transcription below was checked character-by-character against that image, typos and spacing included:

> IT went to a dead end that was never monitored, captured or logged.  The dead end wasnt even owned by me.  I have a total of zero data about anyone using grip.  There was no server enforce to be able to set to"true".  There was a webpage which had a "swtich" on it that loked like it did something but it was unable to be pressed.
>
> The diagnostic is something else entirely.  It uploaded GSE.lua and the the companion files.  thats it.   The function has been updated where a user could choose to upload other files at their discretion *(edited)*
>
> All the diag uploads have been tied to a user initiated request.

*(Quoted as written — typos, spacing and the client's "(edited)" marker included, per this package's no-paraphrase rule. The same statement is recorded in the `GRIP-IP-Complaint` package as `evidence/companion-app/OPERATOR-STATEMENT-2026-07-29.md`.)*

**Message identifiers (snowflake-decoded, authoritative).** The statement was sent as two messages in a Discord DM:

| Message ID | Decoded UTC | Content |
|---|---|---|
| `1532228792528015480` | **2026-07-30 03:30:11.573 UTC** | the main statement (shown `(edited)`) |
| `1532229212893741196` | **2026-07-30 03:31:51.796 UTC** | the closing line, 100 seconds later — *"All the diag uploads have been tied to a user initiated request."* |

Permalinks: [message 1](https://discord.com/channels/@me/788975881678618644/1532228792528015480) · [message 2](https://discord.com/channels/@me/788975881678618644/1532229212893741196)

Two notes on those, both deliberate:

- **The UTC date is 2026-07-30, not 07-29.** The capture shows `10:30 PM` in the author's local time, which decodes to 03:30 UTC the following day — consistent with UTC−5. This package treats snowflake-decoded UTC as authoritative for every other quote, so it does here too. The "2026-07-29" used in filenames and headings is the **local** date of the conversation; where the exact instant matters, cite the UTC above.
- **These are DM permalinks** (`/channels/@me/…`), so they resolve only for the two participants — a third party clicking them sees nothing. That is why the citable artifact is the hash-anchored capture, with the permalinks as corroboration for the parties rather than as public verification.

**Two further points in that statement, easy to miss and both material:**

| | |
|---|---|
| **The endpoint was not even his infrastructure** | *"The dead end wasnt even owned by me."* The code pointed at something outside the author's control, which is a stronger position again than "it pointed somewhere I never used." |
| **He holds no data on GRIP users at all** | *"I have a total of zero data about anyone using grip."* This answers the separate **"GSE surveils and bans GRIP users"** allegation directly, not merely the deletion claim — and it is the operator of the only server that could hold such data saying he has none. |

**Why this matters more than the `enforce: false` captures.** Those captures showed the flag was **false** on three dates. The author's statement is stronger: **there was no server-side `enforce` to set true at all.** The endpoint led to a dead end that was never monitored, captured or logged, and the on-screen "switch" could not even be pressed. So the destructive routine was not "armed and switched off" — **there was never a mechanism capable of arming it.**

**On the diagnostic — capability versus use, kept distinct.** §3 below establishes from the shipped 0.4.22 code what that path *could* reach. The author states what it *did*: it uploaded `GSE.lua` and the Companion's own files, and nothing else. These are not in conflict — a code path can have more reach than the server ever exercised, and **only the operator can speak to what was actually requested**, because that is a server-side fact no amount of client analysis can establish. The two claims should always be presented in that order and never merged.

**Additionally, per the author (2026-07-29):** *all* diagnostic uploads are now tied to a **user-initiated request**.

Record that precisely, because it is a statement about operational behaviour, not something the shipped client enforces. In the **0.4.26** bytes hashed above, the SSE handler for `companion:request` still calls the gather when the message carries a non-empty `kinds` array — i.e. the *client* will still respond to a server-sent request. So the correct statement is: **the operator states the server only issues these in response to a user-initiated report**, and/or the change post-dates 0.4.26. Do **not** claim the client rejects unsolicited requests, because in 0.4.26 it does not. Anyone can check that themselves, so claiming otherwise would be found out.

**Standing caveat, stated plainly.** This is the author's account. For server-side behaviour there is no independent way to verify it — no third party can audit a server they do not run — and this package does not pretend otherwise. What can be checked independently is everything else: the build hashes, the `enforce: false` captures the discloser published himself, and the client code.

---

---

## 0. Build identified — we examined the exact bytes the discloser did

| Artifact | SHA-256 | Match |
|---|---|---|
| Installed `app.asar` (`%LOCALAPPDATA%\Programs\gse-companion\resources\app.asar`) | `27716e71c29d9403e0e225cec97f03995a864bf3f4855024e255ec21454cd6e1` | = discloser's `hashes.txt` 0.4.22 entry, labelled "= the INSTALLED app.asar, verified 2026-07-09" |
| `GSE Companion Setup 0.4.22.exe` (installer) | `61015247508dc209ff3118cbd8842216ccd1c31c19dd94f9f80788c6ee1b665d` | = discloser's "GSE Companion Setup 0.4.22.exe" |

His hashes are honest and match reality — see `discloser-own-evidence/hashes.txt`. Because we're all looking at the same bytes, his own evidence can be used to check his own conclusions.

**Method:** extracted `app.asar` (Electron; 512 files); analyzed `out/main/index.js` (137,312 bytes; his hash `56598af5…`). Grepped and read the relevant code paths; decoded base64 string literals to defeat obfuscation. Line numbers below are into that `index.js`.

---

## 1. "GSE deletes your data" — code existed, **never executed** ❌

- The destructive cleanup ran only under **`restricted && enforce`**. `enforce` is served by `GET https://api.gse.tools/settings/access-policy`.
- The discloser captured that endpoint himself on **three dates** and committed the results (`discloser-own-evidence/live_access_policy_2026-06-20.json`, `-06-21.json`, `-07-09.json`):

  ```
  2026-06-20  → "enforce": false
  2026-06-21  → "enforce": false
  2026-07-09  → "enforce": false
  ```

  The arming flag was **off on every date he recorded.** The routine never ran against anyone.
- In the **current build (0.4.22)** the hardcoded cleanup is **removed**. `enforce` is fetched and only feeds the status UI (`index.js` ~650, ~3043, ~3058, ~3067–3068 `policy:state`). No `runAccountCleanup` exists.
- The GRIP-specific targeting shown in the video (base64 `GRIP-EMS.lua` / `GRIP_EMS_CHAR` / `provenanceSource` / `gse-legacy`) is **not present in 0.4.22** — confirmed absent as plaintext, as those base64 literals, and after decoding every base64 literal in the main process. Per the discloser's **own** timeline it lived in **0.4.12–0.4.14** (`evidence/app_asar_grip_region_0.4.14.js`) and was generalized/removed afterward.

**Conclusion:** "could delete" refers to code that was present in earlier builds; "**deleted your data**" **never occurred**. The discloser's own files show the trigger was off, and per the author (§1a) **there was no server-side `enforce` capable of being set true** — the path led to a dead end that was never monitored, captured or logged, and the visible "switch" could not be pressed. It functioned as a dormant canary (the GSE author's stated intent), and it is gone from the shipping build.

## 2. What the delete targeted, when it existed — narrow

Per the disclosed 0.4.14 code, it flagged only sequences tagged **`provenanceSource === "gse-legacy"`** (GRIP's *own* provenance tag) **or** whose name matched a GSE sequence — i.e., GSE-origin content that had been scraped, converted, and stripped of its ownership ID, sitting in a competitor's file. It did not target legitimate GRIP content.

## 3. What IS in 0.4.22 — the real, current capabilities

- **Signed directive engine (ed25519).** `qo()` verifies a `v2:`-prefixed signature vs. an embedded tweetnacl key (~1055). `Jo()`/`Po()` runs a plan **only if** signed, not expired, persona matches, and **WoW is closed** (~1514). Interpreter ops (`ds`, ~847–899): `listFiles / read / deleteKeys / setKey / write`, scoped to `Interface\AddOns` + `WTF` (`Io`, ~913). **Requires a server-pushed, ed25519-signed plan** — none observed in the captures.
- **`restrictedAccount` flag.** A server-supplied file-scan (`bo`/`fs`, ~811) sets a flag on the user's **own** GSE.Tools account record (`go`, ~661). Detection target is server-supplied.
- **⚠ UNSIGNED diagnostic upload — the real residual.** SSE `companion:request` (~1704) → `zo()` (~1455) gathers files **by kind** (incl. **BugGrabber/BugSack** via the `Ao` regex `/^!?Bug(Grabber|Sack)\.lua$/i`, ~911/997) **and** reads **server-specified paths** under `AddOns`/`WTF`, then POSTs their contents to `/diagnostic/upload` (~1479). This path is **not** ed25519-signed and **not** `enforce`-gated **in 0.4.22**. **No evidence of use** found in the captures.

  > **Status in 0.4.26 — scoped down, not removed (verified 2026-07-29).** Checked against the shipped `app.asar.original` (SHA-256 `c5e569a768acf03bfbe7fe8aa9a9d6a9c4a52f534fa913cc374f90534a57ac21`, version 0.4.26) and the current source. The endpoint still exists, but: `Ho()` executes `n.delete("errorlogs")` **before** gathering, so the BugGrabber/BugSack reader `Co()` is **unreachable from a server request**; `settings` is sent with `accessToken` and `userSession` deleted; the always-on portion is a **GSE-only mandatory gather** (`Po()`); it requires an authenticated session plus a freshly-refreshed bearer token; and a `requestFiles` flag now raises a user-visible desktop notification. **Still outstanding:** the per-request ed25519 signature recommended in `COMPANION-APP-FIX.md`. So the specific capability the disclosure showcased is gated off, and the arbitrary-path concern is materially reduced — but the path is not gone, and this document should not claim it is.
  >
  > **Hash-anchored (2026-07-29).** Extracted from a clean installer, not from a working tree: `GSE Companion Setup 0.4.26.exe` SHA-256 `c720ec821818fa2b58a4e50d71dbbd0c06c81c01ec573b5e2a4505554d0780d7` → `resources/app.asar` SHA-256 `c5e569a768acf03bfbe7fe8aa9a9d6a9c4a52f534fa913cc374f90534a57ac21` (6,210,073 bytes), `package.json` version `0.4.26`, `out/main/index.js` 136,744 bytes. Confirmed present in those shipped bytes: `.delete("errorlogs")`, `delete s.accessToken`, and the `/diagnostic/upload` endpoint.
  >
  > **Reachability vs presence — state this before anyone else does.** The error-log reader is **still in the binary**; a strings scan finds `/^!?Bug(Grabber|Sack)\.lua$/i` and `has("errorlogs")`. It is **unreachable from a server request** because the handler force-drops the `errorlogs` kind before gathering. Do not claim the code was deleted — claim, accurately, that it cannot be triggered, and point at `.delete("errorlogs")`.
- **User bug report.** `As()` (~2949) via `report:submit` (~2982) — user-initiated, honors `includeModList`.

## 4. GSE addon self-protection — legitimate, corroborated

The discloser accurately documents GSE's defensive features (see `discloser-own-evidence/hashes.txt`, and independently verified in the GSE addon source): ChaCha20 codec (`GSE/API/Codec.lua`), locked runtime namespace to deny in-memory scraping (`GSE/API/Plugins.lua`, `Storage.lua`), and ed25519 checksum verification (`GSE/API/Checksum.lua`). These protect GSE's All-Rights-Reserved content from the exact scraping at issue — they are defensive, not offensive.

---

## Verdict summary

| Claim (disclosure / video) | Verdict |
|---|---|
| "GSE Companion **deletes your data**" | **Did not happen** — `enforce=false` on all 3 of his own captures; cleanup removed in 0.4.22 |
| GRIP-targeting deletion routine | **Existed 0.4.12–0.4.14**; dormant (never armed); **removed** by 0.4.22 |
| "It's a **paywall / breaks the EULA**" | **Misframed** — addon 100% free; GSE.Tools takes no money; creators' own optional Patreon |
| "GSE **surveils & bans** GRIP users" | **Misframed** — human moderation of a documented scraping/redistribution group |
| Companion can **read/upload your files** | **Real capability** (unsigned path); no evidence of use; **should be fixed** (sign + opt-in) |
| 0.4.22 **BugGrabber/BugSack** collection | **Real**, via the server-triggered unsigned upload (not autonomous "always-on") |

## Reproduce

```
certutil -hashfile "%LOCALAPPDATA%\Programs\gse-companion\resources\app.asar" SHA256   (Windows)
sha256sum "$LOCALAPPDATA/Programs/gse-companion/resources/app.asar"                     (bash)
```
→ compare to `discloser-own-evidence/hashes.txt`. Then open the three `live_access_policy_*.json` and read the `enforce` value.

For the **0.4.26** claims, hash the installer and the asar inside it (no 7-Zip needed — Windows' bundled `tar` reads the payload):

```
certutil -hashfile "GSE Companion Setup 0.4.26.exe" SHA256
```
→ expect `c720ec821818fa2b58a4e50d71dbbd0c06c81c01ec573b5e2a4505554d0780d7`. The `resources/app.asar` extracted from it must hash to `c5e569a768acf03bfbe7fe8aa9a9d6a9c4a52f534fa913cc374f90534a57ac21` and be 6,210,073 bytes. Then search `out/main/index.js` for `.delete("errorlogs")` (the gate) and `/diagnostic/upload` (the endpoint that still exists).
