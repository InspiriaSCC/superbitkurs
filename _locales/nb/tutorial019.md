### @activities true

# super:bit - Kodeøkt 10: Bit:Botens FireLEDs
## Bruk de innebygde lysene på Bit:Boten
### Introduksjon @unplugged

Bitboten har to "horn" på sidene.
På hvert av disse sidene sitter det 6 FireLEDs, ofte kalt NeoPixler, som kan styres ved hjelp av kode.
I denne økten lærer du hvordan du kontrollerer FireLEDene på Bit:Boten ved hjelp av et program.

### Steg 1

Alle blokkene du trenger for å styre FireLEDene på Bit:Boten finner du i menyen ``||bitbot.Bitbot/Lys||``.
For å sette alle FireLEDene til en farge kan du bruke blokken ``||bitbot.sett alle LED til||``.
Hent blokken fra ``||bitbot.Bitbot/Lys||``-menyen og dra den inn i ``||basic.ved start||``-blokken.
Klikk på den røde firkanten i blokken for å velge en farge, last ned programmet og se hva som skjer med lysene på Bit:Boten.
Test med forskjellige farger.
*Dersom lysene ikke tennes kan det være fordi Micro:biten fortsatt er koblet til PCen med USB-kabelen.
Slå av Bit:Boten, fjern USB-kabelen, slå på Bit:Boten på nytt og se om det hjelper.*


```blocks
bitbot.setLedColor(0xFF0000)
```

### Steg 2

Du kan også slå på individuelle lys på Bit:Boten.
Til det bruker du blokken ``||bitbot.sett LED nr 0 til||``.
Fjern blokken ``||bitbot.sett alle LED til||`` fra ``||basic.ved start||``-blokken.
Du kan flytte individuelle blokker ved å holde inne **CTRL** på tastaturet mens du klikker og drar med musen.
Hent ``||bitbot.sett LED nr 0 til||``-blokken fra ``||bitbot.Bitbot/Lys||``-menyen og endre **0** til **5**.
Kopier ``||bitbot.Bitbot/Lys||`` og plasser kopien rett under originalen.
Endre **5** til **11**
Last ned det nye programmet og se hva som skjer med lysene på Bit:Boten.

```blocks
bitbot.setPixelColor(5, 0xFF0000)
bitbot.setPixelColor(11, 0xFF0000)
```

### Plasseringen av de individuelle lysene på Bit:Bot @unplugged

Som du ser er LED nummer 5 og 11 de to lysene lengst foran på Bit:Boten.
Akkurat disse to lysene er fine å bruke som retningsvisere, eller som indikatorer for de to linjesensorene som sitter på undersiden av Bit:Boten.
Lysene på venstre side av Bit:Boten er nummerert fra 0-5 (bakfra mot front), mens lysene på høyre side er nummerert 6-11 (bakfra mot front).

### Steg 3

En annen fin blokk å bruke er blokken ``||bitbot.sett LED til regnbue||``.
Fjern alle blokkene i programmet ditt fra ``||basic.ved start||``-blokken.
Hent blokken ``||bitbot.sett LED til regnbue||`` fra ``||bitbot.Bitbot/Lys||``-menyen og dra den inn i ``||basic.ved start||``-blokken.
Last ned programmet til Micro:Biten, slå på Bit:Boten og se hva som skjer.

```blocks
bitbot.ledRainbow()
```

### Endringer i lysinnstillinger på Bit:Boten @unplugged

I enkelte tilfeller vil lysene på Bit:Boten ikke slå seg på når du laster ned et program.
Ofte skyldes det at Micro:Biten fortsatt er koblet til PCen med USB-kabelen.
I utgangspunktet skal endringer i lysinnstillngene på Bit:Boten vises automatisk, men det kan noen ganger hende at det ikke skjer.
Om du vil overstyre hvordan lysendringer oppdateres, kan du bruke blokken ``||bitbot.sett oppdateringsmodus manual||``.
Dersom den er satt til **Manual** vil ingen endringer som gjelder lysene vises før du setter inn blokken ``||bitbot.vis LED-endringer||``.
Om blokken ``||bitbot.sett oppdateringsmodus manual||`` settes til **Auto** vil alle oppdateringer senere i programmet vises automatisk.
Disse funksjonene regnes som avanserte, så om du vil holde det enkelt kan du som regel bruke blokken ``||bitbot.sett LED lysstyrke 40||`` for å sikre at lysene kommer på.

### Steg 4

Du kan animere den fine regnbuen på en veldig enkel måte.
Hent blokken ``||bitbot.roter LED||`` og sett den inn i ``||basic.gjenta for alltid||``-blokken (**ikke** i ``||basic.ved start||``-blokken).
Last ned programmet til Micro:Biten, slå på Bit:Boten og se på forskjellen.

```blocks
bitbot.ledRainbow()
basic.forever(function () {
    bitbot.ledRotate()
})
```

### Steg 5

For en litt langsommere animasjon kan du sette inn en ``||basic.pause 100 ms||``-blokk i ``||basic.gjenta for alltid||``-blokken under ``||bitbot.roter LED||``.
Last ned programmet og se hvordan animasjonen endres. Du kan endre tidsverdien i ``||basic.pause||``-blokken og se hva du liker best.

