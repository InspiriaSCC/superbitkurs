### @activities true

# super:bit - Kodeøkt 1: Bruk displayet
## Introduksjon
### Introduksjon @unplugged
MakeCode-vinduet består av tre deler: Til venstre ser du Micro:Bit-simulatoren som viser hva koden din gjør med Micro:Biten.
I midten er en kolonne med fargede kategorier. Her er blokkene du trenger for å bygge kode.
Til høyre finner du arbeidsområdet. Her plasserer du blokker for å bygge programmer til Micro:Biten.
Når du flytter en blokk i arbeidsområdet, følger blokkene under blokken du flytter også med.
***Du kan flytte en enkeltblokk ved å holde inn Ctrl-knappen mens du klikker og drar.***
La oss varme opp litt lett kode til å begynne med.

### La oss starte enkelt @unplugged

Vi starter med å vise litt tekst i displayet på Micro:Biten ved hjelp av MakeCode-blokker.

### Steg 1: Startblokkene @unplugged
De fleste kodeblokkene i MakeCode må legges i en startblokk for at koden skal kjøre.
Når du starter MakeCode ser du to sånne startblokker på arbeidsbordet ditt. Du trenger ikke å bruke begge.
Mange blokker vil være grå på skjermen om de legges utenfor en startblokk. Det betyr at de ikke er en del av et program, og at kommandoene i disse blokkene ikke utføres.


### Steg 2: Tekst i en uendelig løkke
Å vise tekst er en ``||Basic.Basis||``-funksjon i MakeCode.
Klikk på ``||Basic.Basis||`` for å åpne ``||Basic.Basis||``menyen og hent ut blokken ``||Basic.vis tekst||``.
Plasser blokken i ``||Basic.gjenta for alltid||``-blokken på arbeidsbordet. Endre teksten inni blokken til hva du vil.
Når du har skrevet inn litt tekst, kobler du Micro:Biten til enheten du jobber på og trykker på **"Last ned"** nederst til venstre på skjermen.
Vent til lyset på baksiden av Micro:Biten har sluttet å blinke.
Siden displayet bare er 5x5 pixler, vil teksten rulle forbi i displayet.

```blocks

basic.forever(function () {
    basic.showString("Hello!")
})
```

### Forskjellen på "ved start" og "gjenta for alltid" @unplugged

Når du plasserer blokker i en ``||Basic.gjenta for alltid||``-blokk vil koden gjentas så lenge Micro:Biten er på.
``||Basic.ved start||``-blokken kjører koden som ligger i den en gang, og så stopper den.
``||basic.ved start||`` er en viktig blokk.
I den definerer du variabler som skal brukes flere steder i programmet (globale variabler), og der setter du opp startkriteriene i koden.
``||Basic.gjenta for alltid||``-løkken er fin for kode som skal kjøre igjen og igjen, som for eksempel tekst som skal rulle over displayet gjentatte ganger.

### Steg 3: Tekst som vises bare én gang

Klikk og dra tekstblokken din fra ``||Basic.gjenta for alltid||``-blokken og inn i ``||Basic.ved start||``-blokken.
Last ned progreammet til Micro:Biten og observer hva som skjer.

```blocks
basic.showString("Hello!")
```

### Steg 4: Vise tall

MakeCode behandler tall og tekststrenger forskjellig. Du kan vise tall som tekst, men MakeCode kan ikke bruke tall definert som tekst til matematiske operasjoner.
Før du går videre må du fjerne ``||Basic.vis tekst||`` fra ``||Basic.ved start||``.
For å vise et tall må du hente blokken ``||basic.vis tall||`` fra ``||basic.Basis||``-menyen.
Sett blokken inn i ``||basic.ved start||``, skriv inn et tall og last ned programmet til Micro:Biten.

```blocks
basic.showNumber(8)
```

### Steg 5: Vise ikoner

