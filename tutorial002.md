### @activities true

# super:bit - Kodeøkt 2: Lag en enkel terning 
## Introduksjon
### Introduksjon @unplugged
I denne delen lærer du hvordan du får Micro:Bit til å reagere på en handling, det kalles inndata.


### Steg 4: Superenkel terning
Du kan bruke det innebygde akselerometeret i Micro:Bit til å simulere terningkast.
Gå til ``||input.Inndata||``-menyen og hent blokken ``||input.når ristes||``.
Denne blokkene er en slags startblokk.
Dra den gamle startblokken ut i papirkurven til venstre.

```blocks
input.onGesture(Gesture.Shake, function () {
	
})
```

### Inndata @unplugged

Det finnes flere måter å gi inndata til Micro:Bit på.
Micro:Bit har:<br>
* innebygde sensorer for lys og temperatur<br>
* digitalt kompass<br>
* akselerometer<br>
* 2 knapper som kan brukes hver for seg eller sammen<br>
Alle disse kan brukes som inndata.
I tillegg har Micro:Bit radio og en kontaktstriper som kan ta imot elektroniske signaler.

### Steg 5: Terning uten å lagre variabel
Fra ``||basic.Basis||``-menyen trenger du nå blokken ``||basic.vis tall||``.
Dra den inn i ``||input.når ristes||``-blokken.
Hent en ``||math.velg tilfeldig 0 til 10||``-blokk fra ``||math.matematikk||``-menyen.
Dra den inn i det hvite feltet i ``||basic.vis tall||``-blokken og endre tallene 0 og 10 til 1 og 6.
Micro:Biten viser nå et tilfeldig tall fra og med 1 til og med 6 når den ristes.
Du kan trykke på **"Shake"**-knappen like over B-knappen i simulatoren for å sjekke at koden fungerer. 

```blocks
input.onGesture(Gesture.Shake, function () {
    // @highlight
    basic.showNumber(randint(1, 6))
})
```

### Ferdig! @unplugged
Gratulerer! Du har nå laget en terning ved hjelp av to linjer kode!
Du kan starte terningkastet ved hjelp av andre typer inndata når du er ferdig med denne veiledningen.
Kanskje du får til å kaste terning med et knappetrykk?





* for PXT/microbit
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
