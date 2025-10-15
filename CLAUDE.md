# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file web application for CSV format conversion. The entire application is contained in `csvconverter.html` - a standalone HTML file with embedded CSS and JavaScript.

## Architecture

**Single-Page Application Structure:**
- Self-contained HTML file with no external dependencies
- Pure vanilla JavaScript (no frameworks)
- Client-side only - all processing happens in the browser
- No build process or compilation required

**Core Functionality:**
The application provides CSV file format conversion with:
- File upload via click or drag-and-drop
- Configurable input delimiter detection (comma, semicolon, tab, pipe)
- Output format conversion (CSV, JSON, Excel/TSV)
- Configurable output delimiters
- Live preview of parsed data (first 10 rows)
- Header row detection toggle

**Data Flow:**
1. File upload → `handleFile()` → FileReader API
2. Text parsing → `parseCSV()` → converts to array of objects
3. Preview rendering → `updatePreview()` → populates HTML table
4. Export → `convertToCSV()`/`convertToTSV()` → generates output → `downloadFile()`

**Key Implementation Details:**
- CSV parsing uses string split operations (lines 303-329)
- Data is stored in two global variables: `csvData` (array of objects) and `headers` (array of strings)
- Proper CSV escaping: values containing delimiters or quotes are quoted and escaped (lines 398-400)
- File download uses Blob API with data URLs (lines 413-423)

## Development

Since this is a single HTML file with no build process:

**Running/Testing:**
- Open `csvconverter.html` directly in a web browser
- Or serve via local HTTP server: `python3 -m http.server 8000`

**Making Changes:**
- Edit the HTML file directly
- Refresh browser to see changes
- CSS is in `<style>` block (lines 7-174)
- JavaScript is in `<script>` block (lines 241-424)

**Code Organization:**
- Styles: Lines 7-174
- HTML structure: Lines 176-239
- JavaScript logic: Lines 241-424
  - Event listeners: Lines 252-288
  - CSV parsing: Lines 303-330
  - Preview rendering: Lines 332-361
  - Export functions: Lines 363-423

## Language

The UI text is in German. When making changes, maintain German language for user-facing strings.
