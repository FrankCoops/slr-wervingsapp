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

## Foto's — alle slots gevuld (deels interim stand-in)

De code, fonts en volledige app-logica zijn 1-op-1 uit het ontwerp overgenomen.
De **originele foto's konden niet automatisch worden opgehaald** (de lees-tool
heeft een limiet van ~196 KB per bestand). Alle beelden zijn nu ingevuld — er
staan geen grijze placeholders meer — maar een deel is nog een tijdelijke
stand-in.

**Echte foto's** (aangeleverd via `Afbeeldingen/`, app toont ze in zwart-wit):

- Projectlocaties: `uploads/DeMaas.jpg` · `Oranjeboomstraat.jpg` ·
  `Pagina_Binnenrotte.png` · `Stadionpark.jpg` · `Wilhelminapier.jpg`
- Gebouw-render buitenkant → `assets/photos/cover-gebouw.jpg` (cover / beginpagina)
- Gebouw-render dakplein → `uploads/20230718-c02.jpg` + `uploads/20230718-c07.jpg`
  (Hoofdstuk 2 "Vet gebouw": chapter-hero én home-tegel)

**Stand-in: zwart-wit stock** uit de beeldbank (`Afbeeldingen/Beeldbank/…`):

| Slot | Stockbron |
|------|-----------|
| `assets/photos/cover.jpg` | ethan-de-long (nu alleen index-hero "Waarom je voor ons kiest") |
| `assets/photos/groep.jpg` | joel-muniz (groepsfoto) |
| `assets/photos/stadsjongen.jpg` | king-nkosy |
| `assets/photos/leerling-1.jpg` | jakob-rosen |
| `assets/photos/avond.jpg` | jc-laurio |
| `assets/photos/brug.jpg` | santiago-antunez |
| `uploads/20230718-c01.jpg` | cottonbro-studio |
| `uploads/20230718-c08.jpg` | frank-k |
| `uploads/pasted-1785187167939-0.png` | ralph-rabago |

**Stand-in: gegenereerd** — `assets/photos/skyline-lucht.png` (402×268) is een
gestileerd skyline-silhouet, gemaakt voor de interactieve kaart (de beeldbank had
geen skyline). De klikvlakken/hotspots liggen hierop.

De echte school-/stadsbeelden (schoolgebouw, skyline, brug, avond) kun je later
zelf plaatsen: zet de bestanden met **exact dezelfde naam** in `Afbeeldingen/` of
kopieer ze direct naar het pad hierboven. Afmetingen mogen afwijken; houd voor
`skyline-lucht.png` de verhouding 402×268 aan (interactieve kaart).

## Naar GitHub pushen

```bash
git remote add origin https://github.com/<gebruiker>/<repo>.git
git push -u origin main
```

De app is direct te hosten via GitHub Pages (Settings → Pages → deploy from
branch → `main` / root). `index.html` is het startpunt.