Du kan også vise ferdige ikoner i displayet.
Til det bruker du ``||basic.vis ikon||`` fra ``||basic.Basis||``-menyen.
Fjern ``||Basic.vis tall||`` fra ``||Basic.ved start||`` og sett inn en ``||basic.vis ikon||``.
Klikk på den lille hvite pilen til høyre for hjerteikonet for å velge ikon.

```blocks
basic.showIcon(IconNames.Heart)
```

### Steg 6: Lage egne bilder

Fjern ``||basic.vis ikon||``-blokken fra koden din før du går videre.
Du kan også tegne dine egne bilder på 5x5 piksler.
Da bruker du ``||basic.vis skjerm||``-blokken fra ``||basic.Basis||``-menyen.
Hent den og sett den inn i ``||basic.ved start||``-blokken.
Hver av de 25 rutene på denne blokken representerer en LED på displayet.
Klikk på ruter for å slå lyset av og på.
Klarer du å tegne et smilefjes?

```blocks
basic.showLeds(`
    . . . . .
    . # . # .
    . . . . .
    # . . . #
    . # # # .
    `)
```

### Animasjoner @unplugged

Om du vil lage animasjoner på displayet, kan du bruke det du har lært til nå.
I tillegg kan det være lurt å ta med blokken ``||basic.pause (ms)||`` fra ``||basic.Basis||``-menyen.
``||basic.pause (ms)||`` brukes for sikre at man rekker å oppfatte et bilde i displayet før programmet går videre.

### Steg 7: Animasjoner

Fjern koden din fra arbeidsområdet.
Hent en ny ``||Basic.gjenta for alltid||``-blokk fra ``||basic.Basis||``-menyen.
Hent en ny ``||basic.vis skjerm||``-blokk fra ``||basic.Basis||``-menyen og tegn det første bildet i animasjonen din.
I eksemplet lager vi et bankende hjerte.

```blocks
basic.forever(function () {
    basic.showLeds(`
        . # . # .
        # # # # #
        # # # # #
        . # # # .
        . . # . .
        `)
})
```

### Steg 8: Animasjoner

Før du setter inn neste bilde i animasjonen bør du pause programmet lenge nok til at du rekker å oppfatte det første bildet.
Hent en ``||basic.pause (ms)||``-blokk fra ``||basic.Basis||``-menyen og sett den inn under ``||basic.vis skjerm||``-blokken.

```blocks
basic.forever(function () {
    basic.showLeds(`
        . # . # .
        # # # # #
        # # # # #
        . # # # .
        . . # . .
        `)
    basic.pause(100)
})
```

### Steg 9: Fullfør animasjonen

Sett inn flere ``||basic.vis skjerm||``-blokker med små endringer under den første.
Husk å sette en pauseblokk mellom bildene og etter det siste bildet i ``||Basic.gjenta for alltid||``-blokken.
Du kan kopiere en blokk ved å høyreklikke på den og velge **"Lag kopi"** fra rullegardinmenyen som dukker opp.
Dette gjør det enklere når du skal lage små endringer mellom bildene i animasjonen.
Juster tiden mellom blokkene slik at animasjonen vises slik du foretrekker.

```blocks
basic.forever(function () {
    basic.showLeds(`
        . # . # .
        # # # # #
        # # # # #
        . # # # .
        . . # . .
        `)
    basic.pause(100)
    basic.showLeds(`
        . . . . .
        . # . # .
        . # # # .
        . . # . .
        . . . . .
        `)
    basic.pause(100)
    basic.showLeds(`
        . . . . .
        . . . . .
        . . # . .
        . . . . .
        . . . . .
        `)
    basic.pause(100)
    basic.showLeds(`
        . . . . .
        . # . # .
        . # # # .
        . . # . .
        . . . . .
        `)
    basic.pause(100)
})
```


### Det var det!
Godt jobba! Nå har du lært de mest grunnleggende blokkene som brukes til å vise tall, tekst og bilder på displayet.
I neste runde skal vi se nærmere på hvordan vi kan bruke det du har lært til å lage en elektronisk terning.

* for PXT/microbit
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
