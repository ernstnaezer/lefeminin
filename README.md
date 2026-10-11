# Le Féminin — statische website

Statische HTML-versie van de expositieflyer. Geen build-stap, geen framework:
upload de map en klaar.

## Bestanden

```
index.html              alle tekst + structuur
css/style.css           opmaak (mobile first)
favicon.svg             tabblad-icoon
share-card.html         bron voor het deelplaatje (zie onder)
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
  og-image.jpg          deelvoorbeeld 1200x630 (WhatsApp e.d.)
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

## Links

Alle knoppen wijzen naar een echte pagina:

| Waar | Knop | Adres |
| --- | --- | --- |
| Lya | Instagram | <https://www.instagram.com/lyaishaak/> |
| Fi | Website | <https://finaezer.nl/> |
| Ilonka | Website | <https://iloospaintings.nl> |
| Lopende tentoonstellingen | Route plannen | Google Maps, Herenstraat 16 |
| Lopende tentoonstellingen | De Speciaalzaak | <https://www.speciaalzaakvoorburg.nl> |

Een knop erbij? Kopieer een `<a class="pill">` blok binnen `artist__links` en
wissel het icoon om: `#i-globe` voor een website, `#i-instagram` voor
Instagram. Een knop weg? Verwijder het hele `<a>…</a>` blok — daarom heeft
Lya alleen Instagram en hebben Fi en Ilonka alleen een website.

Externe links staan op `target="_blank" rel="noopener"`, dus ze openen in een
nieuw tabblad.

## Tekst of foto's wijzigen

- Tekst: rechtstreeks in `index.html`.
- Een schilderij vervangen: zet je eigen bestand in `images/` en pas de `src`
  aan. De kaarten tonen liggende uitsnedes op mobiel (3:4) en staande op
  desktop (346:565); `object-fit: cover` doet de rest, dus elk formaat werkt.
- Kleuren staan bovenaan `css/style.css` in `:root` (maroon `#660B1D`,
  goud `#BA7935`, teal `#244E4D`, crème `#FCECDD` — overgenomen uit de flyer).

## Deelvoorbeeld (WhatsApp, Facebook, LinkedIn)

`images/og-image.jpg` (1200×630, ~105 kB) is het plaatje dat verschijnt als
iemand <https://lefeminin.nl> deelt. Het staat in de `og:`-tags bovenaan
`index.html`; die moeten **absolute** URL's bevatten, anders laat WhatsApp
niets zien.

Het plaatje is gemaakt met `share-card.html`: dat is dezelfde kop als op de
site (zelfde CSS en decoraties) plus de datum- en locatieregel. Wijzigen gaat
zo:

1. Pas de tekst in `share-card.html` aan.
2. Start de lokale server (zie *Publiceren*) en open
   <http://127.0.0.1:8000/share-card.html>.
3. Maak een schermafdruk van het blok `.card` en schaal die naar 1200×630;
   bewaar als `images/og-image.jpg` (JPEG, kwaliteit ±88, blijf onder 300 kB).

WhatsApp onthoudt een voorbeeld lang. Zie je na een wijziging nog het oude
plaatje, deel de link dan één keer met `?v=2` erachter.

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
