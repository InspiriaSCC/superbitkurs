### @activities true

# super:bit - kodeøkt 14: Micro:Bitens lyssensor
## Lag et automatisk nattlys med Micro:Bit
### Introduksjon @unplugged

Diplayet på Micro:Biten består av 25 LED-pærer.
Micro:Bit kan også brukes til å måle lys fra omgivelsene.
I denne økten lærer du hvordan du kan bruke lyssensoren til å lage en lampe som slår seg på når det blir mørkt.

### Litt praktisk om lyssensoren @unplugged

Før du begynner å kode selve lampen, kan det være lurt å lære litt mer om lyssensoren.
Micro:Biten måler lysnivået på en skala fra 0 (helt mørkt) til 255 (fullt lys).
To Micro:Biter ved siden av hverandre måler gjerne litt forskjellige lysnivåer.
Dette skyldes måten elektroniske komponenter produseres på og er helt normalt.
Før du begynner å sette inn lysmålerverdier i koden din, lønner det seg å finne ut hvilke baseverdier du får i det rommet du befinner deg i.


### Steg 1
Hent en ``||basic.vis tall||``-blokk fra ``||basic.Basis||``-menyen og dra den inn i ``||basic.gjenta for alltid||``-blokken i arbeidsområdet ditt.
Hent en oval ``||input.lysnivå||``-blokk fra ``||input.Inndata||``-menyen og dra den inn i det hvite feltet i ``||basic.vis tall||``-blokken.
``||input.lysnivå||`` er en variabel som alltid inneholder verdien av lyssensoren til Micro:Biten.
Verdien vil hele tiden variere med lyset i omgivelsene til Micro:Biten.
Last ned programmet til Micro:Biten og sjekk hvilke verdier du får når du lar Micro:Biten ligge med skjermen opp uten at noe skygger for den, og hvilke verdier du får når du skygger for skjermen med hånden.
I eksemplet ble det målt verdiene 220 med skjermen liggende åpent under en lampe og 100 når skjermen lå i skyggen av en hånd.

```blocks
basic.forever(function () {
    // @highlight
    basic.showNumber(input.lightLevel())
})
```

### Koble til en LED-pære @unplugged
Før du går videre kan det være lurt å koble til en LED-pære.
LED-pæren kan du koble til med to ledninger med krokodilleklemmer.
Koble det korte beinet på LED-pæren til **"GND"** og det lange beinet til **"pin 0"** på Micro:Biten.

![LEDkobling](https://raw.githubusercontent.com/Yngel72/Superbit/master/static/LEDkobling.jpg)

### Steg 2

For å sjekke lyssensoren trenger du en ``||logic.hvis så ellers||``-blokk fra ``||logic.Logikk||``-menyen.
Hent en og dra den inn i ``||basic.gjenta for alltid||``-blokken i arbeidsområdet ditt.
Dersom du fortsatt har en ``||basic.vis tall||``-blokk i ``||basic.gjenta for alltid||``-blokken, dra den ut til venstre og kast den i søppelbøtta.

```blocks
basic.forever(function () {
    // @highlight
    if (true) {
    	
    } else {
    	
    }
})
```

### Valg av tallverdier @unplugged

Nå må du vurdere når du vil at LED-pæren skal slå seg på.
I eksempelkoden brukes et lysnivå som er litt høyere enn "skyggenivået" som ble målt, i dette tilfellet 100.
Det kan godt hende du må bruke andre tall.

### Steg 3

Nå skal du sjekke om lysnivået er så lavt at LED-pæren skal skrus på.
Til det trenger du en heksagonal ``||logic.0 < 0||``-blokk fra ``||logic.Logikk||``-menyen.
Dra den inn i heksagonet øverst i ``||logic.hvis så ellers||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    if (0 < 0) {
    	
    } else {
    	
    }
})
```

### Steg 4

Nå trenger du den ovale ``||input.lysnivå||``-blokken fra ``||input.Inndata||``-menyen igjen.
Hent en og dra den inn i det første hvite feltet i ``||logic.0 < 0||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    if (input.lightLevel() < 0) {
    	
    } else {
    	
    }
})
```

