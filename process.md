## Proces CSS to the rescue 

### Week 1

De dinsdag van week 1 kon ik beginnen aan mijn controlepaneel voor CSS to the Rescue, aangezien we daarvoor een andere kleine opdracht kregen om dingen van CSS te onderzoeken.

Ik had in gedachten om een controlepaneel te maken voor een voertuig dat kan vliegen. Na wat experimenteren besloot ik om een UFO te maken, omdat ik dat het leukst vond om mee te experimenteren, en het hoefde er niet zo realistisch uit te zien. De features die mij heel gaaf leken om te maken waren:

- Een joystick waarmee je de UFO kunt besturen.
- Een snelheidshendel die je naar voren en naar achteren kunt schuiven, waarmee je de snelheid van je UFO kunt beïnvloeden.
- Een gave omgeving maken waardoor het lijkt alsof je door de ruimte beweegt.
- Als je over het dashboard hovert, verandert dat je perspectief in de UFO, waardoor het lijkt alsof je je in de UFO bevindt, als de POV van de alien.

Ik begon met het maken van schetsen van hoe ik het wilde maken, en daarna maakte ik de omtrek van de UFO in CSS met een grid op de hoofdsectie. Daarop positioneerde ik een vlak met de joystick en de snelheidshendel, en dat vlak maakte ik schuin met perspectief. Ook voegde ik een radiale gradiënt toe aan het vlak daarachter, wat ervoor zorgde dat het leek alsof je in een ronde cockpit zat.

Daarna begon ik met het maken van de ruimte. Ik had geen idee hoe ik dit zou moeten doen. Ik begon met 2 vlakken die schuin tegenover elkaar lagen. En daarop heb ik gradients, kleine divjes en afbeeldingen geplaatst, maar niets werkte echt goed. Ook heb ik de vlakken geanimeerd zodat ze naar je toe kwamen, maar het leek uiteindelijk een beetje op een dummyruimte. Dit was mijn code:


```css
main > div:nth-child(2) > div {
    height:45vh;
    width: 250%;
    transform-style: preserve-3d;
    --dot-bg: black;
    --dot-color: white;
    --dot-size: 1px;
    --dot-space: 22px;
    background:
          linear-gradient(90deg, var(--dot-bg) calc(var(--dot-space) - var(--dot-size)), transparent 1%) center / var(--dot-space) var(--dot-space),
          linear-gradient(var(--dot-bg) calc(var(--dot-space) - var(--dot-size)), transparent 1%) center / var(--dot-space) var(--dot-space),
          var(--dot-color);
}

main > div:nth-child(2) > div:nth-child(1) {
    transform: rotateX(-24deg) translateY(14%) translateX(-25%);
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    flex-wrap: wrap;
    animation: starsMoving1 2s linear infinite;
}
@keyframes starsMoving1 {
    0% {
        transform: rotateX(-24deg) translateY(28.8%) translateX(-25%);
    }
    100% {
        transform: rotateX(-24deg) translateY(14%) translateX(-25%);
    }
}
main > div:nth-child(2) > div:nth-child(2) {
    transform: rotateX(32deg) translateY(1%) translateX(-25%);
    animation: starsMoving2 2s linear infinite;
}
@keyframes starsMoving2 {
    0% {
        transform: rotateX(32deg) translateY(-13.65%) translateX(-25%);
    }
    100% {
        transform: rotateX(32deg) translateY(1%) translateX(-25%);
    }
}
```

### Week 2

Totdat ik in week twee op CodePen iets heel cools zag. Daar had iemand een ruimte gemaakt waar je doorheen kon bewegen, bestaande uit vier vlakken met afbeeldingen erop. De vlakken bewogen naar je toe, waardoor het leek alsof je aan het bewegen was. Ik heb dat toen gekopieerd, uitgepluisd, aangepast en ermee geëxperimenteerd totdat het er goed uitzag.

Daarna heb ik de snelheidshendel gekoppeld aan een eigenschap die met wat berekeningen de duur van de animatie beïnvloedde, waardoor het leek alsof je sneller of langzamer ging.

Ook heb ik de joystick gemaakt die de bestemming verandert waar je naartoe gaat en de ufo deels roteert, zodat het lijkt alsof je beweegt.

Op vrijdag hadden we een beoordelingsgesprek en toen zei Sanne dat ik beter de perspectief kon verkleinen in plaats van de duur van de animatie, omdat je het dan kunt animeren en het er vloeiender uitziet als je van snelheid verandert. Hier heb ik ook mee geëxperimenteerd. Ik wilde de range-input niet instellen op 0 tot 500px, omdat dan het einde van het bereik veel meer invloed heeft dan de rest. Dus vermenigvuldigde ik de waarde met 5. Dit was al iets beter, maar nog niet helemaal. Ook zie je vaak in films met een ruimteschip dat ze een bepaalde modus moeten activeren voordat ze op hun topsnelheid zitten. Dit heb ik toen ook gedaan, zodat ik weer een extra knop had op mijn bedieningspaneel en het beter werkte. Ook heb ik toen de overgang op 1 seconde gezet, waardoor je een lichte vertraging hebt omdat de ufo natuurlijk op gang moet komen voordat hij echt de ruimte ingezogen wordt.


### Week 3

