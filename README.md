# Sourav Ghosh · CV Studio

A personal academic CV editor, designed for GitHub Pages. No server, account, build step, or external CDN is needed. The initial CV uses Sourav's supplied `Sourav_Ghosh_CV_default.json`, including its current publications, photo and styling. The default JSON is kept in this repository and now includes seven skills drawn from the supplied CV.

## Use

Serve this folder over HTTP (`python3 -m http.server 8000`) and open http://localhost:8000. Avoid opening index.html directly: PDF and Word exports fetch local fonts.

Edit sections and entries, add custom sections, change their order, and hide sections from exports. Changes save in this browser's local storage. PDF and editable DOCX exports are generated entirely in the browser with embedded Computer Modern Unicode fonts. Page counts can differ between formats because Word and the PDF generator use different layout engines.

Use **Restore default CV** to return to the bundled default; current edits are saved as a history checkpoint first. Existing browser edits are preserved on website updates. **Download default JSON** provides the current default backup, including its saved history; default restoration preserves your current local history and application versions.

Use **Backup** to download your current data, and **Restore a backup** to move it to another browser or device. Clearing site data removes browser edits. Initial data in data.js stays unchanged by browser edits. Review citation notes in the Publications editor; missing bibliographic details have not been invented. Optional journal metrics are copied from the original CV, not independently verified.

## Page placement

In any section, tick **Start this section on a new page** to move its heading and content to a fresh page. Each entry also has **Keep this entry together**, which keeps its title, metadata, details and any publication contribution together when they fit on a page. Entries longer than one full page may still split. Controls work in both Simple and Advanced modes and are saved in backups. Preview/PDF use the same page rules; Word uses native page-break and keep-with-next properties and can paginate differently by reader. Empty or hidden sections do not create page breaks.

## Academic profile links

Under **Personal details → Academic & professional profiles**, enter ORCID, Google Scholar, GitHub and ResearchGate profile URLs. ORCID also accepts a hyphenated ID. Only valid HTTP(S) links appear. Text labels such as [Google Scholar] sit below personal details, with or without a photo. When a photo is present, matching clickable icons also appear directly underneath it. Icons respect the photo placement/size and black-and-white mode; text links follow the Links colour. Preview links open a new tab. PDF annotations and Word hyperlinks support both labels and icons. URLs are included in browser saves and backups; no account scraping or remote icon requests occur.

## Arrange mode

Click **Arrange mode** in the sidebar. Drag the ⠿ handles to reorder sections, choose a section, then drag its entries. Publication groups can also be reordered when grouping is enabled. Papers move within their group; edit Publication group to change a paper’s classification. Reordering papers switches their publication sort to Manual so exports follow the saved order.

Drop to save automatically; click **Done arranging** to return to editing and preview. Focus a handle and press ↑ or ↓ for keyboard ordering. Escape cancels an active drag. Existing arrow buttons remain available. A history checkpoint is saved before every changed arrangement. Arrange mode supports both Simple and Advanced controls.

## Import publications from Google Scholar or Scopus

In a Publications section, click **Import publications** and upload a **Google Scholar BibTeX** export (`.bib`, `.bibtex` or `.txt`) or a **Scopus CSV** export (`.csv`), up to 2 MB / 1,000 publications. The importer reads common article and conference citation fields, converts BibTeX author names and common LaTeX accents, and previews entries before changing your CV.

Matching DOIs, matching titles and very similar long titles are flagged against all existing publication sections and earlier entries in the uploaded file. Likely duplicates start unselected. Review/edit fields, select entries and choose **Add selected**. In Advanced mode, matched publications can update existing entries: review each changed field and select which values to apply. Existing nonempty fields start unchecked; missing fields start checked. **Undo this import** reverses additions and selected-field updates from the latest imported batch during the current session; save a backup before leaving if you want a separate copy. Entries without titles are skipped with a file note; malformed files do not add anything. Missing fields remain flagged for review. No website scraping or external service is used.

You can import multiple exports one at a time. Unsupported complex LaTeX and bibliographic inheritance may need manual corrections in review. Scopus CSV columns are mapped by header, so column order can vary. Full author names are preferred and Scopus author IDs are removed from displayed names. Page ranges and article numbers are both supported. DOI, volume, issue, venue and publication year are preserved. Citation counts are not treated as journal metrics. UTF-8 and Windows-1252 CSV files are accepted. Quoted commas, quotes and line breaks are handled; malformed rows fail without adding partial records. RIS and PDF imports are not supported.

## Style & photo

Choose **Body text alignment** in either mode: Left, Justified, Center or Right. It applies to descriptions and publication citations in the preview and PDF/Word downloads. Headings, header alignment, dates and metadata retain their own layout. Existing CVs remain left-aligned until changed.


Choose **Simple** for essential editing, templates, palettes, photos and downloads. Switch to **Advanced** for all styling and publication controls, application versions, completeness checks and history. Both modes edit the same saved CV.

Four templates retain Computer Modern typography: **Classic Hong**, **Oxford**, **Modern Researcher** and **Spectrum Academic**. Spectrum uses plum and teal, numbered section bands and a coloured page edge. Advanced controls include separate name/heading/link/divider colours, margins, line spacing, entry/section spacing, indentation and black-and-white print mode.

Upload an optional JPG or PNG photo (up to 10 MB); adjust zoom, crop position, border, shape, placement and size. The original upload remains local and the same crop is used in both downloads. Photos and styling are included in JSON backups. Old backups remain compatible.

The A4 preview and PDF share one measured layout, including page breaks and page numbers. Preview zoom changes only the screen view. Word is editable and preserves typography, colours, photos, links and scientific sub/superscripts, but its page breaks can differ by reader.

## Advanced tools

- Publication numbering or author-year format, own-name emphasis, sorting and type grouping.
- Every publication has an Authorship dropdown (First author / Equal-contributing first author / Co-author, or Not specified) and a My contribution text field. Both appear beneath the citation with a bold authorship label in preview, PDF and Word. The default CV includes the user-supplied roles and contribution descriptions; unspecified contribution text stays blank. Existing matching papers receive missing fields once, preserving manual edits.
- Each publication has a manual Nature Index checkbox and impact-factor text field. Advanced → Publications → Journal & metric appearance sets independent colours and normal, bold, italic or underline styles (including combinations) for journal names and both labels. These appear in the preview, PDF and Word. Black-and-white print mode overrides their colours; original free-text metrics remain separately optional.
- Rich text with bold, italic, links, bullets, subscripts and superscripts.
- Dedicated forms for teaching, grants, talks, awards, supervision, projects and skills, plus custom sections. Skills include a skillset name, expertise (Beginner / Intermediate / Advanced / Expert), type (Technical / Research / Software & Tools / Laboratory / Communication / Leadership / Other) and rich-text details. Seven user-supplied skills are provided by default; expertise levels supplied by Sourav are Expert for modelling, Advanced for machine learning, Intermediate for HPC, and Expert for data analysis/workflow automation. Existing Skills entries are preserved, matching names are skipped, and the defaults are added only once. Empty sections are excluded from downloads. You can add further Skills sections through Add a section.
- Named application versions save section visibility and styling while sharing current CV content. Up to 12 versions are stored.
- Completeness checks flag missing fields, malformed years/DOIs and likely duplicate publications for review.
- History keeps up to 10 checkpoints, including manual checkpoints and snapshots before significant changes. Restore creates a checkpoint of the current CV first.

Versions and history are browser-local and included in backups. Download backups for durable copies and transfers between devices.

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
