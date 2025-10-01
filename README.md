# 🎬 MP4 → JPG Frame Extractor

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![No Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen.svg)](https://github.com/allarddewinter/mp4-to-jpg)
[![Privacy First](https://img.shields.io/badge/privacy-100%25%20local-blue.svg)](https://github.com/allarddewinter/mp4-to-jpg)

> **"And now for something completely different..."** — *The Ministry of Silly Frames™*

A modern, privacy-first, in-browser video frame extractor. Convert any HTML5-supported video into JPEG frames—**no uploads, no servers, 100% client-side**.

Perfect for creating image sequences from screen recordings to share with LLMs that don't support direct video input.

---

## 🎯 Why This Tool?

Initially created to solve a common workplace problem: **sharing screen recordings with AI assistants that only accept images**. Many enterprise LLMs don't support video input, so extracting key frames from recordings became essential for effective collaboration and troubleshooting.

### Use Cases

- 📹 **Screen recording → LLM input**: Extract frames from recordings for ChatGPT, Claude, or other image-only AI tools
- 🎓 **Tutorial creation**: Generate image sequences from video tutorials
- 🔍 **Video analysis**: Extract frames at specific timestamps for review
- 🎨 **Content creation**: Pull still frames from videos for presentations or documentation
- 🐛 **Bug reporting**: Capture specific moments from screen recordings

---

## ✨ Features

### 🔒 Privacy-First

- **100% client-side processing** — your videos never leave your device
- No uploads, no tracking, no servers
- Works completely offline (after initial page load)

### 🎛️ Flexible Extraction Modes

1. **Step Mode**: Extract every N seconds (e.g., every 0.5s)
2. **FPS Mode**: Extract at specific frame rate (e.g., 2 frames per second)
3. **Timestamp Mode**: Extract at exact timestamps (e.g., `0, 1.25, 5, 10.5`)

### 🎨 Full Control

- **Custom time range**: Extract from start to end or any segment
- **Quality settings**: Adjust JPEG quality (20%-100%)
- **Scale control**: Resize output (5%-400% of original)
- **Max frames limit**: Prevent browser memory issues (up to 5000 frames)

### 📦 Export Options

- **Individual downloads**: Each frame downloaded separately
- **Auto-download**: Automatically download frames as they're extracted
- **ZIP bundle**: Download all frames as a single ZIP file
- **Smart naming**: Files named with frame number and timestamp

### ⌨️ Modern UX

- **Drag & drop** file upload
- **Keyboard shortcuts**: E (extract), C (cancel), Z (zip), R (clear)
- **Progress tracking**: Visual progress bar with status updates
- **Responsive design**: Works on desktop and mobile
- **Dark mode support**: Automatic based on system preference
- **Gallery preview**: Thumbnail preview of all extracted frames

---

## 🚀 Quick Start

### Option 1: Use Online (Recommended)

Visit the live demo: **[https://allarddewinter.github.io/mp4-to-jpg/](https://allarddewinter.github.io/mp4-to-jpg/)**

### Option 2: Download & Use Offline

1. Download `index.html`
2. Open it in any modern browser
3. Start extracting frames!

### Option 3: Deploy Your Own

1. Fork this repository
2. Enable GitHub Pages in Settings → Pages
3. Set source to `main` branch, `/ (root)` directory
4. Your app will be live at `https://yourusername.github.io/mp4-to-jpg/`

---

## 📖 How to Use

### Basic Workflow

1. **Load Video**
   - Click "Choose File" or drag & drop a video onto the page
   - Supported formats: MP4, WebM, MOV, and any HTML5-compatible video

2. **Set Time Range** (Optional)
   - Specify start and end times in seconds
   - Or click "Use full duration" to extract from entire video

3. **Choose Extraction Mode**
   
   **Step Mode** (Every N seconds)
   - Set step interval (e.g., `0.5` for every half second)
   - Set max frames to prevent memory issues
   
   **FPS Mode** (Frames per second)
   - Set desired FPS (e.g., `2` means 2 frames every second)
   - Tool shows equivalent step interval
   
   **Timestamp Mode** (Specific times)
   - Enter comma or space-separated timestamps
   - Example: `0, 1.25, 2, 3.5, 10`

4. **Adjust Output Settings**
   - **Scale**: Resize images (100% = original size)
   - **Quality**: JPEG compression (92% recommended)
   - **Auto-download**: Enable to download each frame immediately

5. **Extract**
   - Click "Extract frames" or press `E`
   - Watch progress bar for status
   - Preview appears in gallery below

6. **Download**
   - Individual: Click "Download" on any thumbnail
   - Bulk: Click "Download all as ZIP" or press `Z`

### Keyboard Shortcuts

- `E` — Extract frames
- `C` — Cancel extraction
- `Z` — Download all as ZIP
- `R` — Clear results

---

## 🔧 Technical Details

### How It Works

1. **Video Loading**: HTML5 `<video>` element loads your file using object URLs
2. **Seeking**: JavaScript seeks to target timestamps
3. **Capture**: Each frame is drawn to a hidden `<canvas>` element
4. **Encoding**: Canvas converts to JPEG blob with specified quality
5. **Storage**: Blobs stored in memory for preview and download
6. **ZIP**: JSZip library (loaded on-demand from CDN) bundles files

### Browser Compatibility

- ✅ Chrome/Edge 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Opera 76+

### Limitations

- **Keyframe seeking**: MP4s often seek to nearest keyframe, not exact timestamp
- **Memory limits**: Extracting hundreds of high-res frames can use significant RAM
- **iOS restrictions**: Keep browser tab active during extraction
- **Format support**: Limited to browser-supported video codecs

### Performance Tips

- Use **Max frames** limit to prevent memory issues
- Lower **Scale %** for faster processing
- Reduce **Quality** for smaller file sizes
- Close other browser tabs when processing large videos

---

## 🎨 Monty Python Theme

This tool features a playful homage to Monty Python:

- ASCII art banner
- "Ministry of Silly Frames" branding
- Shrubbery references (because every good tool needs one)
- Clean, white background inspired by classic British comedy sketches

*No parrots were harmed in the making of this application.*

---

## 🔐 Security & Privacy

### Content Security Policy (CSP)

For maximum security, add this `<meta>` tag to `<head>`:

```html
<meta http-equiv="Content-Security-Policy"
      content="default-src 'self'; 
               img-src 'self' blob: data:; 
               media-src 'self' blob:; 
               script-src 'self' https://cdn.jsdelivr.net; 
               style-src 'self' 'unsafe-inline'; 
               object-src 'none'; 
               base-uri 'self'; 
               frame-ancestors 'none'">
```

### Self-Hosting JSZip

To avoid external CDN dependencies:

1. Download [`jszip.min.js`](https://github.com/Stuk/jszip/releases)
2. Place in same directory as index.html
3. Update script loader in JavaScript:
   ```javascript
   s.src='./jszip.min.js';  // Instead of CDN URL
   ```

---

## 🛠️ Troubleshooting

### Frames are blurry or wrong time

**Solution**: MP4 keyframe limitation. Try:
- Increasing step interval (use 1.0s instead of 0.1s)
- Using lower FPS setting
- Re-encoding video with more keyframes

### Extraction fails on iOS/Safari

**Solution**: 
- Keep browser tab in foreground
- Tap the video area first (user gesture requirement)
- Try smaller time ranges

### "Cannot create ZIP" error

**Solution**:
- Check internet connection (for CDN)
- Self-host JSZip (see Security section)
- Download frames individually instead

### Browser crashes or freezes

**Solution**:
- Reduce **Max frames** limit
- Lower **Scale %** setting
- Process video in smaller time segments
- Close unnecessary browser tabs

---

## 📚 FAQ

**Q: Where is my video uploaded?**  
A: Nowhere! Processing is 100% local in your browser.

**Q: What does "2 FPS" mean exactly?**  
A: Two frames per second = one frame every 0.5 seconds.

**Q: Why do some timestamps skip or snap?**  
A: MP4 compression uses keyframes. Browsers seek to the nearest keyframe, not exact timestamps.

**Q: Can I extract every single frame?**  
A: Technically yes (set FPS to video's native rate), but browser limitations make this unreliable for most MP4s.

**Q: Does this work offline?**  
A: Yes! After the initial page load. However, ZIP download requires internet connection unless you self-host JSZip.

**Q: What's the maximum video size?**  
A: Limited only by browser memory. Tested successfully with multi-GB files.

---

## 🤝 Contributing

Contributions welcome! This is a single-file HTML app, making it easy to fork and modify.

### Ideas for Enhancement

- WebAssembly video decoding for frame-perfect extraction
- WebP/PNG output format options
- Batch processing multiple videos
- Frame comparison/diff tools
- Custom watermarking

---

## 📄 License

MIT License - feel free to use, modify, and distribute.

---

## 🙏 Credits

**Created by**: [Allard de Winter](https://github.com/allarddewinter)

**Inspiration**: Built out of necessity to share screen recordings with workplace LLMs that didn't support video input.

**Special Thanks**:
- Monty Python for the silly inspiration
- The HTML5 video/canvas APIs
- JSZip library by Stuart Knightley

---

## 🔗 Links

- **Live Demo**: [https://allarddewinter.github.io/mp4-to-jpg/](https://allarddewinter.github.io/mp4-to-jpg/)
- **Repository**: [https://github.com/allarddewinter/mp4-to-jpg](https://github.com/allarddewinter/mp4-to-jpg)
- **Issues**: [Report bugs or request features](https://github.com/allarddewinter/mp4-to-jpg/issues)

---

<div align="center">

**"Bring us... a shrubbery!"** 🌳

Made with ♥️ and a healthy appreciation for silly walks

</div>
