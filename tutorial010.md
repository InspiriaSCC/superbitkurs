### @activities true

# super:bit - Kodeøkt 4: Radiosender
## Bruk radiosignaler til å fjernstyre en Bit:Bot
### Introduksjon @unplugged

Gjennomgangen om radiostyring må gjøres i to deler.
Det er fordi det må programmeres to Micro:Biter for å lage en fjernstyrt robot, altså en sender og en mottager.
Senderen tar imot inndata fra den som skal styre roboten via knapper eller bevegelse og videresender dem til mottageren som formidler inndataene til roboten.
Du begynner med å programmere senderen i denne gjennomgangen, så tar vi for oss mottageren i neste runde.

### Steg 1

Siden radiostyring krever at Micro:biten bruker radiosignaler, må du begynne med å aktivere radioen og velge en kanal.
Det gør du med blokken ``||radio.radio sett gruppe||`` som du finner i ``||radio.Radio||``-menyen.
Siden denne koden i denne blokken må kjøres før du kan ta i bruk radioen, må den settes inn i ``||basic.ved start||``-blokken. Hent en ``||radio.radio sett gruppe||`` og plasser den i ``||basic.ved start||``-blokken.

```blocks
radio.setGroup(1)
```

### Steg 2

For å vise at Micro:Biten som skal være radiosender er på og virker, kan du sette inn et ikon i displayet som vises når senderprogrammet kjører.
Du kan tegne en liten radio, eller velge et annet ikon om du foretrekker det. Til det trenger du ``||basic.vis skjerm||``-blokken.
Hent en ``||basic.vis skjerm||`` eller ``||basic.vis ikon||`` blokk fra ``||basic.Basis||``-menyen og sett den inn i ``||basic.ved start||``-blokken under ``||radio.radio sett gruppe||``-blokken.

```blocks
radio.setGroup(1)
// @highlight
basic.showLeds(`
    . . . . #
    . . . . #
    # # # # #
    # . # # #
    # # # # #
    `)
```

### Steg 3

