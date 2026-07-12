# Agent Instructions for New PDF Reader Pages

## Goal
When asked to generate a reader page for a specific book folder, inspect the existing reader implementation, derive chapter titles from the PDFs when possible, create the new reader page, and register the book in the catalog.

## Project convention
- Each book folder under ncert-data/ should contain its own reader page named read.html.
- The existing reader pages in this project are the reference implementation for UI and behavior.
- PDFs for that book should live in a chapters/ subfolder inside the same book folder.

## Required workflow
1. Review an existing reader page from another book, such as ncert-data/kech1dd/read.html, and copy its structure, styling, and interaction patterns.
2. Analyze the UI and functions of that reference page so the new page matches the project’s established experience.
3. Inspect the PDFs in the target folder and extract chapter names from their headings or titles when available.
4. Build the PDF list in the new reader using those chapter names, with the PDF filenames as the underlying data.
5. Create the new read.html inside the target book folder.
6. Update get-books.html so the new book appears in the catalog with the correct title, subject, class, and link.

## What to build
Create a page that:
- shows a PDF list or opens a PDF from the query string
- loads the selected PDF with PDF.js
- renders the pages in a viewer with clear navigation and zoom controls
- supports Previous/Next navigation based on the current page in view
- includes a Download button for the active PDF
- uses the same visual language and layout as the existing readers

## Path rules
Use paths relative to the reader file’s own folder.

Examples:
- Theme stylesheet: ../../stylesheets/w3css-color-pallete.css when the reader page is inside ncert-data/book-folder/
- PDF source: chapters/filename.pdf when the reader page is in the same folder as chapters/

Do not hard-code paths that assume the file is at the repository root.

## Required behavior
- Read the selected PDF name from the query string, for example ?pdf=chapterfile.pdf
- Build the PDF URL as chapters/<selected-file>
- Keep the viewer in scroll mode by default
- Let Previous/Next move to the page currently in view rather than only the last rendered page
- Keep the page counter updated while the user scrolls
- Preserve the same navigation, toolbar, and responsive behavior as the existing readers

## Suggested structure
1. Create the book folder if it does not exist.
2. Create read.html in that folder.
3. Copy the structure from an existing reader page such as ncert-data/kech1dd/read.html.
4. Populate the PDF list with the chapter PDFs and the chapter names inferred from the PDFs.
5. Update get-books.html so the new book is included in the catalog.
6. Ensure the stylesheet, PDF.js script, and chapter PDF paths use folder-relative links.

## Verification checklist
Before finishing, confirm that:
- the page loads without broken stylesheet paths
- the PDF opens from chapters/ in the book folder
- Previous/Next works in sync with the visible page
- Download uses the currently selected PDF
- the new book appears in get-books.html