### Steg 5

Om du vil at LED-pæren skal slå seg på når du skygger for Micro:Bit-displayet med hånden, bør du velge å sette inn et lysnivå i ``||logic.lysnivå < 0||``-blokken som er litt høyere enn det du målte da du skygget for med hånden.
I eksemplet brukes 150, men det kan hende du må bruke et lavere eller høyere tall, avhengig av belysningen der du befinner deg.

```blocks
basic.forever(function () {
    // @highlight
    if (input.lightLevel() < 150) {
    	
    } else {
    	
    }
})
```

### Steg 6

Når lysnivået går under verdien du satte inn i ``||logic.lysnivå < 0||``-blokken, skal LED-pæren tennes.
Hent en ``||pins.skriv digital til P0 verdi 0||``-blokk fra ``||pins.Tilkoblinger||`` under **"Avansert"** og dra den inn i det første gapet i ``||logic.hvis så ellers||``-blokken.
Endre tallet **"0"** til **"1"** i det siste feltet i ``||pins.skriv digital til P0 verdi 0||``-blokken.

```blocks
basic.forever(function () {
    if (input.lightLevel() < 150) {
        // @highlight
        pins.digitalWritePin(DigitalPin.P0, 1)
    } else {
    	
    }
})
```

### Hva ``||pins.skriv digital til P0 verdi 0||`` gjør @unplugged

Blokken ``||pins.skriv digital til P0 verdi 0||`` setter 3 Volt spenning mellom en pin med nummeret du velger og GND dersom verdien er 1,
og ingen spenning mellom samme pin og GND når verdien er 0.
Dette kan du bruke til f.eks. å slå en LED-pære av eller på med.
Vær oppmerksom på at Micro:Biten ikke takler mye strøm, så ikke prøv å kjøre en motor eller noe annet strømkrevende på denne måten.
Da risikerer du å svi kretsene i Micro:Biten og ødelegge den.

### Steg 7

Når lysnivået er høyere enn vardien du satte inn i ``||logic.lysnivå < 0||``-blokken skal LED-pæren være slukket.
Kopier ``||pins.skriv digital digital til P0 verdi 0||``-blokken og dra kopien inn i det siste gapet på ``||logic.hvis så ellers||``-blokken.
Endre tallet **"1"** til **"0"** i det siste feltet i den nye ``||pins.skriv digital til P0 verdi 0||``-blokken.
Last ned programmet til Micro:Biten og sjekk at alt fungerer som det skal.

```blocks
basic.forever(function () {
    if (input.lightLevel() < 150) {
        pins.digitalWritePin(DigitalPin.P0, 1)
    } else {
        // @highlight
        pins.digitalWritePin(DigitalPin.P0, 0)
    }
})
```

### Steg 8

For litt mer tilbakemelding fra Micro:Biten kan du enten velge å vise lysmålerverdiene slik du gjorde i det første steget i denne økten.
Om du vil vise de målte lysverdiene, henter du bare en ``||basic.vis tall||`` blokk fra ``||basic.Basis||``-menyen.
Plasser den under ``||pins.skriv digital digital til P0 verdi 1||``-blokken i det øverste gapet i ``||logic.hvis så ellers||``-blokken.
Hent den ovale variabelen ``||input.lysmåler||`` fra ``||input.Inndata||``-menyen og sett den inn i det hvite feltet i ``||basic.vis tall||`` blokken.
Last ned programmet til Micro:Biten og test koden din.

```blocks
basic.forever(function () {
    if (input.lightLevel() < 150) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        // @highlight
        basic.showNumber(input.lightLevel())
    } else {
        pins.digitalWritePin(DigitalPin.P0, 0)
    }
})
```

