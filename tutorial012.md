### @activities true

# super:bit - Kodeøkt 10: Enkel bruk av servo
## Bruk servoer til å lage bevegelse
### Introduksjon @unplugged

En servo er en elektrisk motor som styres av datasignaler.
Det gjør at servoen kan lage veldig presise bevegelser, og derfor brukes de ofte til roboter og andre maskiner som krever høy presisjon.

### Introduksjon 2 @unplugged

En ulempe med servoer og andre elektriske motorer når de brukes sammen med Micro:Bit er at de krever mye strøm.
Micro:Biten kan bare levere 3 volt spenning og noen få milliampère strøm.
Derfor trenger servoer og motorer en ekstern strømkilde for å brukes med Micro:Bit.
Heldigvis har Bit:Bot en egen batteripakke som leverer de bortimot 5 volt som en servo trenger.
Derfor skal du i denne gjennomgangen lære hvordan du kan bruke servoer sammen med Micro:Bit **og** Bit:Bot.

### Tilkoblinger @unplugged

Rett foran hjulet på Bit:Botens venstre side finner du to kontakter med 3 pinner.
Dette er servokontaktene til Bit:Boten.
Det fremste paret med pinner er merket P1 og P2.
P1 og P2 er signalutgangene fra Micro:Biten som brukes til å kontrollere servoene.
De to neste parene er merket henholdsvis 5V og GND.
5V gir 5 volts positiv spenning ut, og GND er jord (eller minus).

### To typer servoer @unplugged

Det følger 2 typer servo med til super:bit.
De som er merket 180 grader har et utslag på kun 180 grader.
De som er merket 360 grader kan rotere rundt og rundt.
Her brukes en 180-graderservo.

### Steg 1 @unplugged

Monter en hvit, enkel plastarm til en **180-graderservo** som vist på bildet.
Koble **180-graderservoen** til P0 rekken av kontakter som forklart og vist.
Servoene som følger med super:bit har tre ledninger ut, en brun, en rød og en oransje.
Brun er jordledningen, den skal kobles til GND.
Rød er "+"-ledningen som skal kobles til 5V.
Oransje er signalledningen som skal kobles til P1 eller P2.
Plasser kontakten til servoen på pinnene ved P1 slik at oransje ledning treffer P1, rød ledning treffer 5V og brun ledning treffer GND.

![Servokobling](https://raw.githubusercontent.com/Yngel72/Superbit/master/static/Servokobling.jpg)

### Steg 2

Først skal vi la en trykknapphendelse styre servoen.
Hent en ``||input.når knapp A trykkes||``-blokk fra ``||input.Inndata||``-menyen og plasser den i arbeidsområdet.

```blocks
// @highlight
input.onButtonPressed(Button.A, function () {
	
})
```

### Steg 3

Alle blokkene til servostyring ligger i mappen ``||bitbot.Bitbot/Sensorer og Styring||``.
Hent en ``||bitbot.sett servo P1 til 90 grader||`` og plasser den i ``||input.når knapp A trykkes||``-blokken.
Last ned programmet til Micro:Biten og se hva som skjer når du setter Micro:Biten i Bit:Boten og trykker på A-knappen ved siden av displayet.

```blocks
input.onButtonPressed(Button.A, function () {
    // @highlight
    bitbot.bbSetServo(BBServos.P1, 90)
})
```

### Steg 4

Hent en ny ``||input.når knapp A trykkes||``-blokk fra ``||input.Inndata||``-menyen og plasser den i arbeidsområdet.
Endre ``||input.knapp A||`` til ``||input.knapp B||``.

```blocks
input.onButtonPressed(Button.A, function () {
    bitbot.bbSetServo(BBServos.P1, 90)
})
// @highlight
input.onButtonPressed(Button.B, function () {
	
})
```

### Steg 5

Hent en ny ``||bitbot.sett servo P1 til 90 grader||`` og plasser den i ``||input.når knapp B trykkes||``-blokken.
Endre ``||bitbot.90 grader||`` til ``||bitbot.180 grader||``.
Last ned programmet til Micro:Biten og se på forskjellen om du trykker på A-knappen eller B-knappen.

```blocks
input.onButtonPressed(Button.A, function () {
    bitbot.bbSetServo(BBServos.P1, 90)
})
input.onButtonPressed(Button.B, function () {
    // @highlight
    bitbot.bbSetServo(BBServos.P1, 180)
})
```

### Avslutning @unplugged

Nå kan du bruke de grunnleggende blokkene for servostyring med bitbot.
I neste instruksjon skal vi kombinere noen flere kodeferdigheter og bruke servoen til noe mer praktisk.

```package
bitbot=github:4tronix/BitBot
```

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
