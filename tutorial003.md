### @activities true

# super:bit - Kodeøkt 6: Lag en hoppeteller 
## Introduksjon
### Introduksjon @unplugged

Micro:Biten kan fint brukes i forbindelse med fysisk aktivitet.
Her lærer du å bruke Micro:Biten som skritteller eller hoppeteller.
Akselerometeret i Micro:Biten kan brukes på flere måter.
I økten lærer du hvordan du velger akselerometerfunksjon fra en meny.
Du kan så teste ut hvilken funksjon du mener fungerer best som skritteller eller hoppeteller.

### Registrering av inndata krever en variabel @unplugged

For å kunne registrere inndata trenger du en variabel som kan lagre inndatahendelser.
I dette eksempelet vil en hendelse være ett hopp eller ett skritt, og variabelen skal lagre antall hendelser.
For å lage en skritt- eller hoppeteller må du i tillegg lage en løkke som sjekker variabelen med jevne mellomrom og viser verdien i displayet.

### Steg 1: Lag en variabel og gi den en startverdi

Første steg er å lage variabelen.
Klikk på ``||variables.variabler||`` og velg "Lag en variabel". Gi variabelen navnet "hopp".
Hent blokken ``||variables.sett hopp til||`` fra ``||variables.variabler||``-menyen og legg den inn i ``||basic.ved start||``-blokken.
La variabelen ha verdien 0 i starten av programmet.
Da starter programmet alltid på 0 skritt eller hopp.

```blocks
let hopp = 0
```

### Steg 2: Hent inndata og lagre dem i variabelen

Gå til ``||input.Inndata||``-menyen og hent blokken ``||input.når ristes||``.
Hent blokken ``||variables.endre hopp med 1||`` fra ``||variables.Variabler||``-menyen og dra den inn i ``||input.når ristes||``-blokken.
Nå vil verdien til variabelen ``||variables.hopp||`` øke med 1 hver gang Micro:Biten ristes.

```blocks
// @highlight
input.onGesture(Gesture.Shake, function () {
    hopp += 1
})
let hopp = 0
```

### Steg 3: Vis verdien til variabelen i displayet

Foreløpig har du ikke laget noen form for utdata, så det går ikke an å se hvor mange hopp du har gjort selv om de registreres.
Om du ikke har en ``||basic.gjenta for alltid||`` i arbeidsområdet, gå til ``||basic.Basis||``-menyen og hent en.
Hent en ``||basic.vis tall||``-blokk fra ``||basic.Basis||``-menyen og dra den inn i ``||basic.gjenta for alltid||``.
Hent variabelen ``||variables.hopp||`` fra ``||variables.Variabler||``-menyen og dra den inn i det hvite feltet i ``||basic.vis tall||``-blokken.

```blocks
input.onGesture(Gesture.Shake, function () {
    hopp += 1
})
let hopp = 0
// @highlight
basic.forever(function () {
    basic.showNumber(hopp)
})
```

### Steg 4: Andre måter å registrere hopp og skritt på

Dette programmet kan brukes både som hoppeteller og skritteller.
Det kan hende at ``||input.når ristes||`` ikke alltid registrerer skritt like godt.
Da kan det lønne seg å prøve en av de andre mulighetene for inndata fra akselerometeret.
En som gjerne fungerer fint til skrittellere er ``||input.3 G||``.
``||input.3 G||`` er gjemt i samme blokk som ``||input.når ristes||``.
Klikk på den lille pilen til høyre for ``||input.ristes||`` i ``||input.når ristes||``-blokken.
Velg ``||input.3 G||`` fra menyen som dukker opp.
Som du ser finnes det mange mulige akselerometerinndata.
Et eksempel kan være om du bygger Micro:Biten inn i en ball, godt polstret så den ikke blir ødelagt.
Da kan den registrere antall ballkast opp i luften dersom du bruker ``||input.fritt fall||`` i stedet for ``||input.når ristes||``.

```blocks
// @highlight
input.onGesture(Gesture.ThreeG, function () {
    hopp += 1
})
let hopp = 0
basic.forever(function () {
    basic.showNumber(hopp)
})
```

### Steg 5: Det var alt!

Nå har du lært noen triks du kan gjøre med akselerometeret i Micro:Bit.
Om du bruker fantasien, kan du sikkert finne mange andre spennende måter å bruke akselerometeret på.

* for PXT/microbit
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
