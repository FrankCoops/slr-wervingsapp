# Wervingsapp — Stedelijk Lyceum Rotterdam

Interactieve wervings-/voorlichtingsapp (prototype) voor het Stedelijk Lyceum
Rotterdam, dat in 2027 opent op de Kop van Zuid. De app presenteert de school in
zes hoofdstukken — introductie, het gebouw, de Kop van Zuid, het onderwijsconcept
"De Stad als Klaslokaal", de projecten en aanmelden — binnen een iPhone-frame.

Dit is de geïmplementeerde versie van het Claude Design-bestand
`Wervingsapp SLR.dc.html`.

## Snel starten

De app is een statische site. Serveer de map met een willekeurige webserver —
openen via `file://` werkt **niet** (de runtime laadt onderdelen via `fetch`).

```bash
python3 -m http.server 8000
```

Open daarna http://localhost:8000 in je browser.

> Er is een internetverbinding nodig: de runtime (`support.js`) laadt React en de
> JSX-compiler (Babel) van unpkg.com.

## Structuur

```
index.html                 → de app (identiek aan "Wervingsapp SLR.dc.html")
Wervingsapp SLR.dc.html     → origineel Claude Design-bronbestand
support.js                  → Claude Design "DC" runtime (parst de template, rendert met React)
ios-frame.jsx               → iPhone-frame component (IOSDevice e.d.)
image-slot.js               → <image-slot> web-component (uit de starter, meegeleverd)
fonts/                      → Gilroy (Light/Regular/SemiBold/Bold/ExtraBold)
assets/photos/              → foto's gebruikt in de app
uploads/                    → foto's van de school en projectlocaties
```

Alle app-logica en teksten staan in `index.html`, in het
`<script type="text/x-dc" data-dc-script>`-blok onderaan het bestand. Daar pas je
de projecten, stappen, redenen en overige inhoud aan.

## Foto's — deels echt, deels nog placeholder

De code, fonts en volledige app-logica zijn 1-op-1 uit het ontwerp overgenomen.
De **foto's konden niet automatisch worden opgehaald** (de lees-tool heeft een
limiet van ~196 KB per bestand; de originele foto's zijn groter).

**Al ingevuld met de echte foto** (aangeleverd via de map `Afbeeldingen/`):

- `uploads/DeMaas.jpg`
- `uploads/Oranjeboomstraat.jpg`
- `uploads/Pagina_Binnenrotte.png`
- `uploads/Stadionpark.jpg`
- `uploads/Wilhelminapier.jpg`

**Nog grijze placeholder — hier moeten de echte foto's nog in** (12):

- `assets/photos/cover.jpg` · `groep.jpg` · `stadsjongen.jpg` · `avond.jpg` ·
  `brug.jpg` · `leerling-1.jpg` · `skyline-lucht.png`
- `uploads/20230718-c01.jpg` · `20230718-c02.jpg` · `20230718-c07.jpg` ·
  `20230718-c08.jpg` · `pasted-1785187167939-0.png`

Vervangen gaat het makkelijkst zo: zet de echte bestanden in de map
`Afbeeldingen/` (of kopieer ze direct naar het juiste pad hierboven). De
afmetingen mogen afwijken; alleen `assets/photos/skyline-lucht.png` wordt op een
vaste maat (402×268) gebruikt voor de interactieve kaart, dus houd die verhouding
aan.

## Naar GitHub pushen

```bash
git remote add origin https://github.com/<gebruiker>/<repo>.git
git push -u origin main
```

De app is direct te hosten via GitHub Pages (Settings → Pages → deploy from
branch → `main` / root). `index.html` is het startpunt.
