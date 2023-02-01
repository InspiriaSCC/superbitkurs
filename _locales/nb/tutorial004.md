### @activities true

# super:bit - Ekstra kodeøkt: Lag spill - Funksjoner og spillblokker
## Introduksjon
### Introduksjon @unplugged

Ved hjelp av displayet og inndata kan man lage spill til Micro:Bit.
Alle funksjoner som har med spill å gjøre finner du under **"Avansert"** i blokkemenyen.
Denne gjennomgangen er ganske lang, den består av 23 steg, så sett av litt god tid.
Du skal nå lage spillet som ligger på alle nye Micro:Bits når de startes første gang.
Spillet kalles *"Chase the dot"* på engelsk, og går ut på å styre en lysende spillebrikke som skal fange en annen brikke som blinker.
Du må vende på hele Micro:Biten for å få brikken du styrer til å falle ned mot byttet den jakter på.

### Steg 1 Lag variablene

Først må du lage en variabel for hver brikke, og definere dem i ``||basic.ved start||``-blokken.
Gå til ``||variables.Variabler||``-menyen og velg **"Lag en variabel..."**.
Lag to variabler, en som du kaller ``||variables.jeger||`` og en som du kaller ``||variables.bytte||``.
Hent to ``||variables.sett bytte til||``-blokker fra ``||variables.Variabler||``-menyen og dra dem inn i ``||basic.ved start||``-blokken.
Endre en av blokkene slik at det står ``||variables.sett bytte til||`` i den ene blokken og ``||variables.sett jeger til||`` i den andre.

```blocks
let bytte = 0
let jeger = 0
```

### Steg 2 Spillmenyen

Klikk på **"Avansert"** nederst i blokkmenyen så menyen utvides.
Klikk på ``||game.Spill||``-menyen som dukker opp og velg blokken ``||game.lag brikke på x: 2 y: 2||``.
Plasser en slik blokk i det hvite feltet i ``||variables.sett bytte til||``-blokken og en i ``||variables.sett jeger til||``-blokken.
Endre X og Y verdiene i "bytteblokken" så det står ``||variables.sett bytte til||`` ``||game.lag brikke på x: 0 y: 0||``.
Jegerblokken kan du la stå som som ``||variables.sett jeger til||`` ``||game.lag brikke på x: 2 y: 2||``

```blocks
// @highlight
let bytte = game.createSprite(0, 0)
let jeger = game.createSprite(2, 2)
```

### Micro:Bit-displayet og koordinater @unplugged

Variablene er nå spillebrikker på displayet til Micro:Biten.
Displayet til Micro:Bit behandles som et koordinatsystem av programmet.
Koordinatene går fra 0 til 4, ikke fra 1 til 5, selv om displayet har 5 x 5 pixler, siden man gjerne starter rekker og lister med 0 i programmering.
Positiv x-retning er fra venstre mot høyre.
Positiv y-retning er litt uvant her.
Den går fra øverst til nederst, så bevegelse oppover går i negativ y-retning på displayet.
Koordinaten 0,0 er øverst i venstre hjørne av displayet.
Koordinatene 2,2 er midt på displayet.
Koordinatene 4,4 er nederst i høyre hjørne av displayet


### Steg 3 Lysstyrke og blinking

Hent to ``||game.sprite angir x til||``-blokker fra ``||game.Spill||``-menyen og plasser dem under de forrige blokkene dine.
Klikk på den lille pilen til høyre for ``||variables.sprite||`` på den første blokken og velg ``||variables.bytte||``.
Gjør det samme på den andre blokken, men velg ``||variables.jeger||``
Klikk på den lille pilen til høyre for ``||game.x||`` i ``||game.bytte||``-blokken og velg ``||game.blinke||``.
Sett tallet bak ``||game.blinke||`` til 3.
Klikk på den lille pilen til høyre for ``||game.x||`` i ``||game.jeger||``-blokken og velg ``||game.lysstyrke||``.
Sett tallet bak ``||game.lysstyrke||`` til 5.
Nå vil brikken til byttet blinke, mens jegeren lyser hele tiden.

