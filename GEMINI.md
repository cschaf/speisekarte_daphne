# Projekt-Dokumentation: Speisekarte Restaurant Daphne (Signature Edition)

Dieses Projekt dient der Erstellung und Wartung einer hochpräzisen, 18-seitigen Speisekarte für das Restaurant **Daphne** in Bremen. Der Fokus liegt auf einem perfekten PDF-Export für den professionellen Druck (A4).

## Technische Standards (Stand März 2026)

### 1. Layout & Print-Präzision
- **Seitenformat**: Fest auf A4 (`210mm x 297mm`).
- **Seiten-Struktur**: `.page` ist der A4-Container. `.content` ist ein Flex-Container, der den Inhalt aufnimmt und den Footer unten hält.
- **Sicherheitsabstand (Binding Safe)**: `padding: 25mm 30mm 15mm` für die `.content`-Klasse.
- **Vermeidung von Umbrüchen**:
  - `break-inside: avoid` für alle Gerichte (`.mi`).
  - `white-space: nowrap` für Preise (`.p`) und Einheiten.
- **Druck-spezifische Regeln**:
  - `@media print { .no-print { display: none; } }` blendet den Export-Button in der PDF-Datei aus.

### 2. Typografie & Design
- **Schriftarten**: `Cinzel` (Titel), `Lora` (Gerichte), `Cormorant Garamond` (Beschreibungen).
- **Konsistenz**: Jede Inhaltsseite (2–18) verfügt über eine `.border-frame` für einen edlen, umlaufenden Rahmen.
- **Mythos-Seite**: Nutzt `hyphens: auto` und `line-height: 1.9` für optimalen Blocksatz.

### 3. Seitenzahlen-Zentrierung (Fix März 2026)
Das Element `.pf .pn` zeigt die Seitenzahl im Kreis. Das Eltern-Element `.pf` hat `letter-spacing: 2px`, was ohne Korrektur die Zentrierung verschiebt. Daher gilt auf `.pf .pn`:
```css
letter-spacing: 0;
line-height: 1;
text-align: center;
```
Dies stellt sicher, dass ein- **und** zweistellige Zahlen immer zentriert im Kreis erscheinen.

### 4. Bildsprache
- **Lokale Assets**: Alle Bilder im `images/`-Ordner. Keine externen URLs.
- **Platzierung**:
  - Auf Standardseiten (flex) wird `.img-box` durch `<div style="flex:1"></div>` an den unteren Rand gedrückt.
  - Auf Getränkeseiten wird ein verschachteltes `.mc-grid` verwendet.
- **Bild-Fokus**: `object-position` passt den sichtbaren Bereich an (z.B. `center 80%` für Desserts).
- **Höhenmanagement**: Auf vollen Seiten wird `.img-box`-Höhe manuell via `style="height: ...px"` reduziert.

### 5. Bildübersicht (`images/`)
Alle Bilder sind Unsplash-Fotos (kostenlos, kommerziell nutzbar, keine Attribution nötig).

| Datei | Inhalt | Seite |
|-------|--------|-------|
| `cover.jpg` | Mediterraner Restauranttisch im Freien | Cover |
| `appetizers_cold.jpg` | Mezze-Brett mit Pita, Hummus, Oliven | Kalte Vorspeisen |
| `appetizers_warm.jpg` | Warme Tomaten-Ei-Pfanne mit Tzatziki & Oliven | Warme Vorspeisen |
| `salads.jpg` | Griechischer Salat mit Feta & Weinglas | Salate |
| `fish_veggie.jpg` | Lachsfilet auf dunklem Teller | Fisch & Veggie |
| `oven_dishes.jpg` | Souvlaki-Spieße auf dem Grill | Fischspezialitäten (S. 6) |
| `oven_details.jpg` | Mediterrane Tomaten-Reispfanne im Kupfertopf | Beilagen (S. 7) |
| `grill_intro.jpg` | Gemischte Grillplatte mit Saucen | Grillgerichte Intro |
| `grill_specialties.jpg` | Griechisches Grill-Tablett (Souvlaki, Halloumi) | Grillspezialitäten |
| `grill_finale.jpg` | Großer Grillteller mit Spießen & Lammkoteletts | Grillplatten |
| `pasta_pizza.jpg` | Pasta in der Pfanne | Pasta & Pizza |
| `pizza_kids.jpg` | Pizza von oben | Kids & Pizza |
| `desserts.jpg` | Tiramisu | Desserts |
| `drinks_warm.jpg` | Aperol Spritz | Warme Getränke & Aperitifs |
| `drinks_soft.jpg` | Mojito/Limetten-Drink | Softdrinks |
| `drinks_beer_wine.jpg` | Anstoßen mit Rotweingläsern | Biere & Weine |

### 6. Digitale Integration
- **Website**: `https://restaurant-daphnebremen.de/`
- **QR-Code**: Auf der Rückseite (S. 18) verweist ein QR-Code auf die Website.

## PDF-Export Prozess

Der Export **muss** über Microsoft Edge (Headless) erfolgen:

```bash
# Bash (empfohlen für Claude Code / Git Bash):
"/c/Program Files (x86)/Microsoft/Edge/Application/msedge.exe" \
  --headless --disable-gpu --no-pdf-header-footer \
  --print-to-pdf="c:/PFAD/output/export.pdf" \
  "c:/PFAD/index.html"

# PowerShell:
& "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --headless --disable-gpu --no-pdf-header-footer --print-to-pdf="$PWD\output\export.pdf" "$PWD\index.html"
```

## Neue Bilder von Unsplash herunterladen

```bash
# 1. Passende Photos per interner API suchen (kein API-Key nötig):
curl -s "https://unsplash.com/napi/search/photos?query=SUCHBEGRIFF&per_page=10" \
  -H "User-Agent: Mozilla/5.0" -H "Accept: application/json" | \
  python3 -c "
import sys,json,re
d=json.load(sys.stdin)
for r in d.get('results',[]):
    if 'plus.unsplash.com' not in r['urls']['regular']:
        m=re.search(r'photo-([0-9a-f]+-[0-9a-f]+)', r['urls']['regular'])
        if m: print(m.group(1), r['id'])
"

# 2. Bild in hoher Auflösung herunterladen:
curl -L "https://images.unsplash.com/photo-{ID}?w=1600&q=85&fm=jpg" -o images/name.jpg
```

## Wartungs-Checkliste
1. Preise und Gerichte in `index.html` anpassen.
2. Neue Bilder im `images/`-Ordner ablegen und Pfade in `index.html` aktualisieren.
3. Nicht verwendete Bilder aus `images/` entfernen (`git rm`).
4. PDF exportieren und prüfen:
   - Seitenzahlen zentriert im Kreis?
   - Alle Bilder korrekt positioniert?
   - Footer auf allen Seiten sichtbar?
   - Preise ohne Umbruch?
5. Committen und pushen.
