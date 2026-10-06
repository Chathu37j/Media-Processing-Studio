# Media Processing Studio

A browser-based bulk media processing studio for images and videos.

## Features

- Bulk image upload
- Bulk video upload
- Image resize
- Video resize using FFmpeg WebAssembly
- Image enhancement (contrast/saturation, optional 2× smooth upscale)
- Video enhancement (contrast/sharpen via FFmpeg)
- AI background removal for images and videos (≤60 s, 10 fps, max 720 px)
- Output format (JPEG/PNG/WebP) and quality control
- Per-file download + ZIP export
- Video 2× Lanczos upscale
- Transparent / white / black background output
- ZIP export
- Responsive dark UI
- Runs primarily in the browser

## GitHub Pages Deployment

1. Create a new GitHub repository, for example:
   `media-processing-studio`
2. Make the repository **Public** if you want to use GitHub Pages on a free account.
3. Upload `index.html` to the repository root.
4. Go to:
   **Settings → Pages**
5. Under **Build and deployment**, choose:
   - Source: **Deploy from a branch**
   - Branch: **main**
   - Folder: **/ (root)**
6. Click **Save**.
7. Wait for GitHub Pages to deploy.
8. Your site will normally be available at:

   `https://YOUR-USERNAME.github.io/media-processing-studio/`

## Important

This project loads FFmpeg WebAssembly and the image background-removal model from external CDNs. Therefore the browser needs an internet connection when those resources are first loaded.

Large videos and AI processing can use significant RAM/CPU. Performance depends on the user's device and browser.

Video background removal extracts frames at 10 fps (max 720 px, 60 s), removes each background in the browser, then re-encodes with FFmpeg (MP4 for white/black, WebM VP9 alpha for transparent). It is slow and RAM-heavy. Upscaling is Lanczos smoothing, not AI super-resolution.

The JSZip script uses an SRI hash. The unpkg FFmpeg scripts are version-pinned but have no SRI hash yet; generate one with `curl -s URL | openssl dgst -sha384 -binary | openssl base64 -A`.

## Project Structure

```text
media-processing-studio/
├── .gitignore
├── index.html
└── README.md
```

## Local Testing

You can open `index.html` directly in many browsers, but some browser security restrictions can affect module/CDN loading.

For the most reliable local test, use a simple local web server.

Example with Python:

```bash
python -m http.server 8000
```

Then open:

`http://localhost:8000/`

## License

You can adapt this project for your own website or business. Check the licenses/terms of any third-party libraries and models loaded by the application before commercial redistribution.