Resten av koden skal kjøre i en ``||basic.gjenta for alltid||``-blokk. Koden i en ``||basic.gjenta for alltid||``-blokk gjentas igjen og igjen så lenge programmet kjører.
Hent en i ``||basic.Basis||``-menyen om det ikke allerede ligger en i arbeidsområdet.
Du trenger også en ``||logic.hvis sann så ellers||``-blokk fra ``||logic.Logikk||``-menyen.
Plasser ``||logic.hvis sann så ellers||``-blokken i ``||basic.gjenta for alltid||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    if (true) {
    	
    } else {
    	
    }
})
```

### Inndata @unplugged

Nå trenger du en måte å hente inndata på.
Siden Micro:Biten bare har to knapper, er det vanskelig å få til framover, bakover og sving til høyre og venstre med knappene.
Da er akselerometeret en bedre måte å styre roboten på.
Akselerometeret gir inndata når Micro:Biten vippes i fire retninger, og det er egentlig alt vi trenger for å styre roboten.

### Steg 4

Hent en heksagonformet ``||input.er ristes bevegelse||``-blokk fra ``||input.Inndata||``-menyen og plasser den i heksagonet øverst i ``||logic.hvis sann så ellers||``-blokken.
Endre ``||input.ristes||`` til ``||input.logo ned||``.

```blocks
basic.forever(function () {
    // @highlight
    if (input.isGesture(Gesture.LogoDown)) {
    	
    } else {
    	
    }
})
```

### Kommunikasjonen mellom sender og mottager @unplugged

Når Micro:Bit-senderen vippes forover, altså med logoen ned, skal den sende en kode til mottageren via radioen.
Siden du bare trenger 4 retninger; Framover, bakover, høyre og venstre, kan du bruke tallene 1-4 som radiokoder.

### Steg 5

Hent en ``||radio.radio send tall||`` blokk fra ``||radio.Radio||``-menyen og sett den inn i det øverste gapet i ``||logic.hvis sann så ellers||``-blokken.
Endre "0" til "1".

```blocks
basic.forever(function () {
    if (input.isGesture(Gesture.LogoDown)) {
        // @highlight
        radio.sendNumber(1)
    } else {
    	
    }
})
```

### Steg 6

Nå kan du få roboten til å kjøre framover. For å få flere styreretninger må du nå utvide ``||logic.hvis sann så ellers||``-blokken.
Trykk på det lille "+"-tegnet nede til høyre i ``||logic.hvis sann så ellers||``-blokken. tre ganger.
Det vi gi deg et gap for mye, men nå har du riktig antall heksagoner til å sette inndata inn i.
Det ekstra gapet fjerner du i et senere trinn.

```blocks
basic.forever(function () {
    // @highlight
    if (input.isGesture(Gesture.LogoDown)) {
        radio.sendNumber(1)
    } else if (false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

### Steg 7

Kopier heksagonet ``||input.logo ned||`` fra det øverste heksagonet i ``||logic.hvis sann så ellers||``-blokken og dra kopien inn i det øverste, ledige heksagonet.
Endre ``||input.logo ned||`` til ``||input.logo opp||`` i det nye heksagonet.

```blocks
basic.forever(function () {
    // @highlight
    if (input.isGesture(Gesture.LogoDown)) {
        radio.sendNumber(1)
    } else if (input.isGesture(Gesture.LogoUp)) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

### Steg 8

Kopier ``||radio.radio send tall||`` blokken fra det øverste gapet og dra kopien inn i det neste ledige gapet.
Endret tallet i det hvite feltet fra "1" til "2".

```blocks
basic.forever(function () {
    if (input.isGesture(Gesture.LogoDown)) {
        radio.sendNumber(1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        // @highlight
        radio.sendNumber(2)
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

### Steg 9

Kopier heksagonet ``||input.logo ned||`` fra det øverste heksagonet i ``||logic.hvis sann så ellers||``-blokken og dra kopien inn i det øverste, ledige heksagonet.
Endre ``||input.logo ned||`` til ``||input.helning venstre||`` i det nye heksagonet.

```blocks
basic.forever(function () {
    // @highlight
    if (input.isGesture(Gesture.LogoDown)) {
        radio.sendNumber(1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        radio.sendNumber(2)
    } else if (input.isGesture(Gesture.TiltLeft)) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

### Steg 10

Kopier ``||radio.radio send tall||`` blokken fra det øverste gapet og dra kopien inn i det neste ledige gapet.
Endret tallet i det hvite feltet fra "1" til "3".

```blocks
basic.forever(function () {
    if (input.isGesture(Gesture.LogoDown)) {
        radio.sendNumber(1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        radio.sendNumber(2)
    } else if (input.isGesture(Gesture.TiltLeft)) {
        // @highlight
        radio.sendNumber(3)
    } else if (false) {
    	
    } else {
    	
    }
})
```

### Steg 11

Kopier heksagonet ``||input.logo ned||`` fra det øverste heksagonet i ``||logic.hvis sann så ellers||``-blokken og dra kopien inn i det øverste, ledige heksagonet.
Endre ``||input.logo ned||`` til ``||input.helning høyre||`` i det nye heksagonet.

```blocks
basic.forever(function () {
    // @highlight
    if (input.isGesture(Gesture.LogoDown)) {
        radio.sendNumber(1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        radio.sendNumber(2)
    } else if (input.isGesture(Gesture.TiltLeft)) {
        radio.sendNumber(3)
    } else if (input.isGesture(Gesture.TiltRight)) {
    	
    } else {
    	
    }
})
```

### Steg 12

Kopier ``||radio.radio send tall||`` blokken fra det øverste gapet og dra kopien inn i det neste ledige gapet.
Endret tallet i det hvite feltet fra "1" til "4".

```blocks
basic.forever(function () {
    if (input.isGesture(Gesture.LogoDown)) {
        radio.sendNumber(1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        radio.sendNumber(2)
    } else if (input.isGesture(Gesture.TiltLeft)) {
        radio.sendNumber(3)
    } else if (input.isGesture(Gesture.TiltRight)) {
        // @highlight
        radio.sendNumber(4)
    } else {
    	
    }
})
```

### Steg 13

Trykk på det lille "-"-tegnet ytterst til venstre på armen over det siste ledige gapet.
Det fjerner det ledige gapet, og så er radiosenderen klar til bruk.

```blocks
basic.forever(function () {
    // @highlight
    if (input.isGesture(Gesture.LogoDown)) {
        radio.sendNumber(1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        radio.sendNumber(2)
    } else if (input.isGesture(Gesture.TiltLeft)) {
        radio.sendNumber(3)
    } else if (input.isGesture(Gesture.TiltRight)) {
        radio.sendNumber(4)
    }
})
```

### Avslutning @unplugged
Det var alt du trenger til senderen.
Nå kan du laste ned programmet til en Micro:Bit.
Når du skal bruke radiosenderen er det fint å ha en batteripakke tilkoblet, så du slipper å ha den koblet til en PC for strøm.
Foreløpig har du ingen mottager, så neste gjennomgang tar for seg hvordan du lager en mottager som skal sitte i Bitboten du skal fjernstyre.
Det kan være lurt å legge radiosenderen på et trygt sted i mellomtiden, eller merke den med tape, så den ikke blir brukt til noe annet før du skal bruke den som fjernkontroll.


```package
bitbot=github:4tronix/BitBot
```

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
