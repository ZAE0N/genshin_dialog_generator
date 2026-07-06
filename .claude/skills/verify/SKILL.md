---
name: verify
description: Drive the dialogue editor (index.html) in headless Chromium and capture screenshots to verify rendering, auto-layout, and PNG export.
---

# Verify: Genshin dialogue editor

The editor is a single static file (`index.html`) — no build, no server.

## Launch & drive (Playwright)

```bash
# scratchpad: npm install playwright (chromium is pre-installed, do NOT playwright install)
node - <<'EOF'
const { chromium } = require('playwright');
(async () => {
  const b = await chromium.launch({ executablePath: '/opt/pw-browsers/chromium-1194/chrome-linux/chrome' });
  const p = await b.newPage({ viewport: { width: 1440, height: 900 } });
  await p.goto('file:///home/user/genshin_dialog_generator/index.html');
  // drive: p.setInputFiles('#file', img), p.fill('#name'|'#subtitle'|'#text', ...),
  // p.click('#addChoice'), p.locator('#choices input').nth(i).fill(...),
  // p.locator('#scale').fill('1.6'), p.click('#save') + waitForEvent('download')
  await p.screenshot({ path: 'out.png' });
  await b.close();
})();
EOF
```

## Flows worth driving

1. Default state (no image) → placeholder canvas 1280×720 with hint text.
2. Upload landscape (1920×1080) → `#dims` shows "가로형", choices right-anchored ~52% width.
3. Upload portrait (832×1216) → "세로형", choices ~78% width, export PNG keeps original W×H
   (check IHDR bytes 16–24 of the download).
4. Long choice text → pill wraps to 2 lines and grows; stack grows upward.
5. Empty name+text → dialogue block and band hidden, choices still render.
6. Manual `\n` in 대사 → respected as line breaks.

## Gotchas

- Google Fonts link fails in the sandbox (ERR_CONNECTION_RESET) — expected; falls back to system sans.
- Wait ~1s after goto for the embedded asset images before screenshotting.
- Generate test PNGs with pure-python zlib writer (PIL not installed).
