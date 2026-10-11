# Le Féminin — statische website

Statische HTML-versie van de expositieflyer. Geen build-stap, geen framework:
upload de map en klaar.

## Bestanden

```
index.html              alle tekst + structuur
css/style.css           opmaak (mobile first)
favicon.svg             tabblad-icoon
images/
  deco-hero-left.webp   linkerhelft van het beschilderde kader rond de titel
  deco-hero-right.webp  rechterhelft; de twee sluiten naadloos op elkaar aan
  deco-flower.webp      bloem linksonder (alleen desktop, vanaf 900 px)
  deco-wave.webp        geschilderde rand onderaan de pagina
  werk-lya.jpg          schilderij Lya (uit de flyer)
  werk-fi.jpg           schilderij Fi (uit de flyer)
  werk-ilonka.jpg       schilderij Ilonka (uit de flyer)
  kunstenaars.jpg       groepsfoto (1600 px)
  kunstenaars-800.jpg   groepsfoto klein, voor mobiel
  flyer.jpg             de originele flyer (link in de footer)
```

De `deco-*.webp` zijn uit de flyer geknipt met een echt transparantiekanaal:
het crèmekleurige papier is weggerekend en de randen lopen zacht uit. Daardoor
is er nergens een rechte "uitgeknipt"-rand te zien, op welk schermformaat dan
ook. De paginakleur `--cream` (`#FCECDD`) is exact de papierkleur van de
flyer — verander je die, dan kunnen de lichtste penseelvegen iets gaan
afsteken.

De iconen (wereldbol, Instagram, locatiespeld, hart, palet, koffie,
tekstballon) komen uit [Lucide](https://lucide.dev) (ISC-licentie). Ze staan
als `<symbol>`-sprite bovenaan `index.html` en worden aangeroepen met
`<svg class="ico"><use href="#i-palette"/></svg>`. Ze erven hun kleur van de
tekst, dus in een knop verkleuren ze mee bij hover. Een ander icoon nodig?
Plak de paden van lucide.dev als nieuw `<symbol>` in de sprite.

De titel is als HTML-tekst over het geschilderde kader gezet (de tekst uit de
flyer is uit de afbeelding weggeretoucheerd), zodat hij scherp blijft en
meeschaalt.

## Links invullen

In `index.html` staat per kunstenaar een blokje:

```html
<div class="artist__links">
  <a class="pill" href="#"> … Website</a>
  <a class="pill" href="#"> … Instagram</a>
</div>
```

Vervang elke `href="#"` door de echte URL, bijvoorbeeld:

- `href="https://www.lyakunst.nl"`
- `href="https://www.instagram.com/lyakunst/"`

Externe links openen in hetzelfde tabblad; wil je een nieuw tabblad, voeg dan
`target="_blank" rel="noopener"` toe (zoals bij Fi en "Route plannen").
Een knop die je niet nodig hebt: verwijder het hele `<a>…</a>` blok — zo
heeft Fi alleen een websiteknop.

Al ingevuld: Fi (<https://finaezer.nl/>) en De Speciaalzaak onder **Locatie**
(<https://www.speciaalzaakvoorburg.nl>). Nog op `href="#"` staan de vier
knoppen van Lya en Ilonka.

## Tekst of foto's wijzigen

- Tekst: rechtstreeks in `index.html`.
- Een schilderij vervangen: zet je eigen bestand in `images/` en pas de `src`
  aan. De kaarten tonen liggende uitsnedes op mobiel (3:4) en staande op
  desktop (346:565); `object-fit: cover` doet de rest, dus elk formaat werkt.
- Kleuren staan bovenaan `css/style.css` in `:root` (maroon `#660B1D`,
  goud `#BA7935`, teal `#244E4D`, crème `#FCECDD` — overgenomen uit de flyer).

## Publiceren

Alles is relatief gelinkt, dus de map werkt op elke statische host
(GitHub Pages, Netlify, Cloudflare Pages, of gewoon FTP naar een map).

Lokaal bekijken:

```bash
python3 -m http.server 8000
# open http://127.0.0.1:8000/
```

Lettertypes (Cinzel + Montserrat) komen van Google Fonts. Zonder internet valt
de site terug op Georgia/Helvetica; de opmaak blijft heel.
