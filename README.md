# AI Video · Cosmic Cards

เว็บโชว์การ์ด 5 ใบ แต่ละใบผูกกับคลิปวิดีโอของร้าน (dealer) แบบ tarot-style flip. เปิดการ์ดแล้วเล่นคลิปเต็มจอ มี progress bar / prev / next / replay / mute ครบ.

## Shops

| # | ชื่อร้าน | Arcana | Video | Photo |
|---|--------|--------|-------|-------|
| 01 | ร้านโก๋เคมีเกษตร | The Star | `ร้านโก๋การเกษตร.mp4` | `โก๋การเกษตร.png` |
| 02 | ร้านเฮงฮวดการเกษตร | The Moon | `ร้านเฮงฮวดการเกษตร Final (1).mp4` | `เฮงฮวด.png` |
| 03 | ร้านชัยพฤกษ์ ไดร์ฟทรู | The Sun | `ร้านชัยพฤกษ์ ไดร์ฟทรู Final (1).mp4` | `ชัยพฤกษ์เกษตร.png` |
| 04 | ร้านนำชัยเกษตร | The Tower | `ร้านนำชัยเกษตร จ.สุราษฎร์ธานี (Final).mp4` | `นำชัยเกษตร.png` |
| 05 | ร้าน ส.เอเชียเกษตรภัณฑ์ | The World | `ส.เอเชียเกษตรภัณฑ์ จ.สุราษฎร์ธานี (Final).mp4` | `ส.เอเชีย.png` |

## Files in this repo

- `Cosmic Cards - Videos.html` — main standalone page (open directly in a browser)
- `Cosmic Cards _Standalone_.html` — original template (no videos, for reference)
- `*.png` — shop photos shown on the card backs

## Videos are NOT committed

Each `.mp4` is 115–175 MB which exceeds GitHub's 100 MB per-file hard limit, so `*.mp4` is in `.gitignore`. To run the app end-to-end you need the clips next to the HTML file.

**Option A — place the files locally:** drop the 5 `.mp4` files (exact names per the table above) into the same folder as `Cosmic Cards - Videos.html`, then open the HTML.

**Option B — Git LFS:** if you want the clips in the repo, run:

```bash
git lfs install
git lfs track "*.mp4"
git add .gitattributes *.mp4
git commit -m "track videos with LFS"
git push
```

LFS uses the account's storage + bandwidth quota.

**Option C — external hosting:** upload the clips to a CDN / S3 / YouTube and edit the `SHOPS` array inside the HTML (`video:` field) to point to the hosted URLs.

## How it works

The HTML uses an inline bundler format: assets (fonts, template) live inside `<script type="__bundler/*">` tags. On load, JS extracts them and swaps the DOM to the real app. The `SHOPS` array controls everything — shop list, card count, videos, and photos. Find it inside the template and edit in place, or use the accompanying `patch.py` (in development) to regenerate.