```blocks
let bytte = game.createSprite(0, 0)
let jeger = game.createSprite(2, 2)
// @highlight
bytte.set(LedSpriteProperty.Blink, 3)
jeger.set(LedSpriteProperty.Brightness, 5)
```

### Funksjoner @unplugged

I neste trinn skal du lage en funksjon.
En funksjon er kode som kan gjenbrukes der det trengs.
Funksjoner bruker vi når vi trenger å kjøre den samme koden flere forskjellige steder i et program, så vi slipper å skrive den samme koden mange ganger.
Funksjoner minner om løkker, men mens løkker kjører koden flere ganger rett etter hverandre, kan en funksjon kjøre koden en gang og la programmet gå videre.
Neste gang programmet trenger funksjonen, kan du hente den inn igjen.
Å hente inn en funksjon kalles vanligvis å *kalle* på den.

### Navn på variabler og funksjoner @unplugged

Ofte gir man funksjoner, akkurat som variabler, liten førstebokstav.
Om en funksjon eller variabel er satt sammen av flere ord, bruker man gjerne stor førstebokstav i hvert ord bortsett fra på det første ordet.

### Steg 4 Lag en funksjon

Å lage en funksjon minner om å lage en variabel.
Funksjonsmenyen ligger under **"Avansert"**.
Klikk på ``||functions.Funksjoner||``-menyen og velg **"Lag en funksjon..."**
Gi funksjonen navnet nyRunde ved å skrive inn det nye navnet der det står gjørNoe i blokken som dukker opp på skjermen.
Funksjonen legger seg automatisk i arbeidsområdet etter at du har laget den.

```blocks
function nyRunde () {
	
}
```

### Ny runde @unplugged

Når spilleren klarer å fange byttet starter en ny runde.
Da skal et nytt bytte dukke opp et tilfeldig sted på skjermen.
Nå skal du lage funksjonen som starter en ny runde.

### Steg 5 Sett inn kode i funksjonen

Hent to nye ``||game.sprite angir x til||``-blokker fra ``||game.Spill||``-menyen og plasser dem i funksjonsblokken du lagde.
Bytt ut ``||variables.sprite||`` med ``||variables.bytte||`` i begge.
Endre ``||game.x||`` til ``||game.y||`` i den **ene** av blokkene.
Hent en ``||math.velg tilfeldig 0 til 10||``-blokk fra ``||math.Matematikk||``-menyen og plasser den i det hvite feltet etter ``||game.x||`` i den ene blokken.
Endre 10-tallet til et 4-tall i ``||math.velg tilfeldig 0 til 10||``-blokken.
Kopier ``||math.velg tilfeldig 0 til 4||``-blokken du nettopp redigerte over til den andre ``||game.sprite angir x til||``-blokken.
Dette plasserer byttet på en tilfeldig (X,Y)-koordinat når en ny runde starter.

```blocks
let bytte: game.LedSprite = null
function nyRunde () {
    bytte.set(LedSpriteProperty.X, randint(0, 4))
    // @highlight
    bytte.set(LedSpriteProperty.Y, randint(0, 4))
}
```

### Om akselerometeret til Micro:Bit @unplugged

Akselerometeret til Micro:Bit kan være litt varierende sensitivt, slik at man enten ikke får jegeren til å bevege på seg, eller så beveger den seg plutselig alt for fort.
For å gjøre spillet enklere skal vi gjøre det sånn at byttet alltid dukker opp inntil kanten av displayet.
Da blir det lettere for spilleren å fange byttet.
For å få byttet til å dukke opp inntil kanten av displayet skal vi bruke en logisk løkke.
Løkken sjekker om byttet er plassert inntil kanten av displayet.
Om byttet ikke ligger inntil kanten, kjøres "nyRunde"-funksjonen på nytt, helt til byttet er plassert inntil kanten.

### Steg 6 Begrens hvor byttet kan dukke opp

