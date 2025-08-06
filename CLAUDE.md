# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a local mirror of the Arizona Bankruptcy Law Firm website (www.arizonabk.com). The site is a static website that has been downloaded for offline viewing and modification.

## Development Commands

### Running the Local Server
```bash
node server.js
```
The server runs on http://localhost:8080

### Direct Browser Access
Simply open `index.html` in any web browser for quick viewing without a server.

## Architecture

### Project Structure
- **Main Entry Point**: `index.html` - The homepage of the website
- **Assets Directory**: `assets/` - Contains all static resources
  - `css/` - Compiled stylesheets
  - `js/` - JavaScript bundles
  - `images/` - Image assets
  - `fonts/` - Web fonts
- **Offline Copies**: Two directories containing offline website copies
  - `arizonabk-offline/` - Simple offline version
  - `arizonabk-offline-node/` - Node.js served offline version with full page structure
- **Utilities**:
  - `server.js` - Simple Node.js HTTP server for local development
  - `download-complete-site.py` - Python script for downloading and mirroring the website

### Key Technical Details

1. **Static Site**: This is a fully static website with no build process or compilation step required. All assets are pre-compiled and ready to serve.

2. **Server Implementation**: The `server.js` file implements a basic HTTP server using Node.js core modules (no dependencies) that serves static files with appropriate MIME types.

3. **Website Downloader**: The `download-complete-site.py` script:
   - Reads URLs from `arizonabk-sitemap.md`
   - Downloads pages with all their assets
   - Updates asset references to use local paths
   - Creates a complete offline mirror

4. **Page Structure**: The site follows a typical law firm website structure with:
   - Practice area pages (bankruptcy, estate planning)
   - Blog articles
   - Contact and intake forms
   - Attorney profile pages
   - Legal disclosures and disclaimers

### Important Considerations

- **No Build Process**: There are no npm scripts, webpack configs, or build tools. The site is ready to serve as-is.
- **Form Submissions**: Forms exist but won't function without a backend server.
- **External Dependencies**: The site preserves references to Google Fonts and analytics but these are optional for local development.
- **Asset References**: All internal asset references use relative paths for portability.