Deze week was ik bezig met de joystick en de repsonsiveness van mijn ufo. Op kleine schermen is het dashboard namelijk slecht zichtbaar en overlapte de elementen elkaar. Ook werd de border heel rond waardoor de elementen uit het dashboard uit de ufo staken. Dit heb ik opgelost met wat media queries. De joystick was wel een uitdaging. Ik begon met buttons die op click de ufo kantelde en de omgeving verplaatste. Daarna begon ik met het maken van de joystick. Ik begon met 2 divjes en later werden het de `:before` en `:after` van een div want ik wilde oefenen met `:before` en `:after`.
Ik heb geprobeerd om het als geheel te kantelen en los, en daarbij zag los er beter uit. Wel lijkt het stokje soms niet echt aan de bol vast te zitten maar dit zijn kleine momenten en ook alleen als je naar links of rechts stuurt. Wel zit de joystick er goed uit als je hem naar je toe trekt en van je af duwt.
Ik liet de buttons later de omgeving beinvloeden door erop te hoveren maar dat voelde niet echt chill en realistisch. Toen kreeg ik een idee van een klasgenoot die active ophet element in het midden en dan hover op de buttons had om de joystick te bewegen. Dit geeft je het gevoel dat je de joystick vast moet houden en dan kan bewegen. Dit heb ik toen toegepast en het werkte prima. Het enige probleem was dat de joystick tripte als je naar rechts wilde sturen. Ik heb geprobeerd dit op te lossen door de bol kleiner te maken, de buttons groter en de buttons verder weg van de joystick maar niks leek te werken.

### Week 4 

Deze week ging ik de radar maken, propeerde ik een sound toe te voegen van een opstartende ufo als je de power aanzet. En experimenteerde ik met verschillende afbeelingen van de ruimte. Ook voegde ik een titel toe met een kleine animatie in de ufo. En voegde ik bepaalde cursors toe met handjes die dingen kunnen grijpen waardoor de gebruiker weet wat hij kan aanklikken en vastpakken etc.

Ook probeerde ik op hover van het dashboard, het ruimte schip met de achtergrond een beetje te laten bewegen. Dit lukte natuurlijk wel met de achtergrond maar met het ruimte schip lukte dat niet. Dit komt omdat het ruimte schip natuurlijk niet 3D is en de achtergrond wel. Uiteindelijk heb ik alleen de achtergrond een beetje laten bewegen en niet het ruimte schip. De volgende keer maak ik de cockpit wel 3D en dan zou dit wel moeten lukken. 

Ook heb ik deze week @layers toegoegd aan een aantal css files. Dit deed ik omdat het een requirement was van de opdracht. @layers kan je goed gebruiken om lagen zoals: basis, layout, stylingComponents, specialStyling te definieren en zo iets overzichtelijkere code kan schrijven. Ook kan je het gebruiken om specificity problemen op te lossen. Helaas heb ik dit niet mijn code voor zien komen, maar als het voorkomt kan je bijvoorbeeld zo: `@layer base, special;` de volgorde van de layers definieren. 

Op donderdag heb ik de joystick gefixed. Hij tripte helaaml als je hem naar rechts en naar beneded trok, en dat lag aan een rotateY op de label. Hier kwam ik achter na een hoop inspecteren en dingen uitzetten. Ik moest daarna wel wat values van de `:before` veranderen zodat die mooi meegaat met het hoofd van de joystick.

#### De radar

De radar maken ging best goed. Met linear en radial gradients maakte ik de lijnen op de radar. En met een conic gradient maakte ik hetgene dat rond draait. 

```css
form:nth-child(2) div:nth-of-type(3) {
    overflow: hidden;
     background:
     linear-gradient(0deg, transparent 50%, var(--radar-color) 49% 51%, transparent 51% 100%),
     linear-gradient(90deg, transparent 50%, var(--radar-color) 49% 51%, transparent 51% 100%),
     linear-gradient(45deg, transparent 50%, var(--radar-color) 49% 51%, transparent 51% 100%),
     linear-gradient(135deg, transparent 50%, var(--radar-color) 49% 51%, transparent 51% 100%),
     conic-gradient( from var(--angle),transparent, var(--radar-color)),
     radial-gradient(transparent 25%, var(--radar-color) 25% 26%, transparent 27% 100%),
     radial-gradient(transparent 50%, var(--radar-color) 49% 51%, transparent 51% 100%),
     radial-gradient(transparent 75%, var(--radar-color) 75% 76%, transparent 77% 100%);
     animation: rotate var(--animation-duration-radar) linear infinite;
     animation-delay: -1.65s;
}

@keyframes rotate {
    0% {
        --angle: 0deg;
    }
    100% {
        --angle: 360deg;
    }
}
```

Ook maakte ik een zwart rond divje van 4px die van boven naar beneden gaat in de radar, en alleen zichtbaar is wanneer de radar erover heen is gegaan. Na wat timen lukte dit maar ik wist al zeker dat dit veel beter kan wordne geschreven. Op dinsdag begon ik met het herschrijven van deze regels en met berekeningen en custom properties dit veel dynamischer te maken. 

Uiteindelijk lukte het mij niet om heel ver te komen. Uiteindelijk wertke 2 en 3 stappen maar meer niet. Dit komt omdat het vaste keyframes zijn een die kan je niet dynamisch aanmaken. Wel heb ik een beetje geprobeerd te rekenen van hoeveel het divje naar beneden moet bewegen aan de hand van hoevaak die moet bewegen, en heb ik meerdere keyframes aangemaakt. Maar wanneer die moet bewegen is afhankelijk van de tijd van het rondje van de radar, de afstand en natuurlijk waar die gepositioneerd is in de radar. Hier kwam ik niet uit. 

#### Geluid

Het afspelen van geluid is mij niet gelukt deze weken. Wel heb ik het geprobeerd, en door alle webkit attributen op het audio element op display none te zetten, en de playbutton een hoge z-index te geven kan je dus alleen de playbutton zien. Als je die dan een `opacity: 0;` geeft en hem boven op de button zet kan je dus een geluid afspelen. Alleen dan kan je niet met `:has()` de button erachter zogenaamd op acitve zetten. Dus ik besloot om dit te laten, en de button te disabelen.  