Hent en ``||logic.hvis sann så||``-blokk fra ``||logic.Logikk||``-menyen og plasser den i ``||functions.nyRunde||``-blokken under de forrige blokkene du la inn der.
Hent en liten heksagonal ``||logic.ikke||`` blokk fra ``||logic.Logikk||``-menyen og plasser den i heksagonet på ``||basic.hvis sann så||``-blokken.
Hent en heksagonal ``||variables.sprite||`` ``||game.berører kant?||``-blokk fra ``||game.Spill||``-menyen og plasser den inni ``||logic.ikke||`` blokken.
Klikk på den lille hvite pilen til høyre for ``||variables.sprite||`` og velg ``||variables.bytte||`` slik at det står``||logic.hvis ikke||`` ``||variables.bytte||`` ``||game.berører kant?||`` i blokken.
Hent ``||functions.kjør nyRunde||``-blokken fra ``||functions.Funksjoner||``-menyen og plasser den i gapet på ``||basic.hvis sann så||``-blokken
Nå er den logiske løkken klar.

```blocks
let bytte: game.LedSprite = null
function nyRunde () {
    bytte.set(LedSpriteProperty.X, randint(0, 4))
    bytte.set(LedSpriteProperty.Y, randint(0, 4))
    // @highlight
    if (!(bytte.isTouchingEdge())) {
        nyRunde()
    }
}
```

### Steg 7 Kall på funksjonen når spillet starter

Nå må du tilbake til ``||basic.ved start||``-blokken for å kalle på funksjonen du nettopp lagde.
Hent ``||functions.kjør nyRunde||``-blokken fra ``||functions.Funksjoner||``-menyen og plasser den nederst i koden i ``||basic.ved start||``-blokken.
Den siste blokken du trenger i startkoden din er en nedtellingsblokk, slik at ikke spillet varer evig.
Hent en ``||game.start nedtelling 10000 ms||``-blok fra ``||game.Spill||``-menyen og plasser den under ``||functions.kjør nyRunde||``-blokken i ``||basic.ved start||``.
Nedtellingsblokken legger automatisk til en animasjon i starten og en "GAME OVER - SCORE" tekst i slutten av spillet.
Nå har du plassert all koden du trenger i startblokken.
Nå skal vi få jegeren til å bevege seg når Micro:Biten vippes.

```blocks
function nyRunde () {
    bytte.set(LedSpriteProperty.X, randint(0, 4))
    bytte.set(LedSpriteProperty.Y, randint(0, 4))
    if (!(bytte.isTouchingEdge())) {
        nyRunde()
    }
}
let bytte: game.LedSprite = null
bytte = game.createSprite(0, 0)
let jeger = game.createSprite(2, 2)
bytte.set(LedSpriteProperty.Blink, 3)
jeger.set(LedSpriteProperty.Brightness, 5)
// @highlight
nyRunde()
game.startCountdown(10000)
```

### Forskjellen på "ved start" og "gjenta for alltid" @unplugged

Kontrollene til jegeren legges i en "gjenta for alltid"-løkke.
Det er fordi denne koden må kjøres hele tiden for å sjekke statusen til helningen på Micro:Biten.
Hadde vi plassert denne koden i "ved start"-blokken, ville helningen på Micro:Biten blitt sjekket én gang, og aldri mer.
I "ved start"-blokker legger man kode som skal kjøres i oppstarten av et program.
For spillprogrammer vil dette være koden som setter opp startbetingelsene for spillet og definerer spillere, fiender og andre variabler som trengs i resten av koden.
Kode som trengs for aktiviteter og hendelser i spillet, som bevegelsene til spillere og fiender, fornybare ressurser og så videre, kjøres i løkker som gjentas flere ganger ettersom spilleren endrer på ting i spillet.
Da bruker man "gjenta for alltid", eller andre blokker med kode som utløses av hendelser i spillet.
Alle disse blokkene vil være blokker som ikke kan settes inn i en startblokk, men som fungerer som egne, frittstående løkker i arbeidsområdet.

### Steg 8 Spillkontrolleren

Om du ikke allerede har en liggende i arbeidsområdet, så hent en ``||basic.gjenta for alltid||``-blokk fra ``||basic.Basis||``-menyen.
Har du allerede en slik blokk liggende, så bruker du den.
Plasser en ``||logic.hvis sann så ellers||``-blokk fra ``||logic.Logikk||``-menyen i ``||basic.gjenta for alltid||``-blokken.

```blocks
basic.forever(function () {
    // @highlight
    if (true) {
    	
    } else {
    	
    }
})
```

