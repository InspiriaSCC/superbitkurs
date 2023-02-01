### @activities true

# super:bit - Kodeøkt 13: Micro:Bitens termometer
## Mål temperatur med Micro:Bit
### Introduksjon @unplugged

Micro:Bit har et innebygget termometer som overvåker temperaturen til hovedprosessoren.
Det har du tilgang på for å hente ut temperaturmålinger.
Heldigvis blir prosessoren sjelden særlig varmere enn omgivelsene, derfor gir termometeret en grei ganske temperaturmåling.
I denne økten lærer du hvordan du kan bruke temperaturmåleren til Micro:Bit.

### Steg 1

Først trenger du blokken som får displayet til å vise et tall.
Hent en ``||basic.vis tall||``-blokk fra ``||basic.Basis||``-menyen og plasser den i ``||basic.gjenta for alltid||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    basic.showNumber(0)
})
```

### Steg 2

Temperaturmålingen befinner seg i ``||input.Inndata||``-menyen. Der finner du en oval blokk som heter ``||input.temperatur (°C)||``.
Hent ``||input.temperatur (°C)||``-blokken og dra den inn i det hvite feltet i ``||basic.vis tall||``-blokken.
Last programmet ned til Micro:Biten og sjekk temperaturen i rommet.

```blocks
basic.forever(function () {
    // @highlight
    basic.showNumber(input.temperature())
})
```

### Kalibrering av termometeret @unplugged

Prosessoren til Micro:Bit vil normalt være en anelse varmere enn omgivelsene når den jobber.
Som regel er det ikke snakk om mer enn 1-4 grader forskjell.
Om du vil, kan du bruke et nøyaktig termometer for å kalibrere temperaturmålingene.
I eksemplet som kommer nå viste vårt nøyaktige termometer 2 grader lavere temperatur enn det microbiten viste.
Nå skal du kalibrere Micro:Biten i koden, slik at den viser mer nøyaktig temperatur.

### Steg 3

Dra den ovale ``||input.temperatur (°C)||``-blokken ut av ``||basic.vis tall||``-blokken og plasser den i arbeidsområdet ved siden av koden.
Hent en oval ``||math.0 - 0||``-blokk fra ``||math.Matematikk||``-menyen og dra den inn i det hvite feltet i ``||basic.vis tall||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    basic.showNumber(0 - 0)
})
```

### Steg 4

Dra den ovale ``||input.temperatur (°C)||``-blokken fra arbeidsområdet inn i det første hvite feltet i ``||math.0 - 0||``-blokken.
Endre 0 til 2 i det andre hvite feltet i ``||math.0 - 0||``-blokken.
Last programmet ditt ned til Micro:Biten og sjekk at kalibreringen virker.

```blocks
basic.forever(function () {
    // @highlight
    basic.showNumber(input.temperature() - 2)
})
```

### Temperaturvakt @unplugged

Om du kobler til en buzzer eller en høyttaler kan du få Micro:Biten til å gi lyd dersom temperaturen går utenfor temperaturgrensene du setter i programmet.
Buzzeren som fulgte med Superbitsettet må kobles i riktig retning, og skal kobles med det korte beinet til GND på Micro:Biten og det lange beinet merket med "+" til pin 0.
Om du bruker en høyttaler, skal den kobles med en ledning til GND og en ledning til pin 0.
Høyttalere fungerer like fint i begge retninger med Micro:Bit, så polaritet er ikke noe tema når det gjelder dem.
Til den neste delen trenger du en buzzer og to ledninger med krokodilleklemmer.
Nå skal du lage en temperaturvakt.

![Buzzerkobling](https://raw.githubusercontent.com/Yngel72/Superbit/master/static/Buzzerkobling2.jpg)

### Steg 5

Fjern ``||basic.vis tall||``-blokken fra forrige steg fra ``||basic.gjenta for alltid||``-blokken i koden din.
Koble til buzzeren som forklart på bildet i forrige trinn, om du ikke allerede har gjort det.
For å lage en temperaturvakt trenger du aller først en logisk sjekk.
Hent en ``||logic.hvis sann så ellers||``-blokk fra ``||logic.Logikk||``-menyen og dra den inn i ``||basic.gjenta for alltid||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    if (true) {
    	
    } else {
    	
    }
})
```

### Steg 6

Hent en ``||logic.0 < 0||``-blokk fra ``||logic.Logikk||``-menyen og plasser den i heksagonet øverst i ``||logic.hvis sann så ellers||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    if (0 < 0) {
    	
    } else {
    	
    }
})
```

### Steg 7

Hent den ovale ``||input.temperatur (°C)||``-blokken fra ``||input.Inndata||``-menyen og plasser den i det første hvite feltet i ``||logic.0 < 0||``-blokken.
Snu **"<"** til **">"** ved å trykke på den lille, hvite pilen til høyre for **"<"** og velg **">"** fra rullegardinmenyen.

```blocks
basic.forever(function () {
    // @highlight
    if (input.temperature() > 0) {
    	
    } else {
    	
    }
})
```

### Steg 8

