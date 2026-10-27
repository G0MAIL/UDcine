# UDcine — starter movie catalog

A responsive, static movie-discovery site for movies and TV series. Includes search, genre filters, details modal, watchlist, continue-watching list, and a local catalog manager with JSON import/export.

## Run locally
1. Unzip the package.
2. Open `index.html` in a modern browser. For best results, serve the folder using a local static server:
   - Python: `python -m http.server 8000`
   - Then open `http://localhost:8000`.
3. Use the navigation and search. Open a title to view its details/player.
4. Open the catalog manager with **Ctrl+Shift+A** (Windows/Linux) or **Cmd+Shift+A** (Mac). On mobile, use a desktop browser to manage the catalog, or temporarily add a visible admin button in the HTML.
5. Export the catalog JSON before clearing browser data.

## Free deployment: Cloudflare Pages
1. Create a GitHub repository and upload `index.html` (and this README).
2. In Cloudflare, go to Workers & Pages → Create → Pages → Connect to Git.
3. Select the repository. For a plain static site, leave build command blank and set output directory to `/` (or the repository root, depending on the setup screen).
4. Deploy. Every pushed commit can trigger a new deployment.
Alternative: drag-and-drop the folder in a static host that supports direct uploads.

## Supported video source formats
- YouTube watch links or `/embed/` links (converted to the privacy-enhanced `youtube-nocookie.com` embed).
- Vimeo links (converted to Vimeo's player embed).
- Direct HTTPS/HTTP `.mp4`, `.webm`, or `.ogv` URLs.
- Other HTTPS URLs containing `/embed/` (only use providers whose embed terms allow this).

Many streaming pages cannot be embedded because of their security headers or provider terms. This starter deliberately does not scrape sites, bypass paywalls/ads, or defeat DRM. It does not guarantee that a third-party source is ad-free.

## Important limitations
- **The admin is local-only, not secure authentication.** The catalog and watchlist are saved in this browser's `localStorage`; changes do not sync to visitors or other devices. JSON export/import is provided.
- To publish catalog changes to everyone, edit the `seed` array in `index.html` or export your JSON and manually update the seed data, then redeploy.
- A real multi-user admin needs a backend/database and authenticated access (e.g. Supabase/Firebase). Never put admin secrets in static HTML.
- Sample catalog entries are demonstrations. Verify the exact rights, attribution, regional availability, and embed permissions for every title before publishing. Poster images are illustrative remote images and require internet access.
- This project indexes/embeds third-party video sources; it does not host movie files.