### Steg 9 Spillkontrolleren

Hent en ``||input.er ristes bevegelse||`` fra ``||input.Inndata||``-menyen, plasser den i heksagonet øverst i ``||logic.hvis sann så ellers||``-blokken og endre ``||input.ristes||`` til ``||input.helning venstre||``.

```blocks
basic.forever(function () {
    // @highlight
    if (input.isGesture(Gesture.TiltLeft)) {
    	
    } else {
    	
    }
})
```

### Steg 10 Spillkontrolleren

Høyre/venstre er x-aksen på Micro:Bit-displayet, så tilt i disse retningene må føre til bevegelse i x-retning.
Hent en ``||game.sprite endre x med 1||``-blokk fra ``||game.Spill||``-menyen og plasser den i gapet på ``||logic.hvis sann så ellers||``-blokken.
Endre ``||variables.sprite||`` til ``||variables.jeger||`` ved å klikke på den lille pilen til høyre for ``||variables.sprite||`` og velg ``||variables.jeger||``.
Bevegelse mot venstre er bevegelse i negativ x-retning på displayet, så du må endre **1** til **-1**

```blocks
let jeger: game.LedSprite = null
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        // @highlight
        jeger.change(LedSpriteProperty.X, -1)
    } else {
    	
    }
})
```

### Steg 11 Spillkontrolleren

Nå må du gjøre det samme for de gjenstående tre retningene.
Utvid ``||logic.hvis sann så ellers||``-blokken to ganger ved å trykke på det lille **+**-tegnet nederst til venstre på blokken.
Du trenger tre ledige gap under gapet du allerede har satt inn en blokk i.
Om du skulle klikke for mange ganger, kan du trykke på **-**-tegnet til høyre på den nest nederste armen på blokken.

```blocks
let jeger: game.LedSprite = null
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        // @highlight
        jeger.change(LedSpriteProperty.X, -1)
    } else if (false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    }
})
```

### Steg 12 Spillkontrolleren

Kopier ``||input.er helning venstre bevegelse||``-blokken fra den øverste armen i ``||logic.hvis sann så ellers||``-blokken og plasser kopien i det neste ledige heksagonet.
Endre ``||input.helning venstre||`` til ``||input.helning høyre||``
Kopier ``||game.jeger endre x med -1||``-blokken og plasser kopien i gapet under heksagonet du nettopp redigerte.
Endre **-1** til **1**

```blocks
let jeger: game.LedSprite = null
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        jeger.change(LedSpriteProperty.X, -1)
    } else if (input.isGesture(Gesture.TiltRight)) {
        // @highlight
        jeger.change(LedSpriteProperty.X, 1)
    } else if (false) {
    	
    } else if (false) {
    	
    }
})
```

### Steg 13 Spillkontrolleren

Kopier ``||input.er helning venstre bevegelse||``-blokken fra den øverste armen i ``||logic.hvis sann så ellers||``-blokken og plasser kopien i det neste ledige heksagonet.
Endre ``||input.helning venstre||`` til ``||input.logo ned||``
Kopier ``||game.jeger endre x med -1||``-blokken og plasser kopien i gapet under heksagonet du nettopp redigerte.
Endre ``||game.x||`` til ``||game.y||``

```blocks
let jeger: game.LedSprite = null
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        jeger.change(LedSpriteProperty.X, -1)
    } else if (input.isGesture(Gesture.TiltRight)) {
        jeger.change(LedSpriteProperty.X, 1)
    } else if (input.isGesture(Gesture.LogoDown)) {
        // @highlight
        jeger.change(LedSpriteProperty.Y, -1)
    } else if (false) {
    	
    }
})
```

### Om koordinatsystemet til LED-matrisen @unplugged

Positiv y-retning er nedover på displayet, så når vi heller på Micro:biten så logoen står opp ned, vil jegeren bevege seg i negativ y-retning.
Dette kan virke litt baklengs sammenliknet med det elevene lærer om kartesiske koordinatsystemer i mattetimene, men sånn er altså LED-matrisen definert.
Her kan kanskje et læringspunkt være at koordinatsystemer kan defineres på flere måter.

