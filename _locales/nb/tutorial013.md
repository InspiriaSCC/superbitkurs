### @activities true

# super:bit - Kodeøkt 17: Sender til radiostyrt servo
## Bruk servoer til å lage radiostyrt bevegelse - sender
### Introduksjon @unplugged

I denne gjennomgangen skal du lage radiosenderen til en fjernstyrt bom som løftes opp og ned av en servo.

### Steg 1

Siden radiostyring krever at Micro:biten bruker radiosignaler, må du begynne med å aktivere radioen og velge en kanal.
Det gør du med blokken ``||radio.radio sett gruppe||`` som du finner i ``||radio.Radio||``-menyen.
Hent en ``||radio.radio sett gruppe||`` og plasser den i ``||basic.ved start||``-blokken.
Noter hvilken radiogruppe senderen er satt til.
Standardtallet når du henter blokken er ``||radio.gruppe 1||``, men du kan velge hva du vil så lenge du noterer det og bruker samme gruppe i programmet til mottageren.
Vi bruker ``||radio.gruppe 1||`` i eksempelkoden.

```blocks
radio.setGroup(1)
```

### Steg 2

For å vise at Micro:Biten som skal være radiosender er på og virker, kan du sette inn et ikon i displayet som vises når senderprogrammet kjører.
Du kan tegne en liten radio, eller velge et annet ikon om du foretrekker det.
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

Til en bom som bare skal gå opp og ned trenger du egentlig bare to inndata: Åpne og lukke.
Da passer trykknappene fint.
Hent to ``||input.når knapp A trykkes||``-blokker fra ``||input.Inndata||``-menyen og plasser dem i arbeidsområdet.
Endre ``||input.knapp A||`` til ``||input.knapp B||`` i den ene av dem.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
// @highlight
input.onButtonPressed(Button.B, function () {
	
})
```

### Steg 4

Hent en ``||radio.radio send tall 0||``-blokk fra ``||radio.Radio||``-menyen og plasser den i ``||input.når knapp A trykkes||``-blokken.
Kopier ``||radio.radio send tall 0||``-blokken og plasser kopien i ``||input.når knapp B trykkes||``-blokken.
Endre ``||radio.0||`` til ``||radio.1||`` i blokken du nettopp kopierte.

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(0)
})
input.onButtonPressed(Button.B, function () {
    // @highlight
    radio.sendNumber(1)
})
```

### Avslutning @unplugged

Radiosenderen er nå ferdig. Last ned programmet til en Micro:Bit og merk den med tape eller legg den på et trygt sted så den ikke blir ødelagt.
Du kan nå gå videre til å programmere Micro:Biten som skal ta imot radiosignalene og åpne og lukke bommen.



```package
bitbot=github:4tronix/BitBot
```

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