For å teste at alarmen din fungerer, er det lurt å sette maksimumtemperaturen alarmen skal utløses på til 4-5 grader over temperaturen Micro:Biten viser til vanlig.
I eksemplet ble det brukt en Micro:Bit som viste 23 °C når den ikke ble påvirket av noe varmt i nærheten.
Vi valgte derfor å sette makstemperaturen til 27 grader.
Skriv inn din ønskede makstemperatur i det ledige feltet i ``||logic.temperatur (°C) > 0||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    if (input.temperature() > 27) {
    	
    } else {
    	
    }
})
```

### Steg 9

Nå trenger du en alarmlyd.
Til dette eksemplet er det greit å bare bruke en enkelt tone som spilles i et taktslag.
Hent blokken ``||music.spill tone midtre C i et taktslag||`` fra ``||music.Musikk||``-menyen og dra den inn i det første gapet i ``||logic.hvis sann så ellers||``-blokken.

```blocks
basic.forever(function () {
    if (input.temperature() > 27) {
        // @highlight
        music.playTone(262, music.beat(BeatFraction.Whole))
    } else {
    	
    }
})
```

### Steg 10

Det kan være greit at Micro:Biten viser temperaturen både før og etter at alarmen går, slik at du ser at programmet fungerer.
Hent blokken ``||basic.vis tall||`` fra ``||basic.Basis||``-menyen og plasser den under ``||music.spill tone midtre C i et taktslag||``-blokken.
Kopier den ovale ``||input.temperatur (°C)||``-blokken og plasser kopien i det hvite feltet i ``||basic.vis tall||``-blokken.

```blocks
basic.forever(function () {
    if (input.temperature() > 27) {
        music.playTone(262, music.beat(BeatFraction.Whole))
        // @highlight
        basic.showNumber(input.temperature())
    } else {
    	
    }
})
```

### Hvor måles temperaturen? @unplugged

Termometeret på Micro;Biten sitter i hovedprosessoren på baksiden av Micro:Biten.
For å heve/senke temperaturen må du påvirke selve prosessoren.
Om du trykker en finger mot prosessoren, vil temperaturen som regel nærme seg 28-30 grader.

![Prosessor](https://raw.githubusercontent.com/Yngel72/Superbit/master/static/Prosessor2.png))

### Steg 11

Kopier ``||basic.vis tall||`` ``||input.temperatur (°C)||``-blokken og plasser kopien i det siste gapet i ``||logic.hvis sann så ellers||``-blokken.
Nå kan du se temperaturen både før, under og etter at alarmen går.
Last programmet ned til Micro:Biten og se om du klarer å utløse alarmen ved å holde en finger på prosessoren så temperaturen stiger.

```blocks
basic.forever(function () {
    if (input.temperature() > 27) {
        music.playTone(262, music.beat(BeatFraction.Whole))
        basic.showNumber(input.temperature())
    } else {
        // @highlight
        basic.showNumber(input.temperature())
    }
})
```

### Steg 12

Om programmet fungerte som det skulle, kan du nå legge til en frostvakt i samme program.
Da må du starte med å utvide ``||logic.hvis sann så ellers||``-blokken.
Klikk på det lille **"+"**-tegnet nederst til venstre i blokken for å utvide den.

```blocks
basic.forever(function () {
    // @highlight
    if (input.temperature() > 27) {
        music.playTone(262, music.beat(BeatFraction.Whole))
        basic.showNumber(input.temperature())
    } else if (false) {
    	
    } else {
        basic.showNumber(input.temperature())
    }
})
```

### Steg 13

Kopier den heksagonale blokken ``||logic.temperatur (°C) > 0||`` fra det øverste heksagonet i ``||logic.hvis sann så ellers||``-blokken og plasser den i det ledige heksagonet under.
Snu **">"** til **"<"** ved å trykke på den lille, hvite pilen til høyre for **">"** og velg **"<"** fra rullegardinmenyen.
Endre makstemperaturen til minimumstemperaturen du ønsker.
I eksemplet valgte vi 24 °C bare for lett å kunne teste at programmet fungerte.

```blocks
basic.forever(function () {
    // @highlight
    if (input.temperature() > 27) {
        music.playTone(262, music.beat(BeatFraction.Whole))
        basic.showNumber(input.temperature())
    } else if (input.temperature() < 24) {
    	
    } else {
        basic.showNumber(input.temperature())
    }
})
```

### Steg 14

Kopier blokken ``||music.spill tone midtre C i et taktslag||`` og plasser den i det midtre gapet på ``||logic.hvis sann så ellers||``-blokken.
Klikk på **"midtre C"** og velg en annen tone.
I eksemplet valgte vi **"lav C"**.

```blocks
basic.forever(function () {
    if (input.temperature() > 27) {
        music.playTone(262, music.beat(BeatFraction.Whole))
        basic.showNumber(input.temperature())
    } else if (input.temperature() < 24) {
        // @highlight
        music.playTone(131, music.beat(BeatFraction.Whole))
    } else {
        basic.showNumber(input.temperature())
    }
})
```

### Steg 15

Kopier en ``||basic.vis tall||`` ``||input.temperatur (°C)||``-blokk og plasser kopien i det midtre gapet på ``||logic.hvis sann så ellers||``-blokken, under ``||music.spill tone lav C i et taktslag||``, slik at temperaturen vises når alarmen for nedre temperaturgrense går.
Sett nedre temperaturgrense til noe litt under romtemperatur, i dette tilfellet bruker vi 20°C. 
Nå kan laste ned programmet til Micro:Biten og teste at det fungerer.
Bruk gjerne en finger på hovedprosessoren for å teste at alarmen slår ut ved makstemperatur.
Minimumstemperaturen kan du teste ved å holde hovedprosessoren mot siden av et glass med kaldt vann, eller mot en tett plastpose med isbiter.

```blocks
basic.forever(function () {
    if (input.temperature() > 27) {
        music.playTone(262, music.beat(BeatFraction.Whole))
        basic.showNumber(input.temperature())
    } else if (input.temperature() < 20) {
        music.playTone(131, music.beat(BeatFraction.Whole))
        // @highlight
        basic.showNumber(input.temperature())
    } else {
        basic.showNumber(input.temperature())
    }
})
```

### Avslutning @unplugged

Det var det for denne økten. Nå vet du hvordan du bruker temperturmåleren på Micro:Bit.

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
