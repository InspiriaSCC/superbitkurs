### @activities true

# super:bit - Kodeøkt 7: Avansert terning
## Lag en terning som viser øyne
### Introduksjon @unplugged

I denne økten skal du lage en mer realistisk terning.
Terningen skal vise øyne i stedet for tall.
Du må bruke en variabel for å få til dette.
Bruk av variabler i MakeCode krever alltid to trinn.
Først må variabelen opprettes og gis et navn.
Det gjør at det lages en egen blokk for denne variabelen i ``||variables.Variabler||``-menyen.
Så må variabelen defineres i selve koden og gis en verdi.
Blokken ``||variables.sett "variabelnavn" til||`` brukes for å definere variabelen i selve koden, slik at programmet vet at den finnes og at den er en variabel.

### Steg 6: Terning med variabel
Først må du opprette den nye variabelen.
Klikk på ``||variables.Variabler||``-menyen og velg **"Lag en variabel..."**.
Gi variabelen et navn som sier noe om hva den er for noe.
Denne kan du kalle "terningkast".
Hent en ``||input.når ristes||``-blokk fra ``||input.Inndata||``-menyen og legg den på arbeidsflaten.
Hent en ``||variables.sett terningkast til||``-blokk fra ``||variables.Variabler||``-menyen og plasser den **øverst** i ``||input.når ristes||``-blokken.

```blocks
let terningkast = 0
input.onGesture(Gesture.Shake, function () {
    // @highlight
    terningkast = 0
})
```

### Steg 7: Terning med variabel
Hent en ``||math.velg tilfeldig 0 til 10||`` fra ``||math.Matamatikk||``-menyen og dra den inn i det hvite feltet i ``||variables.sett terningkast til||``. Endre så den velger tilfeldig fra 1 til 6. 
Nå vil variabelen ``||variables.terningkast||`` settes til et tilfeldig tall fra 1 til 6 hver gang noen rister på Micro:Biten.
For å vise resultatet må verdien til variabelen sendes til displayet.
Hent en ``||basic.vis tall||``-blokk fra ``||basic.Basis||``-menyen og plasser den under ``||variables.sett terningkast til||``-blokken.

```blocks
let terningkast = 0
input.onGesture(Gesture.Shake, function () {
    terningkast = randint(1, 6)
    // @highlight
    basic.showNumber(0)
})
```
### Steg 8: Terning med variabel
Klikk på ``||variables.Variabler||``-menyen, hent den lille, ovale variabelblokken ``||variables.terningkast||`` og plasser den i det hvite feltet i ``||basic.vis tall||``
Nå vil displayet alltid vise den siste verdien som ble lagret i variabelen ``||variables.terningkast||``.

```blocks
let terningkast = 0
input.onGesture(Gesture.Shake, function () {
    terningkast = randint(1, 6)
    // @highlight
    basic.showNumber(terningkast)
})

```

### Variabler sammenliknet med tall @unplugged
Når du rister på Micro:Biten nå, skjer akkurat det samme som ved den forrige terningen du lagde, men nå lagres det tilfeldige tallet i en variabel.
Siden du bruker en variabel til å lagre terningkastet kan du få displayet til å vise noe annet enn tall når du går videre i veiledningen.

### Steg 9: Terning med øyne, del 1
Dette steget er litt lengre enn de forrige.
Nå skal du bruke noen av de viktigste algoritmene i programmering til å lage et ordentlig program.
Først må du fjerne blokken ``||basic.vis tall||``fra programmet ditt. Kast den i papirkurven.
Så trenger du en ``||logic.hvis sann så ellers||``-blokk fra ``||logic.Logikk||``-menyen.
Dra den inn i ``||input.når ristes||``-blokken og plasser den **under** ``||variables.sett terningkast til||``-blokken.

```blocks
let terningkast = 0
input.onGesture(Gesture.Shake, function () {
    terningkast = randint(1, 6)
    // @highlight
    if (true) {
    	
    } else {
    	
    }
})
```

### Logisk sjekk @unplugged
Nå skal du foreta en logisk sjekk.
Du skal først sjekke om variabelen "terningkast" har verdien 1.
Hvis den har verdien 1, skal Micro:biten vise et terningøye i displayet.
Om verdien ikke er 1, skal programmet gjøre en ny sjekk for verdien 2.
Dersom verdien er 2, skal Micro:Biten vise to terningøyne i displayet.
Om verdiene ikke er 2 heller, gjøres en ny sjekk, helt til programmet finner den sanne verdien av "terningkast".
I alt må du sjekke 5 ganger.
Etter den femte gangen finnes det bare en mulighet igjen, siden "terningkast" bare kan ha 6 mulige verdier, så da trenger du ikke sjekke.

### Steg 10: Terning med øyne, del 2
For å sammenlikne to tall eller variabler bruker du blokken ``||logic.0 = 0||`` fra ``||logic.Logikk||``-menyen.
Hent blokken ``||logic.0 = 0||`` og plasser den i det øverste heksagonet i ``||logic.hvis sann så ellers||``-blokken.
Hent den lille variabelblokken til ``||variables.terningkast||`` i ``||variables.Variabler||``-menyen og plasser den i det første hvite feltet i ``||logic.0 = 0||``-blokken.
I det andre feltet skriver du tallet 1.

```blocks
let terningkast = 0
input.onGesture(Gesture.Shake, function () {
    terningkast = randint(1, 6)
    // @highlight
    if (terningkast == 1) {
    	
    } else {
    	
    }
})
```

