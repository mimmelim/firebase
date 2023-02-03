# Firebase database
## Opprette prosjekt i firebase
Opprett en profil - eller logg inn på - [Firebase sine nettsider](https://firebase.google.com)


Gå til console etterpå (lenke oppe til høgre i vindu) - [Firebase sin konsoll](https://console.firebase.google.com)


Opprett et Firebase prosjekt ved å klikke 'Add project' i Firebase konsollen. Følg instruksjonene på skjermen.  

Disable Google Analytics hvis du ikke vil 'ha noe med dem å gjøre' :)

Velg 'Test mode' når du får valget mellom denne og 'Locked mode'. Test mode er gratis i en periode.
.
.
.
.
Husk å endre i fanen Rules: read og write skal settes til 'true', ikke 'false'!

## Secure your data
(Disse lenkene er muligens utdaterte. Endringer skjer hyppig hos firebase)

Se [rules tab nederst](https://firebase.google.com/docs/firestore/quickstart#web-version-9) på Firebase sin side.

Lær om oppstart i en [youtube-video](https://youtu.be/BjtxPj6jRM8)

## HTML-kode
Legg merke til at vi må sette type til module i script-taggen. Det er fordi firebase 9 er modulbasert. 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Firebase</title>
    <script src="firebaseV23.js" type="module"></script>
</head>
<body>
    <form action="#">
        <label for="fornavn">Skriv inn fornavn: </label>
        <input type="text" id="fornavn">
        <label for="etternavn">Skriv inn etternavn: </label>
        <input type="text" id="etternavn">
        <button type="button" id="leggTilKnapp">Registrer navn</button>
    </form>
    <p id="utskriftAvsnitt"></p>
</body>
</html>
 

## JavaScript-kode
   

