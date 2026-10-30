# First-version validation

- Reviewed the original DOCX content and PDF reference typography/layout.
- Identified Computer Modern in the Hong reference and bundled CMU regular, bold and italic fonts.
- Browser checks: personal CV loaded; created custom section; added and edited entry; reloaded page and verified saved entry; removed temporary test section.
- Verified section hiding excludes publications from preview, showing restores them, and moving sections updates order.
- Verified desktop (1440px), tablet (default browser) and mobile (390px) layouts.
- Generated PDF: 4 A4 pages, text selectable, embedded fonts, reviewed all four rendered pages.
- Generated editable DOCX: 61 paragraphs and three embedded font files; rendered and reviewed all three pages using bundled LibreOffice. Word pagination depends on the reader and can differ from PDF.
- Verified original citation review notes are excluded from exported files.
- JavaScript syntax check passed.

The initial CV preserves supplied content. Missing publication years/DOIs/pages and the mixed source citation are flagged in the editor. Journal metrics are unverified source values, excluded by default.

## Colour and photo update

- Confirmed existing saved CV loads with migrated style defaults and unchanged entries.
- Tested palette selection, heading bands, alignment, spacing, photo upload, shape/position/size controls, photo removal and style reset.
- Confirmed styling and photo survive reloading.
- Exported and visually reviewed all pages of PDF and DOCX with a photo and coloured headings, and without a photo.
- Verified embedded photo, accent colour, heading shading and complete publication/reference content in exports.
- Test avatar was used only in local testing, removed afterward, and is not included in website source.

## BibTeX publication import

- Parser checks: nested braces, quoted fields, concatenated strings, macros, comments, conference venues, corporate authors, surname-first names, accents, pages and DOI normalisation.
- Malformed, empty and non-BibTeX files fail without importing partial records. Untitled records are skipped with a warning. Imported values are treated as text.
- Duplicate checks cover DOI URLs, normalised titles and very similar long titles.
- Browser fixture: four entries yielded two new entries and two unselected duplicates (existing CV match and same-file repeat).
- Adding selected entries changed the live CV publication count from seven to nine; citation formatting and accented authors were preserved. Undo restored seven without touching existing entries.
- No publication-export rendering code changed; imported records use the same preview/PDF/Word citation formatter as manually entered publications.
- Run regression checks with `node tests/bibtex.test.cjs`.

## Scopus CSV import

- Inspected the supplied Scopus CSV header and mapped full author names, title, year, source title, volume, issue, article number, page start/end and DOI. No source-file instructions are executed.
- Parsed all 12 supplied rows, stripped Scopus author IDs from displayed names, preserved accented authors, and checked page ranges and article numbers. The user’s file is not committed or shipped with the website.
- Browser test of the supplied export: 12 entries, 7 likely duplicates, 5 new entries selected; adding yielded 12 CV publications, and undo restored the original 7.
- Regression checks cover BOM/CRLF, quoted commas and quotes, multiline fields, malformed/ragged CSV, duplicate headers, missing titles, full/initials-only authors, DOI normalisation, article numbers and escaped HTML content.
- Existing BibTeX tests remain passing. Run `node tests/scopus.test.cjs` and `node tests/bibtex.test.cjs`.

## Two-mode studio and templates

- Verified Simple/Advanced switches share content, persist on reload and hide advanced controls in Simple mode. Mobile at 390 px has no document horizontal overflow.
- Model regression checks cover presets, bounded settings, zero-valued crop positions, ordering, grouping, selected-field publication merges, shared-content application versions and completeness checks.
- Layout integration checks generate all four templates using bundled fonts and PDF libraries: Classic 4 pages, Oxford 4, Modern Researcher 3, Spectrum 4 for the original CV. PDF page counts equal preview operation counts; every publication title is present. Long-word and multi-page stress content stays within page bounds.
- Browser tests covered Scopus review with selected-field updates, preservation of unchecked fields, undo, history restore, application versions, dedicated project fields, rich subscripts, photo crop and black-and-white mode. Temporary test data and avatar are not shipped.
- Visually reviewed all four Spectrum PDF and Word pages with a photo, plus all three compact PDF pages and all four compact Word pages without a photo. Checked true Word subscript, hyperlinks and embedded photo. Word pagination differs from PDF as documented.
- Existing publication parser suites and JavaScript syntax checks pass.

## Journal name and metric styling

- Added independent journal/Nature Index/impact-factor colours and normal, bold, italic, underline and combination styles. Bundled matching CMU bold-italic for PDF and preview.
- New manual Nature Index checkbox and impact-factor text persist as entry strings, preserving backup compatibility. Original free-text journal metrics remain intact and optional.
- Regression checks verify custom-colour text operations, true bold-italic journal runs, Nature Index underline operations, impact-factor bold text, omission of blank/unchecked labels and monochrome overrides.
- Browser checks cover persistence after reload and PDF/Word download generation.
- Rendered and visually reviewed all four PDF pages and all four Word pages with coloured bold-italic journal names, underlined Nature Index and bold impact-factor labels; inspected Word run properties for exact formatting.

## Supplied default CV

- Preserved Sourav_Ghosh_CV_default.json byte-for-byte and generated initial CV data from its profile, settings and sections. Default initialization excludes historical snapshots; the original downloadable file retains them.
- Default restore keeps local application versions/history and saves the previous CV as a checkpoint. Browser test restored 14 publications, photo and styling; preview rendered five pages and restoration survived reload.
- Added regression check comparing initial data against the supplied JSON and validating both. Existing layout tests now use a stable fixture independent of evolving personal CV data. All parser/model/layout/default tests pass.

## Skills section

- Added a Skills section with skillset name, expertise and skill-type dropdowns, plus rich-text details in both modes. Existing and default CVs receive an empty section once; deleting it is respected. Original supplied JSON remains unchanged.
- Model checks cover idempotent section creation and user deletion. Layout regression checks verify all four skill fields in shared PDF/preview text operations.
- Browser check added a temporary skill, selected Advanced and Software & Tools, saved details and verified values after reload and in both downloads. No example skills are shipped as personal claims.

## Prefilled default skills

- Added six skills and descriptions supported by the supplied research profile, experience and interests. Categories are Research or Technical; expertise levels remain unselected.
- Updated the tracked default JSON and generated initial data together. Original supplied content remains available in Git history.
- Existing users receive missing defaults once, preserving custom descriptions, expertise levels, matching names and IDs. Checks verify no duplicate insertion or overwriting. Browser preview displays all six skills with their descriptions.
