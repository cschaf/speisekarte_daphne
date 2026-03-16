# Speisekarte Restaurant Daphne (Signature Edition)

Digitales Layout-System f&uuml;r den professionellen Gastronomie-Druck.

## Architektur-Prinzipien
- **PDF-First**: Das Layout ist f&uuml;r den A4-Export via Microsoft Edge (Headless) optimiert.
- **Lokale Assets**: Alle Bilder sind lokal im `images/` Ordner gespeichert. Keine externen URLs.
- **Sicherheitszonen**: 30mm Seitenabstand (`padding`) f&uuml;r Mappen-Bindung.
- **Flex & Grid Layout**: `.content` ist eine Flexbox. `.mc-grid` wird f&uuml;r die 2-spaltigen Getr&auml;nkeseiten genutzt.

## Build-Commands
- **PDF-Export (Windows/Edge)**: 
  `& "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --headless --disable-gpu --no-pdf-header-footer --print-to-pdf="$PWD\output\export.pdf" "$PWD\index.html"`

## Styling-Guidelines (M&auml;rz 2026)
- **Typografie**: Cinzel (Titel), Lora (Gerichte), Cormorant (Beschreibungen).
- **Preise**: `white-space: nowrap` verhindert Umbr&uuml;che bei Preisen.
- **Bilder**:
  - `object-fit: cover` ist Standard.
  - `object-position: center 80%` wird f&uuml;r das Dessertbild verwendet, um den Fokus zu verschieben.
  - H&ouml;he wird bei Bedarf via `style="height: ..."` angepasst.
- **Print**: Der Export-Button (`.no-print`) wird via `@media print` ausgeblendet.

## URLs
- **Web**: `https://restaurant-daphnebremen.de/`
- **QR-Code**: Verweist auf die Website.

*Siehe `GEMINI.md` f&uuml;r eine ausf&uuml;hrliche technische Dokumentation.*
