# Speisekarte Restaurant Daphne (Signature Edition)

Digitales Layout-System für den professionellen Gastronomie-Druck.

## Architektur-Prinzipien
- **PDF-First**: Das Layout ist für den A4-Export via Microsoft Edge (Headless) optimiert.
- **Lokale Assets**: Alle Bilder sind lokal im `images/` Ordner gespeichert. Keine externen URLs.
- **Sicherheitszonen**: 30mm Seitenabstand (`padding`) für Mappen-Bindung.
- **Flex & Grid Layout**: `.content` ist eine Flexbox. `.mc-grid` wird für die 2-spaltigen Getränkeseiten genutzt.

## Build-Commands
- **PDF-Export (Bash/Windows mit Edge)**:
  ```bash
  "/c/Program Files (x86)/Microsoft/Edge/Application/msedge.exe" \
    --headless --disable-gpu --no-pdf-header-footer \
    --print-to-pdf="c:/PFAD/output/export.pdf" \
    "c:/PFAD/index.html"
  ```
- **PDF-Export (PowerShell)**:
  ```powershell
  & "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --headless --disable-gpu --no-pdf-header-footer --print-to-pdf="$PWD\output\export.pdf" "$PWD\index.html"
  ```

## Styling-Guidelines (März 2026)
- **Typografie**: Cinzel (Titel), Lora (Gerichte), Cormorant Garamond (Beschreibungen).
- **Preise**: `white-space: nowrap` verhindert Umbrüche bei Preisen.
- **Seitenzahlen** (`.pf .pn`): `letter-spacing: 0; line-height: 1; text-align: center` — neutralisiert vererbtes `letter-spacing` des Elternelements, damit Zahlen zuverlässig im Kreis zentriert sind (gilt für ein- und zweistellige Zahlen).
- **Bilder**:
  - `object-fit: cover` ist Standard.
  - `object-position: center 80%` wird für das Dessertbild verwendet.
  - Höhe bei Bedarf via `style="height: ..."` anpassen.
- **Print**: Der Export-Button (`.no-print`) wird via `@media print` ausgeblendet.

## Bildübersicht (`images/`)
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

## Neue Bilder von Unsplash herunterladen
```bash
# Bild direkt per CDN herunterladen (ID bekannt):
curl -L "https://images.unsplash.com/photo-{ID}?w=1600&q=85&fm=jpg" -o images/name.jpg

# Photo-IDs über interne Unsplash-API suchen:
curl -s "https://unsplash.com/napi/search/photos?query=greek+food&per_page=10" \
  -H "User-Agent: Mozilla/5.0" -H "Accept: application/json" | \
  python3 -c "
import sys,json,re
d=json.load(sys.stdin)
for r in d.get('results',[]):
    if 'plus.unsplash.com' not in r['urls']['regular']:
        m=re.search(r'photo-([0-9a-f]+-[0-9a-f]+)', r['urls']['regular'])
        if m: print(m.group(1), r['id'])
"
```

## URLs
- **Web**: `https://restaurant-daphnebremen.de/`
- **QR-Code**: Verweist auf die Website.

*Siehe `GEMINI.md` für eine ausführliche technische Dokumentation.*