### Steg 11: Terning med øyne, del 3
Nå skal du fortelle programmet hva som skal vises i displayet dersom ``||variables.terningkast||`` har verdien 1.
I det øverste gapet i ``||logic.hvis sann så ellers||``-blokken skal du nå plassere blokken ``||basic.vis skjerm||`` fra ``||basic.Basis||``-menyen.
Tegn et terningøye på skjermen ved å klikke på ruten midt i ``||basic.vis skjerm||``-blokken.

```blocks
let terningkast = 0
input.onGesture(Gesture.Shake, function () {
    terningkast = randint(1, 6)
    if (terningkast == 1) {
        // @highlight
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
    } else {
    	
    }
})
```

### Kopiere og endre blokker @unplugged

Nå skal du gjøre den samme logiske sjekken for alle de mulige terningkastresultatene.
Du kan kopiere en blokk ved å høyreklikke på blokken og velge **"Lag kopi"** fra rullegardinmenyen som dukker opp.
Det sparer deg litt tid når du nå skal bruke de samme blokkene flere ganger med små endringer.
Du kan også kopiere en blokk ved å klikke på den og så trykke **Ctrl-C** etterfulgt av **Ctrl-V** på tastaturet, om du foretrekker å bruke hurtigtaster.
Når du har kopiert en blokk må du ofte gjøre små endringer i blokken der du skal bruke den på nytt.
Dette er fort gjort å glemme, men nå er du advart.

### Steg 12: Terning med øyne, del 4

Når du nå skal gjøre flere logiske sjekker i den samme ``||logic.hvis sann så ellers||``-blokken, må du trykke på det lille "+"-tegnet nederst i venstre hjørne av blokken for å utvide.
Da vil det dukke opp et nytt gap og et nytt heksagon.
Du kan trykke flere ganger og få flere gap.
Om du skulle trykke for mange ganger, kan du trykke på det lille **"-"**-tegnet på høyre side i den øverste armen av det siste gapet for å fjerne det.
Trykk 4 ganger på det lille **"+"**-tegnet så du har 5 gap under det som allerede inneholder en ``||basic.vis skjerm||``-blokk.

```blocks
let terningkast = 0
input.onGesture(Gesture.Shake, function () {
    terningkast = randint(1, 6)
    // @highlight
    if (terningkast == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
    } else if (false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

### Steg 13: Terning med øyne, del 5

Nå kan du kopiere den lille, heksagonale ``||logic.terningkast = 1||``-blokken fra  øverst i ``||logic.hvis sann så ellers||``-blokken og plassere den i det neste ledige heksagonet.
Endre tallet 1 til 2.
Kopier ``||basic.vis skjerm||``-blokken fra de øverste gapet og legg kopien i gap nummer to.
Endre ikonet så det ser ut som to øyne på en terning.

```blocks
let terningkast = 0
input.onGesture(Gesture.Shake, function () {
    terningkast = randint(1, 6)
    if (terningkast == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
    } else if (terningkast == 2) {
        // @highlight
        basic.showLeds(`
            . . . . #
            . . . . .
            . . . . .
            . . . . .
            # . . . .
            `)
    } else if (false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

### Steg 14: Terning med øyne, del 6

Du må gjenta prosessen i forrige steg for resultatene 3, 4 og 5 også.
Kopier eller hent inn blokkene som trengs for å fylle de neste 3 heksagonene og gapene i ``||logic.hvis sann så ellers||``-blokken.
Husk å endre tallet det sjekkes for i ``||logic.heksagonene||`` og antall øyne på ``||basic.vis skjerm||``-blokkene.


```blocks
let terningkast = 0
input.onGesture(Gesture.Shake, function () {
    terningkast = randint(1, 6)
    if (terningkast == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
    } else if (terningkast == 2) {
        basic.showLeds(`
            . . . . #
            . . . . .
            . . . . .
            . . . . .
            # . . . .
            `)
    } else if (terningkast == 3) {
        basic.showLeds(`
            . . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . .
            `)
    } else if (terningkast == 4) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . . . .
            . . . . .
            # . . . #
            `)
    } else if (terningkast == 5) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . #
            `)
    } else {
    	
    }
})
```

### Steg 15: Terning med øyne, del 7
Over det siste gapet trenger du ingen ``||logic.terningkast = 6||``-blokk.
Alle resultatene er sjekket, bortsett fra 6, så da er det den eneste gjenværende muligheten.
Alt du trenger å gjøre nå er å lage den siste ``||basic.vis skjerm||``-blokken i det siste gapet, og så er terningen klar.
Vi anbefaler å laste ned programmet til Micro:Biten. Det er noe eget ved å riste på en digital terning man har laget selv.
Det var det hele! Gratulerer! Du har nettopp programmert en kul elektronisk terning!

```blocks
let terningkast = 0
input.onGesture(Gesture.Shake, function () {
    terningkast = randint(1, 6)
    if (terningkast == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
    } else if (terningkast == 2) {
        basic.showLeds(`
            . . . . #
            . . . . .
            . . . . .
            . . . . .
            # . . . .
            `)
    } else if (terningkast == 3) {
        basic.showLeds(`
            . . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . .
            `)
    } else if (terningkast == 4) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . . . .
            . . . . .
            # . . . #
            `)
    } else if (terningkast == 5) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . #
            `)
    } else {
        basic.showLeds(`
            # . . . #
            . . . . .
            # . . . #
            . . . . .
            # . . . #
            `)
    }
})
```

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
