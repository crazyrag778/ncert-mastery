# Agent Instructions for New PDF Reader Pages

## Goal
When adding a new chapter reader page, create a reader HTML file inside the chapter folder and make it load PDFs from that folder's own chapters directory.

## Project convention
- Each chapter folder under ncert-data/ should contain its own reader page.
- The current project uses index.html inside the chapter folder as the reader page.
- PDFs for that chapter should live in a chapters/ subfolder inside the same chapter folder.

## What to build
Create a page that:
- shows a PDF list or opens a PDF from the query string
- loads the selected PDF with PDF.js
- renders all pages in a scrollable viewer
- supports Previous/Next navigation based on the page currently visible in the viewer
- includes zoom controls
- includes a Download button for the current PDF

## Path rules
Use paths relative to the reader file's own folder.

Examples:
- Theme stylesheet: ../../stylesheets/w3css-color-pallete.css when the reader page is inside ncert-data/chap-folder/
- PDF source: chapters/filename.pdf when the reader page is in the same folder as chapters/

Do not hard-code paths that assume the file is at the repository root.

## Required behavior
- Read the selected PDF name from the query string, for example ?pdf=chapterfile.pdf
- Build the PDF URL as chapters/<selected-file>
- Keep the viewer in scroll mode by default
- Let Previous/Next move to the page currently in view rather than only the last rendered page
- Keep the page counter updated while the user scrolls

## Suggested structure
1. Create the chapter folder if it does not exist.
2. Create an index.html file in that folder.
3. Copy the structure from an existing reader page such as ncert-data/kech1dd/index.html.
4. Update the PDF list to include the chapter's PDFs.
5. Ensure the stylesheet, PDF.js script, and chapter PDF paths use folder-relative links.

## Verification checklist
Before finishing, confirm that:
- the page loads without broken stylesheet paths
- the PDF opens from chapters/ in that chapter folder
- Previous/Next works in sync with the visible page
- Download uses the currently selected PDF
