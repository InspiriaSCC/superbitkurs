### @activities true

# super:bit - Kodeøkt 15: Koble LED-pærer til Micro:Bit
## Introduksjon
### Introduksjon @unplugged

Nå skal du få Micro:Biten til å skru LED-pærer av og på.
Nederst på Micro:Biten ser du 5 brede striper med hull i.
Mellom disse ligger det mange smalere striper.
De brede stripene med hull kan brukes med krokodilleklemmer.
Stripene som er merket 0, 1 og 2 er inn- og utganger for elektronikk.
3V er en plusspol som gir 3 volt til elektronikk man kobler til Micro:Biten.
GND er minuspolen, eller jord, som det gjerne kalles.
Du skal nå bruke disse metallstripene og krokodilleklemmer for å koble til en LED-pære.
Totalt for denne økten vil du trenge 4 ledninger med krokodilleklemmer og 3 LED-pærer (rød, gul, grønn) i tillegg til Micro:Bit og evt. batteripakke om du bruker iPad eller Android, eller USB-kabelen om du bruker PC.

### Få en LED til å blinke 1 @unplugged

Du trenger 2 ledninger med krokodilleklemmer, røde LED-pære og en Micro:Bit med USB-ledning (Evt. batteripakke om du bruker iPad eller Android-brett) til gjennomgangen.
Før du starter kodingen:
Koble en ledning med krokodilleklemme til "0" på Micro:Biten og det lange benet til LED-pæren.
Koble den andre ledningen til det korte benet på LED-pæren og GND på Micro:Biten.
LED-pærene som følger med i Superbitsettet har en innebygget motstand som beskytter dem mot for høy spenning fra Micro:Biten, derfor kan de kobles på direkte..
Pass på at krokodilleklemmene som er koblet til LED-pæren ikke er i kontakt med hverandre.
Du kan bøye bena til LED-pæren forsiktig ut for å få større avstand mellom krokodilleklemmene.
Koble Micro:Biten til PCen ved hjelp av USB-ledningen. (Koble til en batteripakke om du bruker iPad eller Android-brett)
Nå er koblingene klare.

![LEDkobling](https://raw.githubusercontent.com/Yngel72/Superbit/master/static/LEDkobling.jpg)

### Steg 1 Få en LED til å blinke 1

``||pins.Tilkoblinger||`` finner du under **"Avansert"** i menyen. Hent en ``||pins.skriv digital til p0 verdi 0||``-blokk fra ``||pins.Tilkoblinger||``-menyen og dra den inn i ``||basic.gjenta for alltid||``-blokken. (Hvis du mangler, hent en fra ``||basic.Basis||``-menyen. )

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
})
```

### Steg 2 Få en LED til å blinke 2

Hent en ``||basic.pause||``-blokk fra ``||basic.Basis||``-menyen og legg den inn i ``||basic.gjenta for alltid||``-blokken under ``||pins.skriv digital til p0 verdi 0||``-blokken.
Endre tiden i ``||basic.pause||``-blokken til 500 ms.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(500)
})
```

### Steg 3 Få en LED til å blinke 3

Kopier ``||pins.skriv digital til p0 verdi||``-blokken og legg kopien inn under ``||basic.pause||``-blokken.
Endre verdien i det hvite feltet i ``||pins.skriv digital til p0 verdi 0||``-blokken fra 0 til 1.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 1)
})
```

### Om digitale inn- og utdata @unplugged

Ordet "digital" betyr i denne sammenhengen at signalet til eller fra en tilkobling enten kan være av eller på.
Digitale signaler kan ikke ha varierende styrke, de er bare av eller på, med verdiene 0 eller 1.
I denne blokken betegner "p0" en "pin" på Micro:Biten, mens verdien i det hvite feltet bestemmer om p0 skal sende signal eller ikke.
Om verdien er 0 går det ikke noe signal fra p0, og LED-pæra vil være slukket.
Er verdien 1 vil det gå et signal med 3 Volt spenning fra p0, og LED-pære vil være på helt til verdien settes til 0 igjen.
Til sammen har Micro:Bit 19 inn- og utganger du kan bruke dersom du har et breakout board.

### Steg 4 Få en LED til å blinke 4

Kopier ``||basic.pause||``-blokken og legg kopien inn under den siste ``||pins.skriv digital til p0 verdi 1||``-blokken.
Nå kan du laste ned programmet til Micro:Biten og se hva som skjer.
Hva skjer om du endrer verdiene på tiden?
Klarer du å lage et program som sender morsekoden for SOS? (Tre korte, tre lange, tre korte blink)

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(500)
})
```

