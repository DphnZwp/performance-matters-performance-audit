> _Fork_ deze leertaak en ga aan de slag. Onderstaande outline ga je gedurende deze taak in jouw eigen GitHub omgeving uitwerken. De instructie vind je in: [docs/INSTRUCTIONS.md](docs/INSTRUCTIONS.md)

# Titel
De website van McDonalds met informatie over McDonalds en het restaurant.

![1650884835813](https://user-images.githubusercontent.com/69635977/165077450-969547ec-0e65-45b6-8f6a-c456d1ae8b0a.png)

## ContentAudit
De website van McDonalds heeft informatie over het menu, actuele informatie, services, extra informatie over voedsel kwaliteit en informatie wat je kan doen met je familie. Ik heb een performance analyse gedaan voor deze website.

### Getest op 25 april 2022
![Schermafbeelding 2022-04-26 172132](https://user-images.githubusercontent.com/69635977/165336369-a1fc4b34-5761-49c8-9e14-53391fdc987c.png)

### Link
[https://www.mcdonalds.com/nl/nl-nl/familie.html](https://www.mcdonalds.com/nl/nl-nl/familie.html)

### First Contentful Paint (FCP)
*FCP meet hoe lang het duurt voordat de browser het eerste stuk DOM-inhoud weergeeft nadat een gebruiker naar de pagina heeft genavigeerd.*

![Schermafbeelding 2022-04-26 172201](https://user-images.githubusercontent.com/69635977/165336442-5c3ba9dc-d4f7-4bc8-aa77-3107d12d2ec8.png)

De FCP van McDonalds is 1.7 s. Een probleem dat vooral belangrijk is voor FCP, is de laadtijd van lettertypen. Ik kan er bijvoorbeeld voor zorgen dat tekst zichtbaar blijft tijdens het laden van webfonts.

#### Mogelijkheden
- Preconnect to required origins
- Eliminate render-blocking resources

#### Diagnostiek
- Ensure text remains visible during webfont load
- Avoid chaining critical requests

### Time to Interactive (TTI)
*TTI meet hoe lang het duurt voordat een pagina volledig interactief wordt.*

![Schermafbeelding 2022-04-26 172215](https://user-images.githubusercontent.com/69635977/165336466-6de0b2e6-a9ba-4966-a11e-5ee3325f905d.png)

De TTI van McDonalds is 5.3 s.

### Speed Index
*Speed Index meet hoe snel inhoud visueel wordt weergegeven tijdens het laden van de pagina.*

![Schermafbeelding 2022-04-26 172233](https://user-images.githubusercontent.com/69635977/165336491-16ec1bca-d9bf-408e-8742-76bece13101f.png)

De Speed Index van McDonalds is 4.7 s.

### Total Blocking Time (TBT)
*TBT meet de totale hoeveelheid tijd dat een pagina is geblokkeerd om te reageren op gebruikersinvoer, zoals muisklikken, schermtikken of toetsenborddrukken. Het is een som van alle tijdsperioden tussen FCP en Time to Interactive, wanneer de taakduur meer dan 50 ms bedroeg, uitgedrukt in milliseconden.*

![Schermafbeelding 2022-04-26 172248](https://user-images.githubusercontent.com/69635977/165336532-1d6eeb91-d91d-41ce-8efc-c0d91c806219.png)

### Largest Contentful Paint (LCP)
*LCP meet wanneer het grootste inhoudselement in de viewport op het scherm wordt weergegeven. Dit benadert wanneer de hoofdinhoud van de pagina zichtbaar is voor gebruikers.*

![Schermafbeelding 2022-04-26 172306](https://user-images.githubusercontent.com/69635977/165336550-c568405a-ccfb-4dd1-b924-c9d00b5af628.png)

### Cumulative Layout Shift (CLS)
_Beschrijf de uitslag van de CLS van de test en toon de resultaten. Beschrijf wat kan worden verbeterd als de score minder dan 90 is._

![Schermafbeelding 2022-04-26 172321](https://user-images.githubusercontent.com/69635977/165336573-ecb47bea-28c1-4f99-8d97-c6d693f294da.png)

## Bronnen

## Licentie

![GNU GPL V3](https://www.gnu.org/graphics/gplv3-127x51.png)

This work is licensed under [GNU GPLv3](./LICENSE).
