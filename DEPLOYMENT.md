# Deploying Slides to mehtaver.se

This document is for LLMs (Claude Code, etc.) deploying slide decks to Swapneel's personal website.

## Repository Structure

```
github-io-template/          # Source repo (git@github.com:SwapneelM/github-io-template.git)
  slides/                    # All slide decks live here
    images/                  # Shared image directory for slide assets
      extracted/             # Images extracted from PPTX/PDF sources
      real_talk_about_ai/    # Per-deck image subdirectories
      whatsapp/
    arbiter.html
    css-methods.html
    job-talk-2026.html
    ...
  _site/                     # Built site (SEPARATE git repo, pushes to swapneelm.github.io)
    slides/                  # Built copies of slides land here after jekyll build
```

## Step 1: Place the Slide Files

### For reveal.js HTML slides (self-contained)
```bash
# Copy the HTML file to slides/
cp /path/to/your-slides.html slides/your-slide-name.html

# If the slides reference local images (check with grep):
grep -o 'src="[^"]*"' slides/your-slide-name.html | grep -v http

# Copy referenced images to the correct relative path
# Most Jupyter-exported slides use images/extracted/
mkdir -p slides/images/extracted/
cp /path/to/images/* slides/images/extracted/

# For slides with their own image directory:
mkdir -p slides/images/your-slide-name/
cp /path/to/images/* slides/images/your-slide-name/
```

### For slides built with reveal.js CDN (hand-authored)
Same process. The HTML file must be self-contained or reference images via relative paths from `slides/`.

### Naming Convention
- Use lowercase kebab-case: `job-talk-2026.html`, `css-methods.html`
- Include year for dated talks: `dw-kenya-ai-products-2026.html`
- No spaces, no underscores in filenames

## Step 2: Test Locally (MANDATORY)

### 2a. Quick test with Python HTTP server
```python
import http.server, socketserver, threading, time, os
from playwright.sync_api import sync_playwright

os.chdir("/Users/swapneel/Documents/projects/github-io-template/slides")
handler = http.server.SimpleHTTPRequestHandler
httpd = socketserver.TCPServer(('127.0.0.1', 8900), handler)
t = threading.Thread(target=httpd.serve_forever, daemon=True)
t.start()
time.sleep(1)

with sync_playwright() as p:
    browser = p.chromium.launch(headless=True)
    page = browser.new_page(viewport={"width": 1280, "height": 720})
    page.goto("http://127.0.0.1:8900/your-slide-name.html", timeout=30000)
    time.sleep(8)  # Jupyter slides use RequireJS — needs extra load time

    # Check slide count
    slide_count = page.evaluate("document.querySelectorAll('.slides > section').length")
    print(f"Slides found: {slide_count}")

    # Check for broken images
    broken = page.evaluate("""() => {
        const imgs = document.querySelectorAll('img');
        return Array.from(imgs).filter(i => !i.complete || i.naturalHeight === 0).map(i => i.src);
    }""")
    if broken:
        print(f"BROKEN IMAGES: {broken}")
    else:
        print("All images OK")

    # Screenshot first few slides for visual verification
    for i in range(min(5, slide_count)):
        page.screenshot(path=f"/tmp/slide-test-{i+1}.png")
        page.keyboard.press("ArrowRight")
        time.sleep(0.5)

    browser.close()
httpd.shutdown()
```

### 2b. What to verify
1. **Slide count** matches expected number
2. **No broken images** (all return 200, naturalHeight > 0)
3. **Visual check**: open screenshots and verify text renders, images display, layout is correct
4. **Navigation works**: arrow keys advance slides
5. **YouTube embeds** (if any): require HTTP origin, will not load from file:// protocol