### Få 3 LED-pærer til å blinke @unplugged

Før du går videre trenger du to nye ledninger og de to siste LED-pærene.
Før du starter kodingen:

Koble en ledning med krokodilleklemme til "1" på Micro:Biten og det lange benet til den gule LED-pæren.
Koble det korte benet på LED-pæren til den krokodilleklemmen som er på det korte benet til den røde pæren. 
Gjør det samme med den grønne LED-pæren og den siste krokodilleklemmen.
Koble Micro:Biten til PCen ved hjelp av USB-ledningen. (Koble til en batteripakke om du bruker iPad eller Android-brett)

![TrafikklysLED](https://raw.githubusercontent.com/Yngel72/Superbit/master/static/Trafikklyskobling21.jpg)

![TrafikklysMicro:Bit](https://raw.githubusercontent.com/Yngel72/Superbit/master/static/Trafikklyskobling12.jpg)


### Steg 5 Få 3 LED-pærer til å blinke 1

Kopier den første ``||pins.skriv digital til p0 verdi 1||``-blokken to ganger, og legg begge kopiene rett under originalblokken.
Endre ``||pins.p0||`` i ``||pins.skriv digital til p0 verdi 0||`` til ``||pins.p1||`` i den ene av kopiene, og til ``||pins.p2||`` i den andre.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(500)
})
```

### Steg 6 Få 3 LED-pærer til å blinke 2

Kopier ``||pins.skriv digital til p0 verdi 1||``-blokken som ligger mellom de to pauseblokkene to ganger, legg kopiene inn mellom originalblokken og den siste ``||basic.pause||``-blokken.
Endre ``||pins.p0||`` i ``||pins.skriv digital til p0 verdi 1||`` til ``||pins.p1||`` i den ene av kopiene, og til ``||pins.p2||`` i den andre, akkurat som i forrige steg.
Last opp programmet til Micro:Biten og se hva som skjer.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 1)
    pins.digitalWritePin(DigitalPin.P1, 1)
    pins.digitalWritePin(DigitalPin.P2, 1)
    basic.pause(500)
})
```

### Steg 7 Få 3 LED-pærer til å blinke 3

Nå skal du forsøke å endre verdiene 1 og 0 i de hvite feltene slik at de to ytterste LED-pærene tennes samtidig, mens den midterste tennes alene annenhver gang.
Klarer du det?
Klikk på lyspæren ved siden av denne teksten for å se en mulig løsning.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 1)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.pause(500)
})
```

### Steg 8 Få 3 LED-pærer til å blinke 4
Klarer du å utvide koden så LED-pærene tennes én og én?
Da trenger du nok flere ``||pins.skriv digital til p0/p1/p2 verdi 0||``, ``||pins.skriv digital til p0/p1/p2 verdi 1||`` og ``||basic.pause||``-blokker.
Klikk på lyspæren om du vil se en mulig løsning 

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 1)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 1)
    basic.pause(500)
})
```

### Steg 9 Få 3 LED-pærer til å blinke 5

Det du har lært nå kan brukes til å koble et trafikklys.
Sekvensen for trafikklys er som regel rødt -> rødt + gult -> grønt -> gult -> rødt.
Klarer du å endre koden din til å få til denne sekvensen?
(I hintet er det forutsatt at rød LED er på P0, gul på P1 og grønn på P2.)

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.pause(3000)
    pins.digitalWritePin(DigitalPin.P0, 1)
    pins.digitalWritePin(DigitalPin.P1, 1)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.pause(1000)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 1)
    basic.pause(3000)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 1)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.pause(1000)
})
```

### Avslutning @unplugged
Nå har du lært hvordan du kan få Micro:Biten til å slå noe av og på ved hjelp av digitale utganger, og du har lært å kode et trafikklys.

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>