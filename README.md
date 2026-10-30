# Sourav Ghosh · CV Studio

A personal academic CV editor, designed for GitHub Pages. No server, account, build step, or external CDN is needed. The initial CV is populated from Sourav's supplied Word document.

## Use

Serve this folder over HTTP (`python3 -m http.server 8000`) and open http://localhost:8000. Avoid opening index.html directly: PDF and Word exports fetch local fonts.

Edit sections and entries, add custom sections, change their order, and hide sections from exports. Changes save in this browser's local storage. PDF and editable DOCX exports are generated entirely in the browser with embedded Computer Modern Unicode fonts. Page counts can differ between formats because Word and the PDF generator use different layout engines.

Use **Backup** to download your current data, and **Restore a backup** to move it to another browser or device. Clearing site data removes browser edits. Initial data in data.js stays unchanged by browser edits. Review citation notes in the Publications editor; missing bibliographic details have not been invented. Optional journal metrics are copied from the original CV, not independently verified.

## Import publications from Google Scholar or Scopus

In a Publications section, click **Import publications** and upload a **Google Scholar BibTeX** export (`.bib`, `.bibtex` or `.txt`) or a **Scopus CSV** export (`.csv`), up to 2 MB / 1,000 publications. The importer reads common article and conference citation fields, converts BibTeX author names and common LaTeX accents, and previews entries before changing your CV.

Matching DOIs, matching titles and very similar long titles are flagged against all existing publication sections and earlier entries in the uploaded file. Likely duplicates start unselected. Review/edit fields, select entries and choose **Add selected**. Existing entries are never overwritten. **Undo this import** removes the latest imported batch during the current session; save a backup before leaving if you want a separate copy. Entries without titles are skipped with a file note; malformed files do not add anything. Missing fields remain flagged for review. No website scraping or external service is used.

You can import multiple exports one at a time. Unsupported complex LaTeX and bibliographic inheritance may need manual corrections in review. Scopus CSV columns are mapped by header, so column order can vary. Full author names are preferred and Scopus author IDs are removed from displayed names. Page ranges and article numbers are both supported. DOI, volume, issue, venue and publication year are preserved. Citation counts are not treated as journal metrics. UTF-8 and Windows-1252 CSV files are accepted. Quoted commas, quotes and line breaks are handled; malformed rows fail without adding partial records. RIS and PDF imports are not supported.

## Style & photo

Open **Style & photo** in the sidebar to choose six palettes or a custom accent, plain/underlined/banded headings, header alignment, spacing and text size. Upload an optional JPG or PNG photo (up to 10 MB); it is centre-cropped and resized locally. Choose circle/square, left/right placement and three sizes. Photos and style choices are saved with your browser data and JSON backups, and included in PDF/DOCX downloads. Old backups remain compatible. Reset styling preserves your content and photo; remove a photo separately.

## GitHub Pages

1. Create a repository and upload these files to its `main` branch.
2. Under Settings → Pages, select **GitHub Actions** as the source.
3. Run **Publish CV Studio** or push to main. The completed workflow provides the website URL.

GitHub Pages makes the website and its initial CV content public. Browser edits remain on the editing device and are not uploaded to GitHub. Anyone visiting gets their own browser-local copy; there is no shared editing account. Keep the repository private until you are ready for the included contact and reference details to be published.

## Design

Computer Modern typography follows the Hong reference, with a compact academic hierarchy, clear date alignment, numbered publications and highlighted name. Forms and controls are separate from the exported CV.

## Bundled dependencies

- docx (MIT): https://github.com/dolanmiu/docx
- pdf-lib (MIT): https://github.com/Hopding/pdf-lib
- @pdf-lib/fontkit (MIT): https://github.com/Hopding/fontkit
- Computer Modern Unicode fonts (SIL Open Font License): https://github.com/aaaakshat/cm-web-fonts

All assets are served locally. No analytics or external runtime requests.
