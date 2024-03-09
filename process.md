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
