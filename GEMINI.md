# Projekt-Dokumentation: Speisekarte Restaurant Daphne (Signature Edition)

Dieses Projekt dient der Erstellung und Wartung einer hochpräzisen, 18-seitigen Speisekarte f&uuml;r das Restaurant **Daphne** in Bremen. Der Fokus liegt auf einem perfekten PDF-Export f&uuml;r den professionellen Druck (A4).

## Technische Standards (Stand M&auml;rz 2026)

### 1. Layout & Print-Pr&auml;zision
- **Seitenformat**: Fest auf A4 (`210mm x 297mm`).
- **Seiten-Struktur**: `.page` ist der A4-Container. `.content` ist ein Flex-Container, der den Inhalt aufnimmt und den Footer unten hält.
- **Sicherheitsabstand (Binding Safe)**: `padding: 25mm 30mm 15mm` f&uuml;r die `.content`-Klasse.
- **Vermeidung von Umbr&uuml;chen**: 
  - `break-inside: avoid` f&uuml;r alle Gerichte (`.mi`).
  - `white-space: nowrap` f&uuml;r Preise (`.p`) und Einheiten.
- **Druck-spezifische Regeln**:
  - `@media print { .no-print { display: none; } }` wird verwendet, um den Export-Button in der PDF-Datei auszublenden.

### 2. Typografie & Design
- **Schriftarten**: `Cinzel` (Titel), `Lora` (Gerichte), `Cormorant Garamond` (Beschreibungen).
- **Konsistenz**: Jede Inhaltsseite (2-18) verf&uuml;gt &uuml;ber eine `.border-frame` f&uuml;r einen edlen, umlaufenden Rahmen.
- **Mythos-Seite**: Nutzt `hyphens: auto` und `line-height: 1.9` f&uuml;r optimalen Blocksatz.

### 3. Bildsprache
- **Lokale Assets**: Alle Bilder werden im `images/`-Ordner gespeichert, um Ladefehler zu verhindern. Es werden keine externen URLs mehr verwendet.
- **Platzierung**:
  - Auf Standardseiten (flex) wird die `.img-box` durch `<div style="flex:1"></div>` an den unteren Rand gedr&uuml;ckt.
  - Auf Getr&auml;nkeseiten wird ein verschachteltes `.mc-grid` verwendet, damit `.content` weiterhin eine Flexbox bleibt und das Bild korrekt positioniert wird.
- **Bild-Fokus**: `object-position` wird genutzt, um den sichtbaren Bereich eines Bildes anzupassen (z.B. `object-position: center 80%` f&uuml;r das Dessert).
- **H&ouml;henmanagement**: Auf vollen Seiten wird die H&ouml;he der `.img-box` manuell via `style="height: ...px"` reduziert.

### 4. Digitale Integration
- **Website**: Offizielle URL ist `https://restaurant-daphnebremen.de/`.
- **QR-Code**: Auf der R&uuml;ckseite (S. 18) verweist ein QR-Code auf die Website.

## PDF-Export Prozess

Der Export **muss** &uuml;ber Microsoft Edge (Headless) erfolgen, um die volle Kontrolle &uuml;ber CSS und lokale Bilder zu behalten:

```powershell
& "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --headless --disable-gpu --no-pdf-header-footer --print-to-pdf="$PWD\output\export.pdf" "$PWD\index.html"
```

## Wartungs-Checkliste
1. Preise in `index.html` anpassen.
2. Sicherstellen, dass neue Bilder im `images/` Ordner abgelegt und die Pfade in `index.html` aktualisiert werden.
3. PDF exportieren.
4. Pr&uuml;fung: Fluchten alle Preise rechtsb&uuml;ndig? Sind alle Bilder korrekt zentriert und positioniert? Ist der Footer auf allen Seiten sichtbar?
