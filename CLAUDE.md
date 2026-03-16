# Speisekarte Restaurant Daphne (Signature Edition)

Digitales Layout-System f&uuml;r den professionellen Gastronomie-Druck.

## Architektur-Prinzipien
- **PDF-First**: Das Layout ist f&uuml;r den A4-Export via Microsoft Edge (Headless) optimiert.
- **Sicherheitszonen**: 30mm Seitenabstand f&uuml;r Mappen-Bindung.
- **Surgical Design**: Einsatz von CSS Grid f&uuml;r millmetergenaue Preis-Fluchten.

## Build-Commands
- **PDF-Export (Windows/Edge)**: 
  `& "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --headless --disable-gpu --no-pdf-header-footer --print-to-pdf="$PWD\output\export.pdf" "$PWD\index.html"`

## Styling-Guidelines (M&auml;rz 2026)
- **Typografie**: Cinzel (Title), Lora (Dish Name), Cormorant Garamond (Desc).
- **Abst&auml;nde**: `.content { padding: 25mm 30mm 15mm; }`
- **Preise**: `.mi .p { white-space: nowrap; }` &ndash; niemals Preis von W&auml;hrung trennen.
- **Bilder**: `.img-box` (Standardh&ouml;he: 180px), auf Getr&auml;nkeseiten reduziert auf 120-150px.
- **B&uuml;ndigkeit**: Preise m&uuml;ssen am rechten Rand des Rasters fluchten (75px min-width).

## URLs
- **Web**: `https://restaurant-daphnebremen.de/`
- **QR-Code**: `https://api.qrserver.com/v1/create-qr-code/?size=120x120&data=https://restaurant-daphnebremen.de/&bgcolor=050505&color=c4a265`

*Siehe `GEMINI.md` f&uuml;r detaillierte technische Parameter.*
