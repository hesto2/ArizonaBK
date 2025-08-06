# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a local mirror of the Arizona Bankruptcy Law Firm website (www.arizonabk.com). The site is a static website that has been downloaded for offline viewing and modification.

## Development Commands

### Viewing the Site
To view the website, open any of the HTML files in the `www.arizonabk.com/` directory in a web browser:
```bash
open www.arizonabk.com/index.html
```

For better local development experience with proper MIME types, you can use Python's built-in server:
```bash
cd www.arizonabk.com
python3 -m http.server 8080
```
Then visit http://localhost:8080

## Architecture

### Project Structure
- **Website Content**: `www.arizonabk.com/` - Contains the complete website structure
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