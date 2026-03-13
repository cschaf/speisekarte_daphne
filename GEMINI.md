# Projekt-Analyse: Speisekarte Restaurant Daphne

Dieses Projekt ist eine digitale Speisekarte für das mediterrane Restaurant **Daphne** in Bremen. Es ist als responsive Web-Applikation konzipiert, die auch für den Druck (A4-Format) optimiert ist.

## Projektstruktur

- `index.html`: Die zentrale Datei, die den gesamten Inhalt, das Design (CSS) und die Struktur der Speisekarte enthält.
- `alt_menu.pdf`: Eine ältere Version der Speisekarte im PDF-Format (Referenz).
- `Speisekarte_Daphne.docx`: Das Quelldokument der Speisekarte, wahrscheinlich für die Texterstellung genutzt.

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

## Inhaltliche Bereiche

1. **Cover**: Elegante Titelseite mit Logo und Kontaktinformationen.
2. **Über uns**: Hintergrundinformationen zum Restaurant und der Namensgebung (Griechische Mythologie: Daphne & Apollon).
3. **Speisen**:
    - Suppen & Vorspeisen (kalt/warm)
    - Salate & Vegetarische Gerichte
    - Kinderteller
    - Fischgerichte & Ofengerichte
    - Fleischgerichte vom Grill
    - Beilagen, Saucen & Pasta
    - Pizza & Desserts
4. **Getränke**:
    - Warme Getränke, Aperitifs & Digestifs
    - Alkoholfreie Getränke, Säfte & Biere
    - Umfangreiche Weinkarte (Griechisch & International)
5. **Back Cover**: Abschlussseite mit Standort und Website.

## Besondere Funktionen

- **Druck-Button**: Ein dedizierter Button zum Auslösen des Browser-Druckdialogs (`window.print()`).
- **Print-Optimierung**: Verstecken von UI-Elementen (wie dem Druck-Button) im Ausdruck mittels `@media print`.
- **Interaktive Elemente**: Hover-Effekte auf dem Druck-Button.

## Entwicklung & Wartung

Das Projekt ist minimalistisch aufgebaut und benötigt keinen Build-Prozess. Änderungen können direkt in der `index.html` vorgenommen werden. Die Preise und Gerichte sind statisch im HTML hinterlegt.
