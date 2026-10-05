# Media Processing Studio

A browser-based bulk media processing studio for images and videos.

## Features

- Bulk image upload
- Bulk video upload
- Image resize
- Video resize using FFmpeg WebAssembly
- Image enhancement controls
- AI background removal for images
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

The current version provides browser-based image background removal. Full AI video background removal and true AI video enhancement require additional frame-processing models and a video encoding pipeline.

## Project Structure

```text
media-processing-studio/
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