### Steg 14 Spillkontrolleren

Om du ikke har et ledig heksagon over det siste gapet, kan du trykke på det lille **+**-tegnet nede til høyre i blokken og lage et ekstra gap.
Da får du et nytt heksagon på det nest siste gapet.
Det ekstra gapet fjerner du etter at du har fullført dette steget.
Kopier ``||input.er helning venstre bevegelse||``-blokken fra den øverste armen i ``||logic.hvis sann så ellers||``-blokken og plasser kopien i det siste ledige heksagonet.
Endre ``||input.helning venstre||`` til ``||input.logo opp||``
Kopier ``||game.jeger endre x med -1||``-blokken og plasser kopien i gapet under heksagonet du nettopp redigerte.
Endre ``||game.x||`` til ``||game.y||`` og **-1** til **1**.
Om du nå sitter igjen med et ekstra, tomt gap i ``||logic.hvis sann så ellers||``-blokken, kan du fjerne det ved å trykke på det lille **-**-tegnet til venstre på armen over.

```blocks
let jeger: game.LedSprite = null
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        jeger.change(LedSpriteProperty.X, -1)
    } else if (input.isGesture(Gesture.TiltRight)) {
        jeger.change(LedSpriteProperty.X, 1)
    } else if (input.isGesture(Gesture.LogoDown)) {
        jeger.change(LedSpriteProperty.Y, -1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        // @highlight
        jeger.change(LedSpriteProperty.Y, 1)
    }
})
```

### Steg 15 Spillkontrolleren

Legg til en ``||basic.pause (ms) 100||`` blokk under ``||logic.hvis sann så ellers||``-blokken for at spillet skal kunne rekke å sjekke om spilleren har klart å fange byttet (du har ikke satt inn denne sjekken ennå, men du kommer til det ganske snart).
Nå er spillkontrolleren komplett, men vi mangler en ting. Spilleren må kunne score poeng.

```blocks
let jeger: game.LedSprite = null
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        jeger.change(LedSpriteProperty.X, -1)
    } else if (input.isGesture(Gesture.TiltRight)) {
        jeger.change(LedSpriteProperty.X, 1)
    } else if (input.isGesture(Gesture.LogoDown)) {
        jeger.change(LedSpriteProperty.Y, -1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        jeger.change(LedSpriteProperty.Y, 1)
    }
    // @highlight
    basic.pause(100)
    
})
```

### Score poeng @unplugged

Det siste som gjenstår er å legge til en måte å score poeng på.
Spilleren skal få et poeng hver gang de fanger et bytte.
For å fange byttet, må jegeren være på samme koordinat som byttet.
Her må du bruke en logisk løkke som hele tiden sjekker om de to er på samme koordinatpunkt.
Dette er en ganske infløkt sjekk, så her gjelder det å holde tunga rett i munnen.

### Steg 16 Score poeng

Hent en ``||logic.hvis sann så||``-blokk fra ``||logic.Logikk||``-menyen.
Plasser den nye blokken nederst i ``||basic.gjenta for alltid||``-blokken din.

```blocks
let jeger: game.LedSprite = null
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        jeger.change(LedSpriteProperty.X, -1)
    } else if (input.isGesture(Gesture.TiltRight)) {
        jeger.change(LedSpriteProperty.X, 1)
    } else if (input.isGesture(Gesture.LogoDown)) {
        jeger.change(LedSpriteProperty.Y, -1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        jeger.change(LedSpriteProperty.Y, 1)
    }
    basic.pause(100)
    // @highlight
    if (true) {
    	
    }
})
```

### Steg 17 Score poeng
Hent en liten ``||logic.[heksagon] og [heksagon]||``-blokk fra ``||logic.Logikk||``-menyen og plasser den i heksagonet på ``||logic.hvis sann så||``-blokken.
Denne koden sjekker om ***to*** tilstander er sanne samtidig.

```blocks
let jeger: game.LedSprite = null
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        jeger.change(LedSpriteProperty.X, -1)
    } else if (input.isGesture(Gesture.TiltRight)) {
        jeger.change(LedSpriteProperty.X, 1)
    } else if (input.isGesture(Gesture.LogoDown)) {
        jeger.change(LedSpriteProperty.Y, -1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        jeger.change(LedSpriteProperty.Y, 1)
    }
    basic.pause(100)
    // @highlight
    if (true && true) {
    	
    }
})
```

