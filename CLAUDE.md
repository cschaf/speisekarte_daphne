# Projekt-Analyse: Speisekarte Restaurant Daphne (Signature Edition)

Dieses Projekt umfasst die Entwicklung und Perfektionierung einer digitalen Speisekarte für das mediterrane Restaurant **Daphne** in Bremen. 

**Das oberste Ziel dieses Projekts ist die Erstellung einer perfekten PDF-Datei für den hochwertigen A4-Druck und die Bindung in einer Gastronomie-Mappe.**

## Projektstruktur

- `index.html`: Das Master-Dokument, das Inhalt, Design und Druck-Logik vereint.
- `.github/workflows/deploy.yml`: Pipeline für das automatische Deployment auf GitHub Pages.
- `output/`: Lokales Verzeichnis für die generierten High-End PDF-Exporte (ignoriert via `.gitignore`).
- `README.md`: Projektübersicht mit Status-Badges und Live-Demo Link.
- `GEMINI.md`: Diese Dokumentation der Projektentwicklung und technischen Standards.

## Technische Details & "PDF-First" Fokus

Das Projekt wurde in mehreren Iterationen von einer einfachen Webseite zu einer hochpräzisen Druckvorlage ("Signature Edition") entwickelt.

- **Präzisions-Layout (CSS Grid)**: Einsatz eines 4-Spalten-Grids für die Speisen (Nummer | Name | Füllpunkte | Preis). Dies garantiert, dass die Preise im PDF auf den Millimeter genau rechtsbündig fluchten.
- **Typografische Finesse**:
    - **Überschriften**: `Cinzel` (klassisch-römisch) für ein zeitloses, elegantes Flair.
    - **Gerichte**: `Lora` (Serif) für optimale Lesbarkeit.
    - **Beschreibungen**: `Cormorant Garamond` (kursiv) für eine feine, luxuriöse Anmutung.
    - **Initialen**: Einsatz von Drop-Caps auf der Mythos-Seite für Buchsatz-Qualität.
- **Ästhetik & Farbe**:
    - **Rich Black**: Verwendung von `#050505` für maximale Farbtiefe im Druck.
    - **Gold-Akzente**: Subtile Gold-Verläufe und radial-gradient Füllpunkte, die im PDF gestochen scharf gerendert werden.
- **Druck-Optimierung**:
    - Feste Seitenmaße von `210mm x 297mm`.
    - `break-inside: avoid` für alle Gerichte, um unschöne Seitenumbrüche mitten im Text zu verhindern.
    - Deaktivierung von SVG-Turbulenz-Filtern im Druckmodus, um "weiße Blöcke" im PDF zu vermeiden.
    - Absolute Positionierung der Seitenzahlen und Footer für konstante Platzierung.

## Die "Signature Edition" Struktur (18 Seiten)

Um dem Gast ein Gefühl von Exklusivität und Ruhe zu vermitteln, wurde die Karte auf 18 Seiten entzerrt:

1.  **Cover**: Minimalistisches High-End Design.
2.  **Unsere Geschichte**: Der Daphne-Mythos im edlen Buchsatz.
3.  **Vorspeisen**: Entzerrte Darstellung von Suppen und kalten Vorspeisen.
4.  **Warme Vorspeisen**: Fokus auf hausgemachte Spezialitäten.
5.  **Salate**: Übersichtliche Aufteilung mit Veredelungs-Optionen.
6.  **Meeresfrüchte & Fisch**: Stimmungsvolle Einleitung in die Fischkultur.
7.  **Ofengerichte**: Klassische Spezialitäten.
8.  **Beilagen & Extras**: Logische Platzierung vor den Grillgerichten.
9.  **Vom Grill I**: Einleitung in die Fleischgerichte.
10. **Vom Grill II**: Fokus auf Edelstücke und Spezialitäten.
11. **Grill Finale**: Platten für Gruppen und Ergänzungen.
12. **Pasta & Pizza**: Italienisch-mediterrane Einflüsse.
13. **Pizza & Kinder**: Spezialitäten für die ganze Familie.
14. **Desserts**: Hausgemachte süße Abschlüsse.
15. **Getränke I (Warm & Aperitifs)**: Start der Getränkekarte im **Zwei-Spalten-Layout**.
16. **Getränke II (Digestifs & Softdrinks)**: Übersichtliche Darstellung im dualen Layout.
17. **Biere & Weine I**: Fokus auf Fassbiere und offene Weißweine.
18. **Weine II & Back Cover**: Rotweine und feierlicher Abschluss.

## Deployment & PDF-Export

### Live-Vorschau
Das Projekt wird via GitHub Actions automatisch auf GitHub Pages bereitgestellt:
[Daphne Live-Demo](https://cschaf.github.io/speisekarte_daphne/)

### Master PDF Generation
Der finale Export erfolgt lokal über Microsoft Edge, um die volle Kontrolle über das Rendering zu behalten:

```powershell
& "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --headless --disable-gpu --no-pdf-header-footer --print-to-pdf="$PWD\output\export.pdf" "$PWD\index.html"
```

## Wartung
Änderungen an Preisen oder Gerichten erfolgen direkt in der `index.html`. Nach jeder Änderung muss der oben genannte Befehl ausgeführt werden, um das `export.pdf` zu aktualisieren und die visuelle Integrität zu prüfen.
