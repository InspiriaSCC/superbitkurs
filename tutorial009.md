### @activities true

# super:bit - Kodeøkt 8: Hvordan bruke linjesensoren til Bit:Bot
## Linjesensoren til Bitbot
### Introduksjon @unplugged

På undersiden av Bit:Boten, på hver sin side rett bak stålkula framme i snuten, sitter det fire små, svarte knotter.
Dette er linjesensoren til Bit:Boten.
Linjesensoren er en lyssensor som leser kontraster i underlaget, og den kan brukes til å få roboten til å følge en linje.
I denne gjennomgangen lærer du hvordan du bruker linjesensoren.

### Steg 1

Linjesensorkoden bygger du i en ``||basic.gjenta for alltid||``-blokk.
Hent en ``||logic.hvis sann så ellers||``-blokk fra ``||logic.Logikk||``-menyen og dra den inn i ``||basic.gjenta for alltid||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    if (true) {
    	
    } else {
    	
    }
})
```

### Steg 2

Hent en heksagonal ``||logic.0 = 0||``-blokk fra ``||logic.Logikk||``-menyen og dra den inn i heksagonet øverst i ``||logic.hvis sann så ellers||``-blokken

```blocks
basic.forever(function () {
    // @highlight
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

### Steg 3

Hent en oval ``||bitbot.venstre linjesensor||``-blokk fra ``||bitbot.Bitbot/Sensorer og styring||`` og dra den inn i det første hvite feltet i ``||logic.0 = 0||``-blokken.
Endre "0" i det andre hvite feltet til "1".

```blocks
basic.forever(function () {
    // @highlight
    if (bitbot.readLine(BBLineSensor.Left) == 1) {
    	
    } else {
    	
    }
})
```

### Hvordan virker linjesensoren @unplugged

Når linjesensoren befinner seg over et lyst underlag, sender den ikke noe signal til Micro:Bit-hjernen.
Da leser Micro:Biten signalet som 0.
Dersom linjesensoren beveger seg over et underlag som plutselig er mørkere, sender den ut et signal.
Det leser Micro:Biten som 1.
I koden har du så langt fortalt roboten at når venstre linjesensor kommer over noe som er mørkt, så skal det skje noe.
Siden det mørke underlaget her vil være den svarte linjen roboten skal følge, må vi be roboten om å svinge mot venstre, så ikke venstre linjesensor krysser linjen helt og roboten mister linjen.

### Steg 4

Hent en ``||bitbot.snu til venstre med fart 60 %||``-blokk fra ``||bitbot.Bitbot/Kjøring||`` og dra den inn i det øverste gapet på ``||logic.hvis sann så ellers||``-blokken.

```blocks
basic.forever(function () {
    if (bitbot.readLine(BBLineSensor.Left) == 1) {
        // @highlight
        bitbot.rotate(BBRobotDirection.Left, 60)
    } else {
    	
    }
})
```

### Steg 5

Trykk på det lille "+"-tegnet nederst til høyre i ``||logic.hvis sann så ellers||``-blokken så du får et nytt gap og et nytt heksagon.
Kopier hele ``||logic.venstre linjesensor = 1||``-heksagonet fra øverst i ``||logic.hvis sann så ellers||``-blokken og sett det inn i det nye heksagonet du nettop lagde.
Endre ``||bitbot.venstre||`` til ``||bitbot.høyre||`` i den nye heksagonblokken.

```blocks
basic.forever(function () {
    if (bitbot.readLine(BBLineSensor.Left) == 1) {
        bitbot.rotate(BBRobotDirection.Left, 60)
    } else if (bitbot.readLine(BBLineSensor.Right) == 1) {
    	
    } else {
    	
    }
})
```

### Steg 6

Kopier blokken ``||bitbot.snu til venstre med fart 60 %||`` fra det øverste gapet i ``||logic.hvis sann så ellers||``-blokken og sett kopien inn i neste gap.
Endre ``||bitbot.venstre||`` til ``||bitbot.høyre||`` i ``||bitbot.snu til venstre med fart 60 %||``-blokken.

```blocks
basic.forever(function () {
    if (bitbot.readLine(BBLineSensor.Left) == 1) {
        bitbot.rotate(BBRobotDirection.Left, 60)
    } else if (bitbot.readLine(BBLineSensor.Right) == 1) {
        bitbot.rotate(BBRobotDirection.Right, 60)
    } else {
    	
    }
})
```

### Steg 7

Når ingen av sensorene ser den svarte stripa, betyr det at roboten er midt over den.
Da vil vi at roboten skal kjøre rett framover, så i det siste gapet plasserer du en ``||bitbot.kjør framover med fart 60 %||``-blokk fra ``||bitbot.Bitbot/Kjøring||``-menyen.
Etter dette kan du laste ned koden til Micro:Biten og teste koden i Bit:Boten.
60 % fart er ganske raskt, og alt for raskt for kjøring med linjesensor.
Sett ned farten på både framoverkjøring og svinging til et sted mellom 10 og 30. Her må du prøve deg fram.

```blocks
basic.forever(function () {
    if (bitbot.readLine(BBLineSensor.Left) == 1) {
        bitbot.rotate(BBRobotDirection.Left, 60)
    } else if (bitbot.readLine(BBLineSensor.Right) == 1) {
        bitbot.rotate(BBRobotDirection.Right, 60)
    } else {
    	bitbot.go(BBDirection.Forward, 60)
    }
})
```

### Retningsvisere @unplugged

Som en tydelig visuell kontroll på at linjesensorene gjør det de skal, kan du legge til retningsvisere på roboten.
Bit:Boten har til sammen 12 FireLEDs på de to hornene på siden, 6 på hvert horn.
FireLEDs, eller NeoPixler som de ofte kalles, er programmerbare RGB-LEDs, og Bit:Botens FireLEDs er nummerert 0-11.
FireLED nummer 5 (venstre side) og 11 (høyre side) er de to fremste av dem.
Disse to er fine å bruke som retningsvisere eller indikatorer på at linjesensorene sender signal.
I det neste steget lærer du å lage retningsvisere på Bit:Boten.

### Steg 8

Hent blokken ``||bitbot.sett LED nr 0 til [rød]||`` fra menyen ``||bitbot.Bitbot/Lys||`` og plasser den over ``||bitbot.snu til venstre med fart 60 %||``-blokken i det øverste gapet på ``||logic.hvis sann så ellers||``-blokken.
Endre "0" til "5", siden FireLED nummer 5 sitter fremst på venstre horn, og Bit:Boten skal svinge til venstre.
Du kan godt la fargen være rød, som er standardfargen for blokken.

```blocks
basic.forever(function () {
    if (bitbot.readLine(BBLineSensor.Left) == 1) {
        bitbot.setPixelColor(5, 0xFF0000)
        bitbot.rotate(BBRobotDirection.Left, 60)
    } else if (bitbot.readLine(BBLineSensor.Right) == 1) {
        bitbot.rotate(BBRobotDirection.Right, 60)
    } else {
        bitbot.go(BBDirection.Forward, 60)
    }
})
```

### Steg 9
Kopier blokken ``||bitbot.sett LED nr 5 til [rød]||`` og plasser kopien rett under originalen.
Endre "5" til "11" og rød til svart. Dette sørger for at LED nummer 11 slukker.

```blocks
basic.forever(function () {
    if (bitbot.readLine(BBLineSensor.Left) == 1) {
        bitbot.setPixelColor(5, 0xFF0000)
        bitbot.setPixelColor(11, 0x000000)
        bitbot.rotate(BBRobotDirection.Left, 60)
    } else if (bitbot.readLine(BBLineSensor.Right) == 1) {
        bitbot.rotate(BBRobotDirection.Right, 60)
    } else {
        bitbot.go(BBDirection.Forward, 60)
    }
})
```

### Steg 10

Kopier de to blokkene ``||bitbot.sett LED nr 5 til [rød]||`` og ``||bitbot.sett LED nr 11 til [svart]||`` og plasser kopiene i det neste gapet i ``||logic.hvis sann så ellers||``-blokken, over blokken ``||bitbot.snu til høyre med fart 60 %||``.

```blocks
basic.forever(function () {
    if (bitbot.readLine(BBLineSensor.Left) == 1) {
        bitbot.setPixelColor(5, 0xFF0000)
        bitbot.setPixelColor(11, 0x000000)
        bitbot.rotate(BBRobotDirection.Left, 60)
    } else if (bitbot.readLine(BBLineSensor.Right) == 1) {
        bitbot.setPixelColor(5, 0xFF0000)
        bitbot.setPixelColor(11, 0x000000)
        bitbot.rotate(BBRobotDirection.Right, 60)
    } else {
        bitbot.go(BBDirection.Forward, 60)
    }
})
```

### Steg 11

Endre blokkene du plasserte i forrige steg så det står ``||bitbot.sett LED nr 5 til [svart]||`` og ``||bitbot.sett LED nr 11 til [rød]||`` i blokkene over ``||bitbot.snu til høyre med fart 60 %||``-blokken.

```blocks
basic.forever(function () {
    if (bitbot.readLine(BBLineSensor.Left) == 1) {
        bitbot.setPixelColor(5, 0xFF0000)
        bitbot.setPixelColor(11, 0x000000)
        bitbot.rotate(BBRobotDirection.Left, 60)
    } else if (bitbot.readLine(BBLineSensor.Right) == 1) {
        bitbot.setPixelColor(5, 0x000000)
        bitbot.setPixelColor(11, 0xFF0000)
        bitbot.rotate(BBRobotDirection.Right, 60)
    } else {
        bitbot.go(BBDirection.Forward, 60)
    }
})
```

### Steg 12
Til slutt kan du la begge FireLEDene lyse grønt nå Bit:Boten kjører rett fram.
Kopier blokkene ``||bitbot.sett LED nr 5 til [svart]||`` og ``||bitbot.sett LED nr 11 til [rød]||`` og plasser kopiene over blokken ``||bitbot.kjør framover med fart 60 %||`` i det siste gapet.
Endre blokkene så de viser ``||bitbot.sett LED nr 5 til [grønn]||`` og ``||bitbot.sett LED nr 11 til [grønn]||``

```blocks
basic.forever(function () {
    if (bitbot.readLine(BBLineSensor.Left) == 1) {
        bitbot.setPixelColor(5, 0xFF0000)
        bitbot.setPixelColor(11, 0x000000)
        bitbot.rotate(BBRobotDirection.Left, 60)
    } else if (bitbot.readLine(BBLineSensor.Right) == 1) {
        bitbot.setPixelColor(5, 0x000000)
        bitbot.setPixelColor(11, 0xFF0000)
        bitbot.rotate(BBRobotDirection.Right, 60)
    } else {
        bitbot.setPixelColor(5, 0x18E600)
        bitbot.setPixelColor(11, 0x18E600)
        bitbot.go(BBDirection.Forward, 60)
    }
})
```

### Avslutning @unplugged

Nå kan du bruke linjesensoren og du vet også hvordan du kan bruke lyssignaler til å fortelle om en sensor sender signal.
Linjesensorkoden som er brukt her er veldig enkel og kan helt sikkert raffineres en del.
Hvor kjapt en robot klarer å følge en linje er helt avhengig av hvor effektiv koden er.
En konkurranse om linjefølging på tid kan være en fin måte å lære seg å optimalisere kode på.

```package
bitbot=github:4tronix/BitBot
```

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
