# Projekt-Analyse: Speisekarte Restaurant Daphne

Dieses Projekt ist eine digitale Speisekarte für das mediterrane Restaurant **Daphne** in Bremen. Es ist als responsive Web-Applikation konzipiert, die auch für den Druck (A4-Format) optimiert ist.

## Projektstruktur

- `index.html`: Die zentrale Datei, die den gesamten Inhalt, das Design (CSS) und die Struktur der Speisekarte enthält.
- `.github/workflows/deploy.yml`: GitHub Actions Pipeline für das automatische Deployment auf GitHub Pages.
- `output/`: Lokales Verzeichnis für PDF-Exporte (durch `.gitignore` vom Tracking ausgeschlossen).
- `alt_menu.pdf`: Eine ältere Version der Speisekarte im PDF-Format (Referenz).
- `Speisekarte_Daphne.docx`: Das Quelldokument der Speisekarte, wahrscheinlich für die Texterstellung genutzt.
- `.gitignore`: Schließt temporäre Dateien und den `output/` Ordner aus dem Repository aus.

## Technische Details

- **Technologien**: Reines HTML5 und CSS3 (Vanilla CSS).
- **Design-Ansatz**: 
    - **Print-First**: Das Layout ist auf A4-Seiten (`210mm x 297mm`) ausgelegt, um einen hochwertigen PDF-Export oder Ausdruck zu ermöglichen.
    - **Responsive**: Die Darstellung passt sich an Bildschirme an, behält aber das Seiten-Layout bei.
- **Schriftarten**: Verwendung von Google Fonts (`Cinzel`, `Cormorant Garamond`, `Lora`).
- **Medien**: Bilder werden dynamisch von Unsplash geladen.
- **Styling**:
    - Dunkles Farbschema (`#1a1a1a`) mit Gold-Akzenten (`#c4a265`).
    - Einsatz von SVG-Mustern (Meander-Borte) für ein griechisches/mediterranes Flair.
    - CSS-Filter für Rausch-Effekte und Texturen.

## Deployment & CI/CD

Das Projekt wird automatisch über **GitHub Actions** auf **GitHub Pages** bereitgestellt, sobald Änderungen in den `main` Branch gepusht werden.
Die Konfiguration befindet sich in `.github/workflows/deploy.yml`.

## PDF Export

Ein aktueller PDF-Export kann lokal über Microsoft Edge im Headless-Modus generiert werden. Der folgende Befehl erstellt die Datei `export.pdf` im `output/` Verzeichnis:

```powershell
& "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --headless --disable-gpu --no-pdf-header-footer --print-to-pdf="$PWD\output\export.pdf" "$PWD\index.html"
```

## Inhaltliche Bereiche

1. **Cover**: Elegante Titelseite mit Logo und Kontaktinformationen.
2. **Über uns**: Hintergrundinformationen zum Restaurant und der Namensgebung (Griechische Mythologie: Daphne & Apollon).
3. **Speisen**: Suppen, Vorspeisen, Salate, Hauptgerichte, Fisch, Fleisch, Pizza, Pasta und Desserts.
4. **Getränke**: Warme Getränke, Aperitifs, Digestifs, Alkoholfrei, Biere und eine umfangreiche Weinkarte.
5. **Back Cover**: Abschlussseite mit Standort und Website.

## Besondere Funktionen

- **Druck-Button**: Ein dedizierter Button zum Auslösen des Browser-Druckdialogs (`window.print()`).
- **Print-Optimierung**: Verstecken von UI-Elementen im Ausdruck mittels `@media print`.

## Entwicklung & Wartung

Das Projekt ist minimalistisch aufgebaut. Änderungen können direkt in der `index.html` vorgenommen werden. Preise und Gerichte sind statisch im HTML hinterlegt.
