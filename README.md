# TGSL Search Lens

**The Greco Search Lens**

A dependency-free, local-first advanced search workbench for Google and YouTube. Build precise searches with Google search operators, time windows, YouTube filters, and a live preview of the final query and URL.

TGSL Search Lens is a **Single-File Local Application (SFLA)**. It runs from one HTML file without an application server, installation, API key, account connection, framework, or third-party JavaScript dependencies.

> **Compose the search locally. Explore the results on Google or YouTube.**

![TGSL Search Lens screenshot](screenshot.jpg)

## Run TGSL Search Lens

**[▶ Run TGSL Search Lens in your browser](https://mikejamesgreco.github.io/tgsl-search-lens/)**

For offline use, download or clone the repository and open `tgsl-search-lens.html` directly in a modern browser. No build process is needed.

The GitHub Pages link will work once the repository exists and GitHub Pages is enabled for the repository's root directory.

---

## Why TGSL Search Lens?

Google offers a powerful set of search operators, but many are less visible than the standard search box. YouTube has its own filters, and the two search engines interpret query operators differently.

TGSL Search Lens makes those controls approachable without requiring users to memorize syntax. It shows the generated search and destination URL before opening the results in a separate tab.

## Three Search Modes

| Mode | Best for | How it searches |
| --- | --- | --- |
| **Google Search** | Websites, documentation, PDFs, exact phrases, title or URL targeting | Builds a Google search query using supported operators and refinements |
| **Google → YouTube** | Finding YouTube watch pages, Shorts, playlists, and older indexed videos | Uses Google with YouTube-specific site and URL restrictions |
| **YouTube Direct** | Videos, channels, playlists, duration and video-feature filters | Builds a YouTube search URL and optional native filter parameters |

Google → YouTube is **not** the same as YouTube Direct: Google searches its index of YouTube pages, while YouTube Direct searches on the YouTube website. They may return different results.

## Features

### Google search operators

- Ordinary search terms, exact phrases, alternative terms (`OR`), and exclusions (`-`).
- Domain and website restrictions with `site:`; excluded sites with `-site:`.
- Search within titles and URLs with operators such as `intitle:`, `inurl:`, and `intext:`.
- File targeting with `filetype:`.
- Search date restrictions with `after:` and `before:`.
- Additional refinements for language, numeric ranges, and selected page types.
- An optional raw-query field for advanced users who want to enter their own syntax.

### YouTube native search

- Video, channel, playlist, and movie content-type selection.
- Video duration filters and supported relative upload periods.
- Relevance or popularity sorting.
- Feature filters, including HD, captions, Creative Commons, live, 4K, 360°, HDR, VR180, 3D, and location-tagged videos.

**Note:** The native YouTube URL-filter encoding used by this application is not a documented, stable public API. YouTube may change or ignore some of these parameters. Exact custom upload-date filtering is not guaranteed in YouTube Direct.

### Search workflow

- **Live query preview:** inspect the exact search expression that will be submitted.
- **Generated URL:** inspect and copy the search destination.
- **Operator Atlas:** browse operators and load example searches into the workbench.
- **Quick-start recipes:** load example searches for older YouTube videos, technical PDFs, tutorials, and channels.
- **Saved searches:** keep useful combinations in browser local storage when available.
- **Share workbench setup:** copy a link that restores the search controls when the page is hosted online.
- **Keyboard shortcut:** Ctrl/Cmd + Enter opens the current search.

## Getting Started

1. Open the [hosted app](https://mikejamesgreco.github.io/tgsl-search-lens/) or open `tgsl-search-lens.html` locally.
2. Choose **Google Search**, **Google → YouTube**, or **YouTube Direct**.
3. Enter your search terms or select a quick-start recipe.
4. Add optional operators, date restrictions, or video filters.
5. Inspect the query in **Live search preview**, then click **Search**.

The search results open on Google or YouTube in a new tab.

## Example Searches

| Goal | Query example | Suggested mode |
| --- | --- | --- |
| Find technical PDFs | `wiring diagram filetype:pdf` | Google Search |
| Find pages mentioning an exact phrase | `"Ford 300 inline six"` | Google Search |
| Find video watch pages on a topic | `site:youtube.com/watch "engine rebuild"` | Google → YouTube |
| Find older indexed videos | `site:youtube.com/watch carburetor rebuild before:2020-01-01` | Google → YouTube |
| Find long videos with captions | Enter the topic, choose **Over 20 minutes**, and select **Subtitles / captions** | YouTube Direct |

Search operators and indexing are controlled by Google or YouTube, and actual matching can be imperfect. In particular, Google document dates do not establish a video's exact upload date.

## Architecture

```text
┌───────────────────────────────────────┐
│           Your web browser            │
│                                       │
│   tgsl-search-lens.html               │
│          │                            │
│          ├─► Search controls          │
│          ├─► Query / URL generation   │
│          ├─► Operator Atlas           │
│          └─► Saved search settings    │
│                                       │
└───────────────────┬───────────────────┘
                    │ Click Search
                    ▼
        Google Search / YouTube
         (results in new tab)
```

TGSL does not embed or scrape search results. Search terms are transmitted to the selected search engine **when you launch the search**. A copied URL or shared workbench link may also expose the search terms to whoever receives the link.

Saved searches use the browser's local storage, if available. Browser privacy settings, moving between local files and hosted URLs, or clearing browser storage can affect saved-search availability. There is no TGSL cloud account or backend database.

## Repository Structure

```text
tgsl-search-lens/
├── index.html             # GitHub Pages launcher
├── tgsl-search-lens.html  # Complete standalone application
├── screenshot.jpg         # Screenshot (add manually)
└── README.md              # Documentation
```

The `screenshot.jpg` file is intentionally referenced but not included. Add a screenshot with that exact filename to the repository root to display it in this README.

## Single-File Local Application (SFLA)

The main application is self-contained in `tgsl-search-lens.html`. Its HTML, CSS, and JavaScript are embedded in that file. The repository's other files are for documentation and GitHub Pages convenience, not required to run the application locally.

The application version is maintained in a single `APP_VERSION` JavaScript constant inside the HTML and is intentionally not displayed in the interface.

## Browser Support

Designed for current browsers including Microsoft Edge, Google Chrome, and other modern Chromium-based browsers. The application also uses standard browser features such as URL encoding, tabs, and local storage; behavior may vary with browser policies and privacy settings.

## Documentation / References

- [Google: Refine web searches](https://support.google.com/websearch/answer/2466433)
- [Google: Advanced Search](https://support.google.com/websearch/answer/35890)
- [YouTube: Advanced search filters](https://support.google.com/youtube/answer/111997)

TGSL is an independent utility, not affiliated with or endorsed by Google or YouTube.

## Author

**Michael J. Greco**

TGSL Search Lens — **The Greco Search Lens**

© 2026 [mikejamesgreco.me](https://mikejamesgreco.me) LLC. All rights reserved.
