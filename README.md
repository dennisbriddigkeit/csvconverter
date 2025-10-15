# CSV to Excel Converter

A single-page web application for converting bank statement CSV files into a fixed Excel-compatible format.

## Features

- **Column Mapping**: Map CSV columns to fixed structure (Date, Empfänger, Sum)
- **8-Column Output**: Outputs format with placeholder columns for Excel formulas
- **Copy to Clipboard**: Direct paste into Excel with one click
- **Multiple Delimiters**: Supports comma, semicolon, tab, and pipe delimiters
- **Live Preview**: See transformed data before export
- **100% Client-Side**: No server required, runs entirely in your browser

## Usage

1. Open `csvconverter.html` in your web browser
2. Upload your bank statement CSV file
3. Select the correct delimiter if needed
4. Map your CSV columns to Date, Empfänger, and Sum
5. Click "📋 In Zwischenablage kopieren" to copy
6. Paste into Excel

## Output Format

The converter produces 8 columns:

```
Col1 | Col2 | Date | Col4 | Empfänger | Col6 | Col7 | Sum
```

Empty columns (Col1, Col2, Col4, Col6, Col7) are placeholders for your Excel formulas.

## Running Locally

Simply open the HTML file in any modern browser. No installation or build process required.

Alternatively, serve via local HTTP server:
```bash
python3 -m http.server 8000
```

## License

MIT
