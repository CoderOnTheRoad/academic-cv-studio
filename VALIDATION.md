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

## HPC default refinement

- Updated HPC default to Administration & Support, Advanced expertise, and the user-supplied software installation, runtime troubleshooting and user-account administration responsibilities. Updated bundled JSON, initial CV and default skill model together. Untouched earlier HPC defaults migrate; customized entries are preserved.

## Combined modelling skill

- Combined the default DFT, electronic-structure and catalyst-modelling skills into First-Principles Modelling & Computational Materials Science; added Quantum ESPRESSO, VASP and Gaussian as supplied by the user. Four default skills remain. Untouched earlier entries combine automatically; customized entries are preserved.

## Arrange mode

- Browser-tested pointer dragging of sections and education entries, keyboard movement, restoration of original order, save/reload, and return to editing.
- Tested publication group reordering and its persistence, within-group entry ordering, and automatic switch from year sorting to Manual order. Shared layout checks confirm section and publication group order in export blocks.
- Mobile at 390 px has no document horizontal overflow; controls remain accessible in Simple mode. Mouse/pointer dragging is verified; touch handlers share the same pointer implementation.
- Reorder regression checks preserve untouched entries and reject unknown/duplicate IDs. Every changed drop creates a history checkpoint; unchanged/cancelled drags do not mutate CV data.

## Body text alignment

- Added Left, Justified, Center and Right controls in Simple and Advanced Style & photo. Settings persist after reload. Existing CVs default to Left.
- Shared PDF/SVG positioning checks confirm justification, centered/right offsets, unexpanded final lines and explicit line breaks; headings and date rows remain unaffected.
- Exported and inspected all five PDF and five Word pages with justification. Word stores justified paragraph properties and disables expansion of manually broken lines.

## User-supplied expertise levels

- Saved the supplied levels in default JSON, initial data and skill defaults: modelling Expert; machine learning Advanced; HPC Intermediate; scientific data analysis/workflow automation Expert. Other skill fields remain unchanged. Regression checks validate these four values.

## Authorship and contributions

- Read the user-supplied pasted message and attachment as bibliographic content. Added First author / Equal-contributing first author / Co-author dropdown and My contribution text for all publication forms, in both modes.
- Default CV has 14 roles (one first author, four equal-first authors, nine co-authors) and 13 supplied contribution descriptions. First-author Symmetry paper contribution remains blank. Matched by DOI with title fallback for older CVs; manual fields and subsequent blank edits are preserved.
- Browser verified the Comparative CO2 paper’s equal-first role and supplied contribution, edited and reloaded its contribution, then restored the supplied wording. Shared layout tests check bold labels and citation/contribution grouping; model tests cover default mapping and preservation.
- Rendered and visually reviewed all six PDF and all six Word pages. Authorship labels are bold and contribution text sits below the matching citation without clipping.

## Additional skills

- Added the approved Programming & Web Development, Database Management, and Scientific Writing & Productivity Tools descriptions to default JSON and model. Expertise remains unselected for these three. Existing CVs receive missing entries once, without replacing custom entries or duplicates; style reset retains migration markers.
