> _Fork_ deze leertaak en ga aan de slag. Onderstaande outline ga je gedurende deze taak in jouw eigen GitHub omgeving uitwerken. De instructie vind je in: [docs/INSTRUCTIONS.md](docs/INSTRUCTIONS.md)

# Performance audit McDonalds
De website van McDonalds met informatie over McDonalds en het restaurant.

![FireShot Capture 002 - McDonald's Nederland - McDonald's - www mcdonalds com](https://user-images.githubusercontent.com/69635977/165352882-00c3dcd9-786d-4015-8972-75f8860475f8.png)

## ContentAudit
De website van McDonalds heeft informatie over het menu, actuele informatie, services, extra informatie over voedsel kwaliteit en informatie wat je kan doen met je familie. Ik heb een performance analyse gedaan voor deze website met behulp van Lighthouse.

### Datum
Getest op 25 april 2022

### Website
[https://www.mcdonalds.com/nl/nl-nl/familie.html](https://www.mcdonalds.com/nl/nl-nl/familie.html)

![Schermafbeelding 2022-04-26 172132](https://user-images.githubusercontent.com/69635977/165336369-a1fc4b34-5761-49c8-9e14-53391fdc987c.png)

### Netwerk test
De website heeft 86 requests en heeft een *Finish* tijd van 21.86 s en een *Load* tijd van 21.03 s wanneer er snelle 3g internet is zonder cache.

*Transfered* betekend van het netwerk, de rest (van de 758 kB in totaal) was afkomstig uit de cache.

*Finish* is het tijdstempel van de laatste resource, dus het verandert telkens wanneer een nieuw verzoek wordt gedaan. De *Finish* tijd in Chrome Devtools bevat de asynchroon laden (niet -blokkerende) objecten/-elementen op de pagina die kunnen blijven downloaden na de ONLOAD -gebeurtenis voor de pagina is geladen.

*DOMContentLoaded* is de tijdstempel van de DOMContentLoaded-gebeurtenis: geactiveerd wanneer het oorspronkelijke HTML-document volledig is geladen en geparseerd, zonder te wachten tot stylesheets, afbeeldingen en subframes klaar zijn met laden

*Load* is het tijdstempel van de laadgebeurtenis: geactiveerd wanneer een resource en de afhankelijke resources zijn geladen. De reactietijd voor een website betekent in het algemeen de *Load* tijd, omdat dat waarneembaar is voor de gebruiker en op dit punt kan de gebruiker zien dat de browser is voltooid en de pagina klaar is op het scherm.

![Schermafbeelding 2022-04-28 233046](https://user-images.githubusercontent.com/69635977/165849135-10f7c71d-d5cc-4f70-8b2e-d57657e244c9.png)

### First Contentful Paint (FCP)
*FCP meet hoe lang het duurt voordat de browser het eerste stuk DOM-inhoud weergeeft nadat een gebruiker naar de pagina heeft genavigeerd.*

#### De FCP van McDonalds is 1.7 s
![Schermafbeelding 2022-04-26 172201](https://user-images.githubusercontent.com/69635977/165336442-5c3ba9dc-d4f7-4bc8-aa77-3107d12d2ec8.png)

Een probleem dat vooral belangrijk is voor FCP, is de laadtijd van lettertypen. Ik kan er bijvoorbeeld voor zorgen dat tekst zichtbaar blijft tijdens het laden van webfonts.

#### Mogelijkheden van McDonalds
- Maak vooraf verbinding met de vereiste bronnen
- Render-blokkerende bronnen elimineren

#### Diagnostiek van McDonalds
- Zorg ervoor dat tekst zichtbaar blijft tijdens het laden van webfonts
- Vermijd het koppelen van kritieke verzoeken

### Time to Interactive (TTI)
*TTI meet hoe lang het duurt voordat een pagina volledig interactief wordt.*

#### De TTI van McDonalds is 5.3 s
![Schermafbeelding 2022-04-26 172215](https://user-images.githubusercontent.com/69635977/165336466-6de0b2e6-a9ba-4966-a11e-5ee3325f905d.png)

Een verbetering die een bijzonder groot effect kan hebben op TTI, is het uitstellen of verwijderen van onnodig JavaScript-werk. Naar mogelijkheden zoeken om de JavaScript te optimaliseren. Verder kunnen JavaScript-payloads verminderd worden door code te splitsen en het PRPL-patroon toe te passen. Het optimaliseren van JavaScript van derden levert voor sommige sites ook aanzienlijke verbeteringen op.

### Speed Index
*Speed Index meet hoe snel inhoud visueel wordt weergegeven tijdens het laden van de pagina.*

#### De Speed Index van McDonalds is 4.7 s
![Schermafbeelding 2022-04-26 172233](https://user-images.githubusercontent.com/69635977/165336491-16ec1bca-d9bf-408e-8742-76bece13101f.png) 

#### Hoewel alles wat je kan doen om de laadsnelheid van de pagina te verbeteren, de snelheidsindexscore zal verbeteren, zou het aanpakken van problemen die door deze diagnostische audits worden ontdekt, een bijzonder grote impact moeten hebben:
- Minimaliseer het hoofddraadwerk
- Verkort de uitvoeringstijd van JavaScript
- Zorg ervoor dat tekst zichtbaar blijft tijdens het laden van webfonts

### Total Blocking Time (TBT)
*TBT meet de totale hoeveelheid tijd dat een pagina is geblokkeerd om te reageren op gebruikersinvoer, zoals muisklikken, schermtikken of toetsenborddrukken. Het is een som van alle tijdsperioden tussen FCP en Time to Interactive, wanneer de taakduur meer dan 50 ms bedroeg, uitgedrukt in milliseconden.*

#### De TBT van McDonalds is 1,410 ms
![Schermafbeelding 2022-04-26 172248](https://user-images.githubusercontent.com/69635977/165336532-1d6eeb91-d91d-41ce-8efc-c0d91c806219.png)

#### Over het algemeen zijn de meest voorkomende oorzaken van lange taken:
- Onnodig laden, parseren of uitvoeren van JavaScript. Tijdens het analyseren van de code in het Performance-paneel ontdek je misschien dat de hoofdthread werk doet dat niet echt nodig is om de pagina te laden. Het verminderen van JavaScript-payloads met codesplitsing, het verwijderen van ongebruikte code of het efficiënt laden van JavaScript van derden zou de TBT-score moeten verbeteren.
- Inefficiënte JavaScript-instructies. Stel dat je na analyse van de code in het deelvenster Performance een aanroep ziet naar document.querySelectorAll('a') die 2000 nodes retourneert. Door de code te herstructureren om een meer specifieke selector te gebruiken die slechts 10 nodes retourneert, zou de TBT-score moeten verbeteren.

#### Diagnostiek van McDonalds
- Minimaliseer werk in de hoofdthread
- Verkort de uitvoeringstijd van JavaScript
- Vermijd een buitensporige DOM-grootte
- Vermijd lange hoofdthread-taken

### Largest Contentful Paint (LCP)
*LCP meet wanneer het grootste inhoudselement in de viewport op het scherm wordt weergegeven. Dit benadert wanneer de hoofdinhoud van de pagina zichtbaar is voor gebruikers.*

#### De LCP van McDonalds is 3.6 s
![Schermafbeelding 2022-04-26 172306](https://user-images.githubusercontent.com/69635977/165336550-c568405a-ccfb-4dd1-b924-c9d00b5af628.png) 

#### LCP wordt voornamelijk beïnvloed door vier factoren:
- Trage serverreactietijden
- Render-blokkerende JavaScript en CSS
- Laadtijden van bronnen
- Weergave aan de client side

#### Individuele performance technieken die LCP kunnen verbeteren:
- Pas direct laden toe met het PRPL-patroon
- Het kritieke weergavepad optimaliseren
- Optimaliseren van CSS
- Optimaliseren van afbeeldingen
- Weblettertypen optimaliseren
- Optimaliseer van JavaScript (voor client-rendered sites)

#### Mogelijkheden van McDonalds
- Verminder ongebruikt JavaScript
- Maak vooraf verbinding met de vereiste bronnen
- Render-blokkerende bronnen elimineren

#### Diagnostiek van McDonalds
- Zorg ervoor dat tekst zichtbaar blijft tijdens het laden van webfonts
- Vermijd enorme netwerkbelastingen
- Vermijd het koppelen van kritieke verzoeken

### Cumulative Layout Shift (CLS)
*CLS meet de beweging van zichtbare elementen binnen de viewport. Het is een meting voor de grootste uitbarsting van lay-outverschuivingsscores voor elke onverwachte lay-outverschuiving die optreedt gedurende de gehele levensduur van een pagina.*

#### Wat is een lay-outverschuiving?
Een lay-outverschuiving vindt plaats wanneer een zichtbaar element van positie verandert van het ene weergegeven frame naar het volgende.

Een uitbarsting van lay-outverschuivingen, ook wel een sessievenster genoemd, is wanneer een of meer individuele lay-outverschuivingen snel achter elkaar plaatsvinden met minder dan 1 seconde tussen elke shift en een maximum van 5 seconden voor de totale duur van het venster.

De grootste burst is het sessievenster met de maximale cumulatieve score van alle lay-outverschuivingen binnen dat venster.

#### Voor de meeste websites kun je alle onverwachte lay-outverschuivingen vermijden door je aan een paar leidende principes te houden:
- Voeg altijd maatkenmerken toe aan afbeeldingen en video-elementen, of reserveer op een andere manier de vereiste ruimte met bijvoorbeeld [CSS aspect ratio boxes](https://css-tricks.com/aspect-ratio-boxes/). Deze aanpak zorgt ervoor dat de browser de juiste hoeveelheid ruimte in het document kan toewijzen terwijl de afbeelding wordt geladen. Houd er rekening mee dat u ook het [functiebeleid voor media zonder formaat](https://github.com/w3c/webappsec-permissions-policy/blob/main/policies/unsized-media.md) kan gebruiken om dit gedrag te forceren in browsers die functiebeleid ondersteunen.
- Plaats nooit inhoud boven bestaande inhoud, behalve als reactie op een gebruikersinteractie. Dit zorgt ervoor dat eventuele lay-outverschuivingen worden verwacht.
- Geef de voorkeur aan het transformeren van animaties naar animaties van eigenschappen die lay-outwijzigingen veroorzaken. Animeer overgangen op een manier die context en continuïteit van staat tot staat biedt.

#### De CLS van McDonalds is 0.29
![Schermafbeelding 2022-04-26 172321](https://user-images.githubusercontent.com/69635977/165336573-ecb47bea-28c1-4f99-8d97-c6d693f294da.png)

#### Diagnostiek van McDonalds
- Afbeeldingselementen hebben geen expliciete breedte en hoogte
- Vermijd grote lay-outverschuivingen

## Bronnen
- [https://developers.google.com/web/tools/lighthouse](https://developers.google.com/web/tools/lighthouse)
- [https://web.dev/](https://web.dev/)
- [https://css-tricks.com/aspect-ratio-boxes/](https://css-tricks.com/aspect-ratio-boxes/)
- [https://github.com/w3c/webappsec-permissions-policy/blob/main/policies/unsized-media.md](https://github.com/w3c/webappsec-permissions-policy/blob/main/policies/unsized-media.md)

## Licentie

![GNU GPL V3](https://www.gnu.org/graphics/gplv3-127x51.png)

This work is licensed under [GNU GPLv3](./LICENSE).
