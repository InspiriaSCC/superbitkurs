### @activities true

# super:bit - Kodeøkt 3: Kjør Bit:Bot
## Introduksjon til hvordan du kjører Bit:Boten
### Introduksjon @unplugged

Lær hvordan du får BitBoten til å kjøre

### Steg 1 @unplugged

Egentlig må blokkene til Bit:Bot importeres til MakeCode, men siden dette er en såkalt tutorial, er blokkene du trenger allerede hentet inn, så du slipper å importere blokkene til Bit:Bot.
Når du senere skal bruke Bit:Bot må du hente inn blokker ved å hente dem inn fra "Utvidelser" i blokkemenyen.

### Steg 2

Nå skal du få bilen til å kjøre fremover.
Hent en ``||Bitbot.kjør framover med fart 60 % i 400 ms||``-blokk fra ``||Bitbot.Bitbot/Kjøring||`` og plasser den i ``||basic.ved start||``-blokken.

```blocks
// @highlight
bitbot.goms(BBDirection.Forward, 60, 400)
```

### Steg 3

Test programmet på BitBoten og følg med på hvor langt og fort den kjører.
Du kan endre på farten ved å endre tallet der det står ``||Bitbot.fart||`` 60 ``||Bitbot.%||`` og hvor lenge den kjører ved å endre tallet der det står ``||Bitbot.i||`` 400 ``||Bitbot.ms||``.
Test litt forskjellige tider og hastigheter for å få en følelse av hvordan innstillingene påvirker Bit:Boten.
(Blokkene i hintene i denne gjennomgangen gir ingen fasit på hvordan man treffer på 1 meter)

```blocks
// @highlight
bitbot.goms(BBDirection.Forward, 100, 1000)
```

### Steg 4

Mål opp 1 meter på gulvet og prøv å få Bit:Boten til å kjøre akkurat 1 meter før den stopper.
Endre tallene i kodeblokkene for å kontrollere kjørelengden.
Tips: Du får større kontroll ved lavere fart.
Endre kun på ett av tallene av gangen.
Da blir det mye enklere å vurdere hvordan endringen du gjorde påvirket kjørelengden.

```blocks
// @highlight
bitbot.goms(BBDirection.Forward, 60, 800)
```

### Steg 5

Nå skal du få Bit:Boten til å kjøre fram, snu seg rundt og kjøre tilbake til start.
For å snu roboten trenger du blokken ``||bitbot.snu til venstre med fart 60 % i 400 ms||`` fra ``||bitbot.Bitbot||``-menyen.
Legg den under ``||Bitbot.kjør framover med fart ?? % i ?? ms||``-blokken i koden din. Test ut hvilke tall som får Bit:Boten til å snu seg 180 grader.
Rekkefølgen på koden er viktig her. Programmet kjører instruksjonene i samme rekkefølge som blokkene ligger i ``||basic.ved start||``. 
Tips: For å spare tid kan du legge blokken som kjører Bit:Boten 1 meter rett fram utenfor ``||basic.ved start||``-blokken og kun prøve ut svingingen helt til Bitboten snur nøyaktig 180 grader rundt.


```blocks
bitbot.goms(BBDirection.Forward, 60, 400)
// @highlight
bitbot.rotatems(BBRobotDirection.Left, 60, 400)
```

### Steg 6

Du har allerede koden du trenger for å kjøre 1 meter.
Kopier blokken ``||Bitbot.kjør framover med fart ?? % i ?? ms||`` og legg den under snu-blokka, slik at bilen kjører fremover, snur og kjører tilbake.

### Avrunding @unplugged

Nå vet du hvordan du får Bit:Boten til å kjøre.
Da er du klar for å lære noen litt mer avanserte funksjoner på Bit:Boten.

```blocks
bitbot.goms(BBDirection.Forward, 60, 400)
bitbot.rotatems(BBRobotDirection.Left, 60, 400)
// @highlight
bitbot.goms(BBDirection.Forward, 60, 400)
```


```package
bitbot=github:4tronix/BitBot
```

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>


