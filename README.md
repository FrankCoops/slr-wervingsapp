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

**Echte projectlocatie-foto's** (aangeleverd via `Afbeeldingen/`):

- `uploads/DeMaas.jpg` · `Oranjeboomstraat.jpg` · `Pagina_Binnenrotte.png` ·
  `Stadionpark.jpg` · `Wilhelminapier.jpg`

**Personen-slots gevuld met zwart-wit stock** uit de beeldbank van het design
system (`Afbeeldingen/Beeldbank/…`), als tijdelijke stand-in:

- `assets/photos/cover.jpg`  ← ethan-de-long
- `assets/photos/groep.jpg`  ← joel-muniz (groepsfoto)
- `assets/photos/stadsjongen.jpg`  ← king-nkosy
- `assets/photos/leerling-1.jpg`  ← jakob-rosen

**Nog grijze placeholder — hier moeten nog echte school-/stadsbeelden in** (8):

- `assets/photos/avond.jpg` · `brug.jpg` · `skyline-lucht.png`
- `uploads/20230718-c01.jpg` · `20230718-c02.jpg` · `20230718-c07.jpg` ·
  `20230718-c08.jpg` · `pasted-1785187167939-0.png`

Deze zijn stad/gebouw (schoolgebouw-renders, skyline, brug, avondbeeld) en zijn
niet met stockportretten te vullen. Vervangen: zet de echte bestanden met exact
deze namen in `Afbeeldingen/` (of kopieer ze direct naar het pad hierboven). De
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