### Forsinket slukking @unplugged

Du merket kanskje at LED-pæren fortsatte å lyse når du fjernet hånden etter den siste endringen i koden?
Blokkene vi bruker i MakeCode representerer egentlig linjer med JavaScript.
JavaScriptet leses én og én linje.
Når en kommando krever litt tid, tar det en liten stund før programmet ditt går videre.
Kommandoen ``||basic.vis tall||`` er en kommando som tar litt tid.
Programmet går ikke videre før displayet er ferdig med å vise verdien som ``||basic.vis tall||`` henter.
Siden lysverdiene her gjerne er tresifret, tar det noen sekunder før programmet går videre og slukker LED-pæren etter at du har fjernet hånden.

### Steg 9

For å vise lysverdiene når LED-pæren er slukket, kopierer du rett og slett ``||basic.vis tall||`` blokken fra det øverste gapet og plasserer kopien under ``||pins.skriv digital til P0 verdi 0||``-blokken i det nederste gapet på ``||logic.hvis så ellers||``-blokken.
Last programmet ned til Micro:Biten og test at koden fungerer.

```blocks 
basic.forever(function () {
    if (input.lightLevel() < 150) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        basic.showNumber(input.lightLevel())
    } else {
        pins.digitalWritePin(DigitalPin.P0, 0)
        // @highlight
        basic.showNumber(input.lightLevel())
    }
})
```

### Forsinket tenning og slukking @unplugged

Du merket sikkert at både slukking og tenning nå er litt forsinket.
Det skyldes akkurat det samme som tidligere.
LED-pæren må nå vente både med tenning og slokking til den tresifrede lysverdien er ferdig med å rulle over skjermen.

### Steg 10

En annen, kanskje morsommere måte å få tilbakemelding fra displayet på er å bruke symboler for dag og natt i stedet for lysverdier.
Fjern ``||basic.vis tall||`` blokkene fra programmet.
Hent en ``||basic.vis skjerm||``-blokk fra ``||basic.Basis||``-menyen og plasser den under ``||pins.skriv digital til P0 verdi 1||`` i det øverste gapet på ``||logic.hvis så ellers||``-blokken.
Tegn et månesymbol i blokken.

```blocks
basic.forever(function () {
    if (input.lightLevel() < 150) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        // @highlight
        basic.showLeds(`
            . # # # .
            . . # # #
            . . # # #
            . . # # #
            . # # # .
            `)
    } else {
        pins.digitalWritePin(DigitalPin.P0, 0)
    }
})
```

### Steg 11

Hent en ny ``||basic.vis skjerm||``-blokk fra ``||basic.Basis||``-menyen og plasser den under ``||pins.skriv digital til P0 verdi 0||`` i det nederste gapet på ``||logic.hvis så ellers||``-blokken.
Tegn et solsymbol i blokken.

```blocks
basic.forever(function () {
    if (input.lightLevel() < 150) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        basic.showLeds(`
            . # # # .
            . . # # #
            . . # # #
            . . # # #
            . # # # .
            `)
    } else {
        pins.digitalWritePin(DigitalPin.P0, 0)
        // @highlight
        basic.showLeds(`
            # . # . #
            . # # # .
            # # # # #
            . # # # .
            # . # . #
            `)
    }
})
```

### Avslutning @unplugged

Du merket kanskje at forsinkelsene for tenning og slukking ble kortere da du satte inn symbolene i stedet for tallverdiene?
Det skyldes at det krever mindre tid å tegne et symbol enn det tar å rulle et tresiffret tall over skjermen.
Lyssensoren kan brukes til mye mer enn det vi har gått gjennom her.
Du kan bruke inndata fra lyssensoren til å kontrollere Bitboten med.
Du kan for eksempel få Bitboten til å rygge når du lyser på skjermen med en lommelykt.

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>


