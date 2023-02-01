### @activities true

# super:bit - Kodeøkt 18: Mottaker til radiostyrt servo
## Bruk servoer til å lage radiostyrt bevegelse - mottager
### Introduksjon @unplugged

I denne gjennomgangen lærer du å programmere en radiomottager som styrer en servo.


### Tilkoblinger @unplugged

Rett foran hjulet på Bit:Botens ventre side finner du to kontakter med 3 pinner.
Dette er servokontaktene til Bit:Boten.
Det fremste paret med pinner er merket P1 og P2.
P1 og P2 er signalutgangene fra Micro:Biten som brukes til å kontrollere servoer.
De to neste parene er merket 5V og GND.
5V gir 5 volts positiv spenning mot GND, som er jordkontaktene.

### Steg 1 @unplugged

Monter en hvit, enkel plastarm til en **180-graderservo** som vist på bildet.
Koble **180-graderservoen** til rekken av kontakter som forklart og vist.
Servoene som følger med super:bit har tre ledninger ut, en brun, en rød og en oransje.
Brun er jordledningen, den skal kobles til GND.
Rød er "+"-ledningen som skal kobles til 5V.
Oransje er signalledningen som skal kobles til P1 eller P2.
Plasser kontakten til servoen på pinnene ved P1 slik at oransje ledning treffer P1, rød ledning treffer 5V og brun ledning treffer GND.

![Servokobling](https://raw.githubusercontent.com/Yngel72/Superbit/master/static/Servokobling.jpg)

### Steg 2

Bommen du skal åpne og lukke med radiostyring må monteres på den hvite plastarmen.
Bruk tape eller heftemasse til å feste et stripe bølgepapp eller en ispinne til armen, eller finn noe annet i et lett materiale som kan være bom.
Fest selve servoen til et fast underlag, en pappskive eller liknende ved hjelp av tape eller heftemasse.
Normalt skal du kunne feste servoen liggende flatt med klistremerket opp dersom du vil at bommen skal åpnes vertikalt.
Ønsker du at bommen skal åpnes horisontalt, fester du den slik at den står med bommen liggende oppå servoen.

### Steg 3

Siden radiostyring krever at Micro:biten bruker radiosignaler, må du begynne med å aktivere radioen og velge en kanal.
Det gør du med blokken ``||radio.radio sett gruppe||`` som du finner i ``||radio.Radio||``-menyen.
Hent en ``||radio.radio sett gruppe||`` og plasser den i ``||basic.ved start||``-blokken.
Sett radioen til ``||radio.gruppe 1||`` dersom du brukte det samme tallene som i eksempelet vårt da du programmerte senderen.

```blocks
// @highlight
radio.setGroup(1)
```

### Steg 4

For å se at programmet kjører, er det lurt å vise et bilde eller et ikon i displayet.
Hent en ``||basic.vis skjerm||``-blokk fra ``||basic.basis||``-menyen og tegn et bilde, eller bruk blokken ``||basic.vis ikon||`` og velg et ikon du synes passer.
I eksemplet har vi forsøkt å tegne et bilde av en lukket bom.

```blocks
radio.setGroup(1)
// @highlight
basic.showLeds(`
    . . . . .
    . . . . .
    . . . . .
    # # # # #
    . # . . .
    `)
```

### Steg 5

Siden senderen bare sender tall, må mottagerprogrammet kjøre i en ``||radio.når radio mottar receivedNumber||``-blokk fra ``||radio.Radio||``-menyen.
Legg en ``||logic.hvis sann så ellers||``-blokk fra ``||logic.Logikk||``-menyen inn i ``||radio.når radio mottar receivedNumber||``-blokken.

```blocks
radio.onReceivedString(function (receivedNumber) {
    // @highlight
    if (true) {
    	
    } else {
    	
    }
})
```

### Steg 6

Siden senderen sender et tall til mottageren, må vi bruke logisk sjekk for tall i heksagonene i ``||logic.hvis sann så ellers||``-blokken.
Hent en ``||logic.0 = 0||`` fra ``||logic.Logikk||``-menyen og dra den inn i det øverste heksagonet i ``||logic.hvis sann så ellers||``-blokken.

```blocks
radio.onReceivedString(function (receivedNumber) {
    // @highlight
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

### Logisk sjekk med 2 tall @unplugged

Du trenger å gjøre en logisk sjekk for hvert av tallene radiosenderen sender ut.
I dette eksempelet skal bommen være lukket dersom senderen sender tallet 0. Er tallet som blir sendt 1, skal bommen åpnes.
I den logiske sjekken antar vi at bommen er lukket i utgangspunktet.
Vi antar også at bommen er lukket når utslaget på servoen er 0 grader, og at bommen er åpen når utslaget på servoen er 90 grader.
Du blir nødt til å sjekke hvordan servoen og bommen din står når servoen står på 0 og 90 grader etter at du er ferdig med programmeringen av mottageren.
Juster bommens posisjon ved å løfte den hvite armen forsiktig av tannhjulet på servoen når utslaget er 0 grader, og sett så armen og bommen tilbake i riktig posisjon.
Kontroller så at servoen og bommen slår ut riktig vei når posisjonen er 90 grader.

### Steg 7

Dra den røde variabelen ``||variables.receivedNumber||`` inn i det første hvite feltet i ``||logic.0 = 0||``-heksagonet.
Skriv inn "1" i det andre hvite feltet i ``||logic.0 = 0||``-heksagonet.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    // @highlight
    if (receivedNumber == 1) {
    	
    } else {
    	
    }
})
```

### Steg 8

Hent en ``||bitbot.sett servo P1 til 90 grader||``-blokk fra ``||bitbot.Bitbot/Sensorer og styring||`` og dra den inn i det øverste gapet i ``||logic.hvis sann så ellers||``-blokken.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 1) {
        // @highlight
        bitbot.bbSetServo(BBServos.P1, 90)
    } else {
    	
    }
})
```

### Steg 9

Kopier ``||basic.vis skjerm||``-blokk fra ``||basic.ved start||``-blokken og endre den så den viser en åpen bom, eller et annet ikon om du valgte å bruke ``||basic.vis ikon||``-blokken.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 1) {
        bitbot.bbSetServo(BBServos.P1, 90)
        // @highlight
        basic.showLeds(`
            . . . . #
            . . . # .
            . . # . .
            . # . . .
            # # . . .
            `)
    } else {
    	
    }
})
```


