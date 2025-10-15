# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file web application for CSV format conversion, specifically designed for bank statement exports. The entire application is contained in `csvconverter.html` - a standalone HTML file with embedded CSS and JavaScript.

## Architecture

**Single-Page Application Structure:**
- Self-contained HTML file with no external dependencies
- Pure vanilla JavaScript (no frameworks)
- Client-side only - all processing happens in the browser
- No build process or compilation required

**Core Functionality:**
The application provides CSV file format conversion with:
- File upload via click or drag-and-drop
- Configurable input delimiter detection (comma, semicolon (default), tab, pipe)
- Column mapping UI to map CSV columns to fixed structure (Date, Empfänger, Sum)
- 8-column output format with empty placeholder columns for Excel formulas
- Column reordering with up/down buttons
- Automatic date sorting (earliest to latest)
- Copy-to-clipboard functionality for direct paste into Excel
- Live preview of all transformed data
- Delete data button to reset and start over
- Format options lock after file upload

**Data Flow:**
1. File upload → `handleFile()` → FileReader API
2. Text parsing → `parseCSV()` → converts to array of objects
3. Column mapping → `transformData()` → creates fixed 8-column structure
4. Date sorting → `parseDate()` → sorts by date (earliest to latest)
5. Column reordering → `moveColumn()` → custom column arrangement
6. Preview rendering → `updatePreview()` → populates HTML table with all rows
7. Export → Copy to clipboard (tab-separated) or download (CSV)

**Key Implementation Details:**
- CSV parsing uses string split operations with configurable delimiters
- Data stored in global variables: `csvData`, `headers`, `transformedData`, `columnOrder`
- Fixed output structure: Col1, Col2, Date, Col4, Empfänger, Col6, Col7, Sum
- Date parsing supports European formats (DD.MM.YYYY, DD/MM/YYYY) and ISO
- Proper CSV escaping: values containing delimiters or quotes are quoted and escaped
- File download uses Blob API with data URLs
- Clipboard API for Excel paste functionality
- LocalStorage not used (stateless application)

## Development

Since this is a single HTML file with no build process:

**Running/Testing:**
- Open `csvconverter.html` directly in a web browser
- Or serve via local HTTP server: `python3 -m http.server 8000`

**Making Changes:**
- Edit the HTML file directly
- Refresh browser to see changes
- CSS is in `<style>` block at the top
- JavaScript is in `<script>` block at the bottom

**Code Organization:**
- Styles: CSS block with all styling
- HTML structure: Body with upload, options, mapping, column order, and preview sections
- JavaScript logic:
  - Global variables and DOM references
  - Event listeners (upload, drag-drop, mapping changes, buttons)
  - File handling: `handleFile()`, `parseCSV()`
  - Column management: `populateColumnOrderList()`, `moveColumn()`
  - Data transformation: `transformData()`, `parseDate()`
  - Preview: `updatePreview()`
  - Export: Copy to clipboard and download handlers

## Language

The UI text is in German. When making changes, maintain German language for user-facing strings.