```blocks
basic.forever(function () {
    bitbot.ledRotate()
    basic.pause(100)
})
```

### Steg 6

Du kan justere lysstyrken med blokken ``||bitbot.sett LED lysstyrke til 40||``.
Blokken kan også brukes dersom lysene av en eller annen grunn ikke slår seg på av seg selv når du kjører programmet ditt.
Klikk på **"40"** og juster lysstyrken med slideren.
Høyeste lysstyrkeverdi er **255**.
Er verdien **0** vil NeoPixlene være slukket.
Hent blokken ``||bitbot.sett LED lysstyrke til 40||`` fra ``||bitbot.Bitbot/Lys||`` og sett den inn i ``||basic.ved start||``-blokken, under ``||bitbot.sett LED til regnbue||``.
Velg en lysstyrke du synes er passe før du går videre.
(PS: Høyere lysstyrke tapper batteriene til Bit:Boten raskere. FireLEDene krever en del strøm.)

```blocks
bitbot.ledRainbow()
bitbot.ledBrightness(132)
```

### Steg 7

Det finnes også en annen animasjonsblokk i tillegg til ``||bitbot.roter LED||``.
Fjern ``||bitbot.roter LED||`` fra ``||basic.gjenta for alltid||``-blokken og erstatt den med ``||bitbot.flytt LED||`` fra ``||bitbot.Bitbot/Lys||``-menyen.
Last ned programmet og se hva som skjer. (Husk å koble Micro:Biten fra PCen.)

```blocks
basic.forever(function () {
    bitbot.ledShift()
    basic.pause(100)
})
```

### Hvordan flytt LED virker @unplugged

Som du så forsvinner lysene ut av rekken etter hvert når man bruker ``||bitbot.flytt LED||`` i en ``||basic.gjenta for alltid||``-blokk.
``||bitbot.flytt LED||``-kommandoen flytter hvert lys én plass oppover i LED-rekken én gang hver gang den utføres.
Når kommandoen står en ``||basic.gjenta for alltid||``-blokk flyttes alle lysene oppover i rekken helt til alle lysene forsvinner ut av rekken.
Denne funksjonen kan brukes når du vil at alle lysene gradvis skal bli borte, for eksempel for å vise tiden i en nedtelling, eller antall liv som gjenstår i en robotkamp.

### Steg 8

En måte å bruke denne kommandoen på er å flytte den inn i en løkke som gjentas et bestemt antall ganger.
Om ``||bitbot.flytt LED||``-blokken plasseres i en løkke som gjentas 12 ganger, forsvinner alle lysene akkurat ut av rekken når løkken er ferdig med gjentagelsene stopper.
Hent en ``||loops.gjenta 4 ganger||``-blokk fra ``||loops.Løkker||``-menyen og sett den inn i ``||basic.gjenta for alltid||``-blokken over de andre blokkene som allerede ligger der.
Dra de andre blokkene i ``||basic.gjenta for alltid||``-blokken inn i ``||loops.gjenta 4 ganger||``-blokken.

```blocks
basic.forever(function () {
    for (let index = 0; index < 4; index++) {
        bitbot.ledShift()
        basic.pause(100)
    }
})
```

### Steg 9

Endre **4** til **12** i ``||loops.gjenta 4 ganger||``-blokken.
Hent en ``||bitbot.sett LED til regnbue||``-blokk fra ``||bitbot.Bitbot/Lys||``-menyen og legg den inn i ``||basic.gjenta for alltid||``-blokken over ``||loops.gjenta 12 ganger||``-blokken.
Last ned programmet, koble fra USB-kabelen, slå på Bit:Boten og se hva som skjer.

```blocks
basic.forever(function () {
    bitbot.ledRainbow()
    for (let index = 0; index < 12; index++) {
        bitbot.ledShift()
        basic.pause(100)
    }
})
```

### Hvordan den siste koden virker @unplugged

Ved å legge ``||bitbot.flytt LED||``-blokken inn i en ``||loops.gjenta 12 ganger||``-blokk sørger du for at kommandoen gjentas akkurat nok ganger til at alle lysene slukker.
Når du plasserer ``||bitbot.sett LED til regnbue||``-blokken utenfor ``||loops.gjenta 12 ganger||``-blokken men inne i ``||basic.gjenta for alltid||``-blokken, vil regnbuen tennes på nytt hver gang alle lysene er slukket. 
Det gir en litt annerledes animasjon enn ``||bitbot.roter LED||``.

### Avslutning @unplugged

Gratulerer! Nå vet du det meste om hvordan du kan bruke lysene på Bitboten!
Det finnes mer avanserte måter å bruke dem på som du kan utforske selv.
En morsom mulighet er for eksempel å bruke lyssensoren på Micro:Biten til å styre lysene på Bitboten, slik at lysene kommer på når det blir mørkt.

```blocks
bitbot.setLedColor(0x000000)
basic.forever(function () {
    if (input.lightLevel() < 150) {
        bitbot.setLedColor(0xFFFFFF)
    } else {
        bitbot.setLedColor(0x000000)
    }
})
```


```package
bitbot=github:4tronix/BitBot
```

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