### 2c. Common issues
- **Reveal.js not loading**: Jupyter slides use RequireJS async loading. `Reveal` won't be on `window` — use `document.querySelectorAll('.slides > section').length` instead of `Reveal.getTotalSlides()`
- **Images 404**: Check that image paths in HTML match the directory structure under `slides/`
- **Blank slides**: The CDN (unpkg.com) may be slow. Wait 8-10 seconds before testing

## Step 3: Build the Jekyll Site

```bash
cd /Users/swapneel/Documents/projects/github-io-template

# Ruby path (required on this machine)
export PATH="/opt/homebrew/Cellar/ruby/4.0.2/bin:$PATH"

# Production build
JEKYLL_ENV=production bundle exec jekyll build
```

This copies everything from `slides/` into `_site/slides/`. Verify:
```bash
ls _site/slides/your-slide-name.html
```

## Step 4: Deploy from _site/

**CRITICAL: The `_site/` directory is a SEPARATE git repo** that pushes to `git@github.com:SwapneelM/swapneelm.github.io.git`. This is the live site.

```bash
cd _site

# Stage only the new slide files (be specific, don't add unrelated changes)
git add slides/your-slide-name.html slides/images/your-images/

# Commit with descriptive message
git commit -m "Deploy: add <slide-name> (<brief description>)"

# Push to live site
git push origin master
```

The site is live at: `https://mehtaver.se/slides/your-slide-name.html`

## Step 5: Commit Source Files

After deploying, also commit the source files to the template repo:

```bash
cd /Users/swapneel/Documents/projects/github-io-template

git add slides/your-slide-name.html slides/images/your-images/
git commit -m "Add <slide-name>: <brief description>"
git push origin master
```

## Step 6: Verify Live Site

```python
# After push, wait ~30 seconds for GitHub Pages to update, then verify:
from playwright.sync_api import sync_playwright
import time

with sync_playwright() as p:
    browser = p.chromium.launch(headless=True)
    page = browser.new_page(viewport={"width": 1280, "height": 720})
    page.goto("https://mehtaver.se/slides/your-slide-name.html", timeout=30000)
    time.sleep(10)
    slide_count = page.evaluate("document.querySelectorAll('.slides > section').length")
    print(f"Live slides: {slide_count}")
    page.screenshot(path="/tmp/live-slide-test.png")
    browser.close()
```

## Currently Published Slides

| File | Talk | URL |
|------|------|-----|
| `arbiter.html` | Arbiter overview | mehtaver.se/slides/arbiter.html |
| `css-methods.html` | CSS Methods (NYU CSMAP) | mehtaver.se/slides/css-methods.html |
| `djsce-tech-reboot-2026.html` | DJSCE Tech Reboot 2026 | mehtaver.se/slides/djsce-tech-reboot-2026.html |
| `dw-kenya-ai-products-2026.html` | DW Kenya AI Products 2026 | mehtaver.se/slides/dw-kenya-ai-products-2026.html |
| `nyu-csmap-arbiter-2026.html` | NYU CSMAP Arbiter 2026 | mehtaver.se/slides/nyu-csmap-arbiter-2026.html |
| `real_talk_about_ai.html` | Real Talk About AI | mehtaver.se/slides/real_talk_about_ai.html |
| `job-talk-2026.html` | Job Talk: Curbing Strategic Deception | mehtaver.se/slides/job-talk-2026.html |

## Gotchas

1. **Never `git add -A` in `_site/`** unless you intend to deploy ALL pending changes. Be specific with `git add`.
2. **Two separate git repos**: `github-io-template` (source) and `_site/` (deploy target, swapneelm.github.io).
3. **Jekyll build is required** before deploying. Raw files in `slides/` are not served — only `_site/slides/` is.
4. **Do NOT rely on GitHub Actions** for deployment. The CI workflow may fail. Always deploy manually.
5. **Image paths are relative** from the HTML file. A slide at `slides/foo.html` referencing `images/bar.png` resolves to `slides/images/bar.png`.
6. **Large image directories**: if a slide deck has 50+ images, verify they all copied to `_site/` after build.
