# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a local mirror of the Arizona Bankruptcy Law Firm website (www.arizonabk.com). The site is a static website that has been downloaded for offline viewing and modification.

## Development Commands

### Viewing the Site
To view the website, open any of the HTML files in a web browser:
```bash
open index.html
```

For better local development experience with proper MIME types, you can use Python's built-in server:
```bash
python3 -m http.server 8080
```
Then visit http://localhost:8080

## Architecture

### Project Structure
- **Website Content**: Now in root directory (moved from `www.arizonabk.com/` for GitHub Pages)
  - Main pages in subdirectories with `index.html` files
  - Each section (bankruptcy, blog, estate-planning, etc.) is self-contained
- **Assets Directory**: `assets/` - Contains global static resources
  - `css/` - Minified stylesheets (main bundle and supplementary CSS)
  - `js/` - JavaScript bundles
  - `images/` - Shared image assets
  - `fonts/` - Web fonts directory (currently empty, fonts loaded from Google Fonts)

### Content Organization
The site is organized into logical sections:
- **Practice Areas**:
  - `bankruptcy/` - Chapter 7 and Chapter 13 bankruptcy information
  - `estate-planning-asset-protection/` - Wills, POA, and advanced directives
- **Resources**:
  - `blog/` - Legal articles and FAQs
  - `videos/` - Video content page
  - `testimonials/` - Client testimonials
- **Legal Forms & Intake**:
  - `new-client-intake-form/` - General client intake
  - `estate-planning-intake/` - Estate planning specific intake
- **Disclosures & Legal**:
  - `chapter-7-disclosures/` and `chapter-13-disclosures/` - Required legal disclosures
  - `disclaimer/` - Site disclaimer

### Key Technical Details

1. **Static Site**: This is a fully static website with no build process required. All assets are pre-compiled and minified.

2. **External Dependencies**: The site uses:
   - Google Fonts (Alegreya and Source Sans Pro)
   - Cloudinary CDN for some images
   - Google Maps API for location display
   - Schema.org structured data for SEO

3. **Asset Loading**: The site uses performance optimizations including:
   - Preconnect hints for external domains
   - Font preloading with print media trick for non-blocking load
   - Minified and bundled CSS/JS assets

### Important Considerations

- **No Build Process**: There are no npm scripts, webpack configs, or build tools. The site is ready to serve as-is.
- **Form Submissions**: Forms exist but won't function without a backend server.
- **External Dependencies**: The site preserves references to Google Fonts and Cloudinary CDN but will work offline for basic viewing.
- **URL Structure**: Each page uses directory-based URLs with `index.html` files for clean URLs when served by a web server.

## GitHub Pages Deployment

This site is deployed on GitHub Pages at: https://hesto2.github.io/ArizonaBK/

### Critical Asset Path Configuration

**IMPORTANT**: GitHub Pages serves this site from a subdirectory (`/ArizonaBK/`), not the root domain. This affects how asset paths must be configured:

#### Correct Asset Paths for GitHub Pages:
- ✅ **Use**: `/ArizonaBK/assets/images/filename`
- ❌ **Don't use**: `/assets/images/filename` (will 404 on GitHub Pages)
- ❌ **Don't use**: `assets/images/filename` (breaks in subdirectories)

#### Local Assets Referenced:
All local image assets are stored in `/assets/images/` and include:
- `favicon-ffbed04d` - Site favicon
- `header-f56f7294` - Header logo image
- `mobile_logo-c4202588` - Mobile version of logo
- Additional hero/background images

#### Path Resolution Examples:
- **Root page** (`/index.html`):
  - `/ArizonaBK/assets/images/header.png` → Resolves correctly
- **Subdirectory page** (`/blog/article/index.html`):
  - `/ArizonaBK/assets/images/header.png` → Resolves correctly
  - `assets/images/header.png` → Would fail (resolves to `/blog/article/assets/...`)

#### When Making Changes:
1. Always use absolute paths with the GitHub Pages subdirectory prefix
2. Test asset loading on both root and nested pages
3. Verify paths work both locally and on the deployed GitHub Pages site
4. Remember that GitHub Pages URL structure is: `https://[username].github.io/[repository-name]/`

### Repository Information
- **GitHub Repository**: https://github.com/hesto2/ArizonaBK
- **GitHub Pages URL**: https://hesto2.github.io/ArizonaBK/
- **Deployment Branch**: main
- **Deployment Path**: / (root of repository)