### Steg 18 Score poeng

Hent et ``||logic.0 = 0||``-heksagon fra ``||logic.Logikk||``-menyen og plasser det i det første heksagonet i ``||logic.[heksagon] og [heksagon]||``-blokken du nettopp satte inn.
Kopier ``||logic.0 = 0||``-heksagonet og plasser kopien i det andre heksagonet i ``||logic.[heksagon] og [heksagon]||``-blokken.
Koden du har satt inn nå legger til enda et logisk lag og sjekker om ***to og to*** tilstander er sanne samtidig.

```blocks
let jeger: game.LedSprite = null
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        jeger.change(LedSpriteProperty.X, -1)
    } else if (input.isGesture(Gesture.TiltRight)) {
        jeger.change(LedSpriteProperty.X, 1)
    } else if (input.isGesture(Gesture.LogoDown)) {
        jeger.change(LedSpriteProperty.Y, -1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        jeger.change(LedSpriteProperty.Y, 1)
    }
    basic.pause(100)
    // @highlight
    if (0 == 0 && 0 == 0) {
    	
    }
})
```

### Steg 19 Score poeng

Nå trenger du blokker som beskriver x- og y- posisjonene til en brikke hver for seg.
Finn en liten oval ``||variables.sprite||`` ``||game.x||`` i ``||game.Spill||``-menyen og sett den inn i det første hvite feltet i det første ``||logic.0 = 0||``-heksagonet.
Kopier ``||variables.sprite||`` ``||game.x||`` tre ganger og plasser en kopi i hvert hvite felt i de to ``||logic.0 = 0||``-heksagonene.
Nå får du kanskje en feilmelding, siden ``||variables.sprite||`` ikke er en definert variabel i programmet ditt.
Det gjør ingenting, for det retter du opp i neste steg.

```blocks
let jeger: game.LedSprite = null
let sprite: game.LedSprite = null
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        jeger.change(LedSpriteProperty.X, -1)
    } else if (input.isGesture(Gesture.TiltRight)) {
        jeger.change(LedSpriteProperty.X, 1)
    } else if (input.isGesture(Gesture.LogoDown)) {
        jeger.change(LedSpriteProperty.Y, -1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        jeger.change(LedSpriteProperty.Y, 1)
    }
    
    basic.pause(100)
    // @highlight
    if (sprite.get(LedSpriteProperty.X) == sprite.get(LedSpriteProperty.X) && sprite.get(LedSpriteProperty.X) == sprite.get(LedSpriteProperty.X)) {
    	
    }
})
```

### Steg 20 Score poeng

Nå skal du endre de siste blokkene du plasserte sånn at det er jeger- og byttebrikkenes posisjoner som sjekkes mot hverandre.
Endre den første ovale blokken der det står ``||variables.sprite||`` ``||game. x||`` til ``||variables.jeger||`` ``||game. x||`` ved å trykke på den lille pilen til høyre for ``||variables.sprite||`` og velge ``||variables.jeger||``.
I den neste ovale blokken klikker du på pilen til høyre for ``||variables.sprite||`` og velger ``||variables.bytte||``.
Nå sjekker den logiske løkken om begge brikkene har samme x-posisjon.

```blocks
let bytte: game.LedSprite = null
let jeger: game.LedSprite = null
let sprite: game.LedSprite = null
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        jeger.change(LedSpriteProperty.X, -1)
    } else if (input.isGesture(Gesture.TiltRight)) {
        jeger.change(LedSpriteProperty.X, 1)
    } else if (input.isGesture(Gesture.LogoDown)) {
        jeger.change(LedSpriteProperty.Y, -1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        jeger.change(LedSpriteProperty.Y, 1)
    }
    basic.pause(100)
    // @highlight
    if (jeger.get(LedSpriteProperty.X) == bytte.get(LedSpriteProperty.X) && sprite.get(LedSpriteProperty.X) == sprite.get(LedSpriteProperty.X)) {
    	
    }
})
```

