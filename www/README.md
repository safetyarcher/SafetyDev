# Static Home Page (www)

This directory contains the static home page that will be served at the root of safetyarcher.com.

## Files

- `index.html` - Main HTML file
- `styles.css` - Stylesheet for the home page
- `script.js` - JavaScript for interactive features

## Deployment

This static site should be deployed to serve the TLD (safetyarcher.com) through Cloudflare Pages or similar hosting.

### Cloudflare Pages Setup

1. Connect this repository to Cloudflare Pages
2. Set **Root directory** to `www`
3. No build command needed (static HTML/CSS/JS)
4. Set **Build output directory** to `/` (or leave empty)

## Local Development

Simply open `index.html` in a browser, or use a local server:

```bash
# Using Python
python -m http.server 8000

# Using Node.js http-server
npx http-server
```

Then navigate to `http://localhost:8000`
