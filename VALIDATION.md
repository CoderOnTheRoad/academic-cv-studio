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
