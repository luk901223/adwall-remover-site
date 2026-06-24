# AdWall Remover

A lightweight browser extension that automatically removes anti-adblock overlays and restores page scrolling. No configuration needed — it just works.

## The Problem

Many websites detect ad blockers and display full-screen overlays demanding you disable your adblocker before accessing content. These walls block the page, disable scrolling, and interrupt your browsing experience.

## The Solution

AdWall Remover runs silently in the background and:

- **Detects** anti-adblock overlays using keyword matching and CSS pattern recognition
- **Removes** the overlay automatically, even if the site injects it dynamically
- **Restores scrolling** when a site locks the page behind the wall
- **Keeps watching** for walls that re-inject themselves after removal

## Features

- Zero configuration — install and forget
- Works on sites with randomized CSS class names
- Supports multiple languages (English, Polish, French, German, Spanish, Portuguese)
- No data collection, no tracking, no analytics
- No special browser permissions required
- Lightweight — single content script, no background processes

## Installation

### Firefox
Download from [Firefox Add-ons](#) or load manually:
1. Open `about:debugging` in Firefox
2. Click **This Firefox** → **Load Temporary Add-on**
3. Select the `manifest.json` file

### Chrome
Download from [Chrome Web Store](#) or load manually:
1. Open `chrome://extensions/`
2. Enable **Developer mode** (top right)
3. Click **Load unpacked** and select the extension folder

### Edge
Download from [Edge Add-ons](#) or load manually:
1. Open `edge://extensions/`
2. Enable **Developer mode** (left sidebar)
3. Click **Load unpacked** and select the Chrome extension folder

## How It Works

The extension injects a content script that:

1. Scans for known anti-adblock CSS selectors (class names, IDs)
2. Checks all fixed/absolute-positioned high-z-index elements for anti-adblock keywords
3. Removes matching overlays and unlocks scroll
4. Uses a MutationObserver to catch dynamically injected walls
5. Runs fallback checks at 0.5s, 1s, 2s, and 4s after page load

## Project Structure

```
├── manifest.json    # Extension manifest (v2 for Firefox, v3 for Chrome/Edge)
├── content.js       # Main content script
├── icon16.png       # Toolbar icon
├── icon32.png       # Windows taskbar icon
├── icon48.png       # Extensions page icon
└── icon128.png      # Store listing icon
```

## Privacy

AdWall Remover does not collect, store, or transmit any user data. It requires zero browser permissions. All processing happens locally in your browser.

## Contributing

Found a site where the extension doesn't work? Open an [issue](#) with the URL and a description of the anti-adblock wall. Pull requests are welcome.

## License

MIT License — see [LICENSE](LICENSE) for details.