### Steg 10

Trykk på det lille ***"+"***-tegnet nederst i venstre hjørne av ``||logic.hvis sann så ellers||``-blokken.
Det dukker nå opp et nytt heksagon og et nytt gap.
Kopier ``||logic.receivedNumber = 1||``-heksagonet fra øverst i ``||logic.hvis sann så ellers||``-blokken og plasser det i det nye heksagonale feltet.
Endre ``||logic.1||`` til ``||logic.0||``.
Trykk på det lille***"-"***-tegnet til høyre i den nest nederste armen til ``||logic.hvis sann så ellers||``-blokken, slik at det nederste gapet lukker seg.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    // @highlight
    if (receivedNumber == 1) {
        bitbot.bbSetServo(BBServos.P1, 90)
        basic.showLeds(`
            . . . . #
            . . . # .
            . . # . .
            . # . . .
            # # . . .
            `)
    } else if (receivedNumber == 0) {
    	
    }
})
```


### Steg 11



Kopier ``||bitbot.sett servo P1 til 90 grader||``-blokken og legg kopien i det andre gapet på ``||logic.hvis sann så ellers||``-blokken.
Endre ``||bitbot.90 grader||`` til ``||bitbot.0 grader||``

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 1) {
        bitbot.bbSetServo(BBServos.P1, 90)
        basic.showLeds(`
            . . . . #
            . . . # .
            . . # . .
            . # . . .
            # # . . .
            `)
    } else if (receivedNumber == 0) {
        // @highlight
        bitbot.bbSetServo(BBServos.P1, 0)
    }
})
```

### Steg 12

Kopier ``||basic.vis skjerm||``-blokken fra ``||basic.ved start||``-blokken og plasser kopien under ``||bitbot.sett servo P1 til 0 grader||`` i ``||logic.hvis sann så ellers||``-blokken.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 1) {
        bitbot.bbSetServo(BBServos.P1, 90)
        basic.showLeds(`
            . . . . #
            . . . # .
            . . # . .
            . # . . .
            # # . . .
            `)
    } else if (receivedNumber == 0) {
        bitbot.bbSetServo(BBServos.P1, 0)
        // @highlight
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            . # . . .
            `)
    }
})
```

### Avslutning

Last ned programmet til Micro:Biten som skal være mottager og plasser den i Bit:Boten du koblet servoen til.
Nå kan du teste den radiostyrte bommen din ved å trykke på "A"- eller "B"-knappen på radiosenderen du programmerte i forrige kodeøkt.



```package
bitbot=github:4tronix/BitBot
```

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
