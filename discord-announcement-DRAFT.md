# Discord announcement — DRAFT (review with Tim before posting)

> Fits in one Discord message (under the 2,000-char limit). Two shorter variants below.
> ⚠️ Before posting: Tim should confirm (1) `enforce` was never set true, and (2) the diagnostic upload was never used. The evidence points that way, but he's the authority.

---

## Full version

**A quick, factual note on the recent GSE Companion video / "disclosure."**

You may have seen a claim that the GSE Companion app spies on you or deletes other addons' data. Here are the facts — and how to check them yourself.

**No one's data was deleted — there was never a switch to flip.** The author confirms the code in the video pointed at **a dead end that was never monitored, captured or logged**. There was no server-side `enforce` that could be set to true, and the "switch" on the page couldn't even be pressed. The discloser's own captures agree: `"enforce": false` on June 20, June 21 and July 9. It has since been removed entirely.

**The GSE addon is 100% free.** Full class sets are public and free on CurseForge — nothing is sold. A creator may *optionally* link their *own* Patreon for their *own* extras; the sets stay free.

**Nobody was auto-banned for using another addon.** Specific people were removed by admins for organising to scrape, convert, strip the ownership tag from, and redistribute creators' All-Rights-Reserved sequences.

**One fair point — already hardened.** The video did point at something real: a diagnostic path. Per the author it only ever uploaded `GSE.lua` and the Companion's own files, and every upload is now tied to a request *you* start. In **0.4.26**: error logs aren't collected at all, credentials are stripped from anything sent, and file requests notify you.

**Still to come:** signing each request individually — not done yet, and we'd rather say so than have you find out.

**Verify it yourself** (same bytes we all have):
```
certutil -hashfile "%LOCALAPPDATA%\Programs\gse-companion\resources\app.asar" SHA256
```
→ compare to the hash in the discloser's own `hashes.txt`.

Please **don't harass anyone** — not the creator of the video or anyone named. Check the facts and decide for yourself. Questions are welcome. 🙏

---

## Short version (~600 chars)

**Re: the GSE Companion video.** Quick facts: (1) **Nobody's data was deleted** — the "delete" code was behind a server switch that was OFF the whole time (it's in the discloser's *own* captures: `"enforce": false` on 3 dates), and it's since been removed. (2) **The addon is free** — full sets are public on CurseForge; nothing is sold. (3) There's one fair point — a diagnostic upload path — and **it's already been hardened** in 0.4.26: addon error logs are no longer collected at all, credentials are stripped from anything sent, reads are limited to GSE's own files, and file requests now notify you. Still to come: signing each request individually — saying so rather than overclaiming. Verify the build yourself if you like. Please don't harass anyone. Questions welcome.

---

## One-liner (for a pinned reply / quick response)

The "delete your data" claim is about code that never ran — the trigger flag was `false` on every date the discloser himself recorded (it's in his own repo), and it's been removed from the current build. The addon is free. The one diagnostic path that was a fair concern has been hardened in 0.4.26 — error logs no longer collected, credentials stripped, GSE-only reads, and file requests now notify you; per-request signing is still to come. Verify the hashes yourself.
