### @activities true

# super:bit - Kodeøkt 11: Hvordan bruke avstandssensoren til Bit:Bot
## Avstandssensoren til Bit:Bot
### Introduksjon @unplugged

Avstandssensoren som følger med i super:bit-kassen skal festes i den svart kontakten framme på Bit:Boten.
Den kan oppdage gjenstander foran Bit:Boten, slik at man kan bruke den til å unngå kollisjoner.
I denne gjennomgangen lærer du å bruke avstandssensoren til å få Bit:Boten til å unngå hindre.
Plasser sensoren i kontakten foran på Bit:Boten, slik at "øynene" peker forover.
**NB: Avstandssensoren krever omtrent 5 volt og fungerer derfor ofte dårlig med oppladbare AA-batterier i Bit:Boten.
Vanlige, alkaliske, ikke-oppladbare AA-batterier gir høyere spenning enn oppladbare, derfor anbefales de på det sterkeste her.**

![Avstandssensor](https://raw.githubusercontent.com/Yngel72/Superbit/master/static/Avstandssensor.jpg)

### Steg 1

Her bruker vi en ``||basic.gjenta for alltid||``-løkke som utgangspunkt.
I ``||basic.gjenta for alltid||``-blokken må vi ha en logisk sjekk som hele tiden måler avstanden til objekter foran roboten, og bestemmer hva som skal skje om avstanden er for liten.
Hent en ``||logic.hvis sann så ellers||``-blokk fra ``||logic.Logikk||``-menyen og plasser den inni ``||basic.gjenta for alltid||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    if (true) {
        
    } else {
        
    }
})
```

### Steg 2

I heksagonet øverst i ``||logic.hvis sann så ellers||``-blokken trenger vi en **"mindre enn"** sjekk.
Hent det lille heksagonet ``||logic.0 < 0||`` fra ``||logic.Logikk||``-menyen og plasser det i heksagonet på ``||logic.hvis sann så ellers||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    if (0 < 0) {
        
    } else {
        
    }
})
```

### Steg 3

Fra ``||bitbot.Bitbot/Sensorer og styring||`` henter du en oval ``||bitbot.les ultralydsensor som cm||``-blokk og setter den inn i det første hvite feltet i ``||logic.0 < 0||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    if (bitbot.sonar(BBPingUnit.Centimeters) < 0) {
        
    } else {
        
    }
})
```

### Steg 4

Nå må du bestemme hvilken avstand du vil at Bitboten skal reagere på. 10-15 cm pleier å være et godt utgangspunkt.
Endre "0" i det andre hvite feltet i ``||logic.0 < 0||``-blokken til den avstanden du vil teste.

```blocks
basic.forever(function () {
    // @highlight
    if (bitbot.sonar(BBPingUnit.Centimeters) < 10) {
        
    } else {
        
    }
})
```

### Steg 5

Nå skal du instruere roboten om hva den skal gjøre når den støter på et hinder.
Hent en ``||bitbot.snu til venstre med fart 60 i 400 millisekund %||``-blokk fra ``||bitbot.Bitbot/Kjøring/||``-menyen og sett den inn i det øverste gapet i ``||logic.hvis sann så ellers||``-blokken.

```blocks
basic.forever(function () {
    if (bitbot.sonar(BBPingUnit.Centimeters) < 10) {
        // @highlight
        bitbot.rotatems(BBRobotDirection.Left, 60, 400)
    } else {
        
    }
})
```

### Steg 6

Når det ikke er noe hinder foran Bit:Boten, skal den kjøre rett fram.
Hent en ``||bitbot.kjør framover med fart 60 %||``-blokk fra ``||bitbot.Bitbot/Kjøring/||``-menyen og plasser den i det andre gapet på ``||logic.hvis sann så ellers||``-blokken.
Nå gjenstår det bare å teste om avstanden på sensoren, farten på Bit:Boten og utslaget på svingingen fungerer greit for å unngå hindre.
Last ned programmet til Micro:Biten og test en liten hinderløype.
Bruk det du måtte ha av esker, kopper o.l. som hindre.
Det kan hende du må prøve og feile litt før koden fungerer bra.

```blocks
basic.forever(function () {
    if (bitbot.sonar(BBPingUnit.Centimeters) < 10) {
        // @highlight
        bitbot.rotatems(BBRobotDirection.Left, 60, 400)
    } else {
        // @highlight
        bitbot.go(BBDirection.Forward, 60)
    }
})
```

### Steg 7

Dersom du opplever at Bit:Boten ikke helt klarer å unngå hindre slik koden er nå, kan et tips være å få den til å rygge litt når den støter på et hinder.
Du kan bruke blokken ``||bitbot.kjør framover med fart 60 % i 400 ms||`` for å få Bit:Boten til å rygge.
Hent blokken ``||bitbot.kjør framover med fart 60 % i 400 ms||`` fra ``||bitbot.Bitbot/Kjøring||`` og sett den inn **over** ``||bitbot.snu til venstre med fart 60 % i 400 millisekund||``-blokken i det øverste gapet i ``||logic.hvis sann så ellers||``-blokken.
Endre ``||bitbot.framover||`` til ``||bitbot.bakover||`` og endre ``||bitbot.400 ms||`` til et tall du tror passer.
Test den nye koden og se om roboten nå er blitt flinkere til å unngå hindre.

```blocks
basic.forever(function () {
    if (bitbot.sonar(BBPingUnit.Centimeters) < 10) {
        // @highlight
        bitbot.goms(BBDirection.Reverse, 60, 400)
        bitbot.rotatems(BBRobotDirection.Left, 60, 400)
    } else {
        bitbot.go(BBDirection.Forward, 60)
    }
})
```

### Avslutning @unplugged

Det er ikke så mange linjer kode som skal til for å bruke avstandssensoren, men prøving og feiling for å få koden til å virke optimalt tar gjerne litt tid.
**Igjen: Husk at oppladbare batterier ikke fungerer særlig godt med avstandssensoren.
Bruk heller vanlige, ikke-oppladbare AA-batterier når du holder på med akkurat denne sensoren. Hvis det ikke virker, kan det hende BitBoten trenger nye batterier.**

```package
bitbot=github:4tronix/BitBot
```

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>


