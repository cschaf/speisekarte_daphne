# Projekt-Dokumentation: Speisekarte Restaurant Daphne (Signature Edition)

Dieses Projekt dient der Erstellung und Wartung einer hochpräzisen, 18-seitigen Speisekarte f&uuml;r das Restaurant **Daphne** in Bremen. Der Fokus liegt auf einem perfekten PDF-Export f&uuml;r den professionellen Druck (A4).

## Technische Standards (Stand M&auml;rz 2026)

### 1. Layout & Print-Pr&auml;zision
- **Seitenformat**: Fest auf A4 (`210mm x 297mm`).
- **Sicherheitsabstand (Binding Safe)**: `padding: 25mm 30mm 15mm` f&uuml;r die `.content`-Klasse, um sicherzustellen, dass Texte bei der Bindung in Gastronomie-Mappen nicht verdeckt werden.
- **Vermeidung von Umbr&uuml;chen**: 
  - `break-inside: avoid` f&uuml;r alle Gerichte (`.mi`).
  - `white-space: nowrap` f&uuml;r Preise (`.p`) und Einheiten, um "Waisen" (z.B. ein &euro; in der n&auml;chsten Zeile) zu verhindern.
- **Konsistenz**: Jede Inhaltsseite (2-18) verf&uuml;gt &uuml;ber eine `.border-frame` f&uuml;r einen edlen, umlaufenden Rahmen.

### 2. Typografie & Design
- **Cinzel**: F&uuml;r &Uuml;berschriften und Branding (klassisch-griechischer Stil).
- **Lora**: F&uuml;r die Namen der Gerichte (hochwertige Serif).
- **Cormorant Garamond**: F&uuml;r Beschreibungen und Fu&szlig;noten (kursiv, elegant).
- **Mythos-Seite**: Nutzt `hyphens: auto` und einen erh&ouml;hten Zeilenabstand (`line-height: 1.9`) f&uuml;r optimale Lesbarkeit im Blocksatz.

### 3. Bildsprache
- **Qualit&auml;t**: Einsatz von stabilen, hochaufl&ouml;senden Unsplash-IDs.
- **Platzierung**: Bilder befinden sich am Ende der Seite (`margin-top: auto`) und werden &uuml;ber die `.img-box` Klasse gesteuert.
- **Dual-Column Layout**: Auf Getr&auml;nkeseiten (15-18) spannen Bilder &uuml;ber beide Spalten (`grid-column: 1 / -1`).
- **H&ouml;henmanagement**: Auf vollen Seiten (z.B. Getr&auml;nke) wird die H&ouml;he der `.img-box` manuell reduziert (z.B. `120px` bis `150px`), um Overflows zu verhindern.

### 4. Digitale Integration
- **Website**: Offizielle URL ist `https://restaurant-daphnebremen.de/`.
- **QR-Code**: Auf der R&uuml;ckseite (S. 18) f&uuml;hrt ein dynamisch generierter QR-Code (via qrserver.com) direkt zur Reservierungsseite.

## PDF-Export Prozess

Der Export **muss** &uuml;ber Microsoft Edge (Headless) erfolgen, um die volle Kontrolle &uuml;ber CSS-Grids und Google Fonts zu behalten:

```powershell
& "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --headless --disable-gpu --no-pdf-header-footer --print-to-pdf="$PWD\output\export.pdf" "$PWD\index.html"
```

## Wartungs-Checkliste
1. Preise in `index.html` anpassen.
2. Bei langen Texten sicherstellen, dass `.mi .p` nicht umbricht.
3. PDF exportieren.
4. Pr&uuml;fung: Fluchten alle Preise rechtsb&uuml;ndig? Reicht der Platz f&uuml;r die Bindung (30mm links/rechts)? Sind alle Bilder geladen?