### Steg 21 Score poeng

Nå skal du gjøre samme logiske sjekk for y-posisjonen til begge brikkene.
Endre den nest siste ovale blokken der det står ``||variables.sprite||`` ``||game. x||`` til ``||variables.jeger||`` ``||game. y||`` ved å trykke på den lille pilen til høyre for ``||variables.sprite||`` og velge ``||variables.jeger||`` og så trykke på den lille pilen til høyre for ``||game.x||`` og velge ``||game.y||``.
I den siste ovale blokken klikker du på pilen til høyre for ``||variables.sprite||`` og velger ``||variables.bytte||`` og så trykker du på den lille pilen til høyre for ``||game.x||`` og velger ``||game.y||``.
Nå sjekker den logiske løkken om begge brikkene også har samme y-posisjon.

```blocks
let bytte: game.LedSprite = null
let jeger: game.LedSprite = null
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        jeger.change(LedSpriteProperty.X, -1)
    } else if (input.isGesture(Gesture.TiltRight)) {
        jeger.change(LedSpriteProperty.X, 1)
    } else if (input.isGesture(Gesture.LogoDown)) {
        jeger.change(LedSpriteProperty.Y, -1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        jeger.change(LedSpriteProperty.Y, 1)
    }
    basic.pause(100)
    // @highlight
    if (jeger.get(LedSpriteProperty.X) == bytte.get(LedSpriteProperty.X) && jeger.get(LedSpriteProperty.Y) == bytte.get(LedSpriteProperty.Y)) {
    	
    }
})
```

### Steg 22 Score poeng

Dersom den logiske sjekken finner ut at ``||variables.jeger||`` og ``||variables.bytte||`` har samme x- og y-verdi, skal spilleren få et poeng og en ny runde begynne.
Hent en ``||game.endre poengsum med 1||``-blokk fra ``||game.Spill||``-menyen og plasser den i gapet på ``||logic.hvis sann så||``-blokken.
Nå får spilleren et poeng hvergang byttet blir fanget.
Hent blokken ``||functions.kjør nyRunde||`` fra ``||functions.Funksjoner||``-menyen og legg den inn i ``||logic.hvis sann så||``-blokken under ``||game.endre poengsum med 1||``-blokken.
Den siste blokken du satte inn i koden påkaller funksjonen ``||functions.nyRunde||`` som starter en ny spillrunde.
Spillet fortsetter å kjøre nye runder til tiden løper ut.

```blocks
let bytte: game.LedSprite = null
let jeger: game.LedSprite = null
function nyRunde () {
    bytte.set(LedSpriteProperty.X, randint(0, 4))
    bytte.set(LedSpriteProperty.Y, randint(0, 4))
    if (!(bytte.isTouchingEdge())) {
        nyRunde()
    }
}
let bytte: game.LedSprite = null
bytte = game.createSprite(0, 0)
let jeger = game.createSprite(2, 2)
bytte.set(LedSpriteProperty.Blink, 3)
jeger.set(LedSpriteProperty.Brightness, 5)
nyRunde()
game.startCountdown(10000)
basic.forever(function () {
    if (input.isGesture(Gesture.TiltLeft)) {
        jeger.change(LedSpriteProperty.X, -1)
    } else if (input.isGesture(Gesture.TiltRight)) {
        jeger.change(LedSpriteProperty.X, 1)
    } else if (input.isGesture(Gesture.LogoDown)) {
        jeger.change(LedSpriteProperty.Y, -1)
    } else if (input.isGesture(Gesture.LogoUp)) {
        jeger.change(LedSpriteProperty.Y, 1)
    }
    basic.pause(100)
    if (jeger.get(LedSpriteProperty.X) == bytte.get(LedSpriteProperty.X) && jeger.get(LedSpriteProperty.Y) == bytte.get(LedSpriteProperty.Y)) {
        // @highlight
        game.addScore(1)
        nyRunde()
    }
})
```

### Steg 23 Spillet er ferdig

Det var det hele! Nå kan du laste spillet opp til Micro:Biten og teste spillet. Husk at byttet blinker, mens jegeren lyser svakt hele tiden.

* for PXT/microbit
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
