# MP4 → JPG (In‑Browser Frame Extractor) — *Ministry of Silly Frames™*

https://allarddewinter.github.io/mp4-to-jpg/

Convert an **MP4 (or any HTML5‑supported video)** into **multiple JPEG frames**, **entirely in your browser**.  
No uploads. No servers. Just a single static HTML file.

```
\|  /  |/ \_\_ \ / \_\_ \ / \_\_ \  \_    | |  \_\_\_  | |\_\_   \_\_\_   \_\_\_ | |\_
\| |/| | |  | | |  | | |  | |( )   | | / \_ \ | '\_ \ / \_ \ / \_ | **|
\| |  | | |**| | |**| | |**| |/ \_ \ | || (*) || |*) | (*) | (*) | |\_
|*|  |*|\_***/ \_***/ \_***/  (*)  |\_| \_**/ |*.**/ \_**/ \_\_\_/ \_*|
The Ministry of Silly Frames™ (bring a shrubbery)
````

---

## ✨ Features

- **Runs 100% locally**: your video never leaves your machine.
- **Three extraction modes**  
  - **Every N seconds (Step)**  
  - **By FPS** (e.g., `2 FPS → every 0.500 s`)  
  - **Specific timestamps** (`0, 1.25, 5`)
- **Output controls**: JPEG **quality** and **scale (%)**.
- **Download options**: per‑frame or **bundle all as ZIP**.
- **Modern UX**: drag‑and‑drop, keyboard shortcuts, responsive layout.
- **Minimalistic light UI** with Monty Python ASCII homage.

---

## 🖼 Demo

👉 **Live Demo on GitHub Pages**

---

## 🚀 Quick Start

1. **Download** this repo or `index.html`.
2. Open `index.html` in your browser.
3. Drop a video or select via file picker.
4. Choose mode (**Step**, **FPS**, or **Timestamps**).
5. Adjust **Scale** and **JPEG quality**.
6. Click **Extract frames** → download individually or as ZIP.

---

## 🌐 GitHub Pages Deployment

1. Push `index.html` to your `main` branch.
2. In **Settings → Pages**, set:
   - **Source**: `Deploy from branch`
   - **Branch**: `main` → `/ (root)`
3. Your app will be live at:  
   **`https://allarddewinter.github.io/mp4-to-jpg/`**

---

## 🔒 Security (CSP)

Add this `<meta>` tag in `<head>` for a strict Content Security Policy:

```html
<meta http-equiv="Content-Security-Policy"
      content="default-src 'self'; img-src 'self' blob: data:; media-src 'self' blob:; script-src 'self' https://cdn.jsdelivr.net; style-src 'self' 'unsafe-inline'; object-src 'none'; base-uri 'self'; frame-ancestors 'none'">
````

*   Remove `https://cdn.jsdelivr.net` if you self-host JSZip.
*   `img-src blob:` is required for previews and downloads.

***

## 🛠 Troubleshooting

*   **Seeks off?** MP4s often snap to keyframes → lower FPS or increase step.
*   **Blank frames on iOS?** Keep tab active; click **Extract** (user gesture required).
*   **ZIP fails offline?** Self-host `jszip.min.js`.

***

## 📦 Offline ZIP Support

*   Download `jszip.min.js` and include:
    
*   Remove CDN reference in the script loader.

***

## 🧭 FAQ

**Q: What does “2 FPS” mean?**\
A: Capture **two frames per second**, i.e., **every 0.500 s**.

**Q: Does this upload my video?**\
A: No. Everything runs locally in your browser.

***

## 📝 License

MIT License

***

## 🫡 Credits

*   UI homage inspired by **Monty Python** (ASCII banner & micro‑copy).

***
