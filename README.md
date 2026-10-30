# Sourav Ghosh · CV Studio

A personal academic CV editor, designed for GitHub Pages. No server, account, build step, or external CDN is needed. The initial CV is populated from Sourav's supplied Word document.

## Use

Serve this folder over HTTP (`python3 -m http.server 8000`) and open http://localhost:8000. Avoid opening index.html directly: PDF and Word exports fetch local fonts.

Edit sections and entries, add custom sections, change their order, and hide sections from exports. Changes save in this browser's local storage. PDF and editable DOCX exports are generated entirely in the browser with embedded Computer Modern Unicode fonts. Page counts can differ between formats because Word and the PDF generator use different layout engines.

Use **Backup** to download your current data, and **Restore a backup** to move it to another browser or device. Clearing site data removes browser edits. Initial data in data.js stays unchanged by browser edits. Review citation notes in the Publications editor; missing bibliographic details have not been invented. Optional journal metrics are copied from the original CV, not independently verified.

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
