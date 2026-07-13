# Discord announcement — DRAFT (review with Tim before posting)

> Fits in one Discord message (~1,750 chars). Two shorter variants below.
> ⚠️ Before posting: Tim should confirm (1) `enforce` was never set true, and (2) the diagnostic upload was never used. The evidence points that way, but he's the authority.

---

## Full version

**A quick, factual note on the recent GSE Companion video / "disclosure."**

You may have seen a claim that the GSE Companion app spies on you or deletes other addons' data. Here are the facts — and how to check them yourself.

**No one's data was deleted.** The "delete" code shown in the video was gated behind a server switch (`enforce`) that was **off** — the discloser's *own* evidence files show `"enforce": false` on June 20, June 21, **and** July 9. It never ran, and in the current build it has been **removed entirely**. It was a dormant safeguard that was never enabled.

**The GSE addon is 100% free.** Full class sets are public and free on CurseForge — no addon feature is sold. GSE.Tools takes no money; a creator can *optionally* link their *own* Patreon for their *own* extras, and the sets stay free.

**Nobody was auto-banned for using another addon.** Specific people were removed by admins for organizing to scrape, convert, strip the ownership tag from, and redistribute creators' All-Rights-Reserved sequences.

**One fair point — and we're already on it.** There's a diagnostic file-gathering path we're tightening: signing every request and limiting it to opt-in bug reports. Your privacy matters to us and we'd rather fix it than argue about it.

**Verify it yourself** (same bytes we all have):
```
certutil -hashfile "%LOCALAPPDATA%\Programs\gse-companion\resources\app.asar" SHA256
```
→ compare to the hash in the discloser's own `hashes.txt`.

Please **don't harass anyone** — not the creator of the video or anyone named. Check the facts and decide for yourself. Questions are welcome. 🙏

---

## Short version (~600 chars)

**Re: the GSE Companion video.** Quick facts: (1) **Nobody's data was deleted** — the "delete" code was behind a server switch that was OFF the whole time (it's in the discloser's *own* captures: `"enforce": false` on 3 dates), and it's since been removed. (2) **The addon is free** — full sets are public on CurseForge; nothing is sold. (3) There's one fair point — a diagnostic upload path — and **we're already tightening it** (signing + opt-in). Verify the build hash yourself if you like. Please don't harass anyone. Questions welcome.

---

## One-liner (for a pinned reply / quick response)

The "delete your data" claim is about code that never ran — the trigger flag was `false` on every date the discloser himself recorded (it's in his own repo), and it's been removed from the current build. The addon is free. We're tightening the one diagnostic path that was a fair concern. Verify the hashes yourself.
