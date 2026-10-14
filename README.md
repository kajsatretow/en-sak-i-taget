# En sak i taget

En mobilanpassad, offline-kapabel PWA för privata uppgifter. Fokusvyn visar **en** lämplig uppgift åt gången. Ingen backend eller externa beroenden.

## Kom igång i VS Code

1. Öppna mappen `one-thing` i VS Code.
2. Starta en lokal webbserver, t.ex. med `python3 -m http.server 8000` i terminalen.
3. Öppna `http://localhost:8000` i webbläsaren.
4. För användning på mobilen: publicera mappen på en HTTPS-host, t.ex. GitHub Pages, och välj *Lägg till på hemskärmen* i mobilens webbläsare.

**Obs:** Öppna inte bara `index.html` via `file://` om du vill testa PWA/offline-läge. Service workers kräver HTTPS eller localhost.

## Funktioner

- Fyra redigerbara kontexter (Inställningar → Redigera kontexter), med namn sparade enbart lokalt; automatisk växling via redigerbart schema för varje veckodag, med manuellt val fram till nästa schemagräns.
- Uppgifter med flera kontexter, tre prioritetsnivåer, valfria startdatum och deadlines.
- Återkommande uppgifter: dagligen, flera valfria veckodagar, en dag i månaden eller X dagar efter slutförande. Missade tillfällen skapar inte dubbletter.
- Inkorg för snabb registrering och förslag om att organisera en uppgift när fokusvyn är tom.
- Fokus: Klart, Inte nu, Visa en annan. Uppgifter som hoppats över fem gånger erbjuds behåll/inkorg/ta bort.
- Aktiva, pausade och inkorg i administrationsvyn.
- Export/import av JSON-säkerhetskopia via kugghjulet.

## Viktigt om data

Data lagras **endast i localStorage på den aktuella enheten/webbläsaren**. Ingen synkronisering. Rensning av webbplatsdata kan radera uppgifterna. Exportera säkerhetskopia regelbundet.

## Tekniska anteckningar

- `app.js`: tillstånd, datamodell, prioritering, kontextschema, återkommande uppgifter och UI.
- `styles.css`: mobilförst-design.
- `sw.js`: cache för offlineanvändning.
- `manifest.webmanifest`: installationsmetadata.
- `index.html`: appens skal och redigeringsdialog.

## Kända begränsningar / nästa steg

- Ingen molnsynk, notifieringar eller testsvit ännu.
- Veckoschemat är ett initialt **exempel**; justera tiderna i appen.
- Fokusvalen *Inte nu* och *Visa en annan* har i v1 samma effekt: hoppa över uppgiften under aktuell kontextsession.
- Den manuella kontexten återställs vid nästa schemagräns. Om schema saknar framtida gräns återställs den vid midnatt.
- Klara engångsuppgifter lagras i data men visas inte i listan.
- Poängmodellen för prioritering finns i `score()` och kan finjusteras.

**Integritet:** Kontextnamnen i GitHub-koden är generiska. Ändra dem i appens inställningar på mobilen. Befintliga lokalt sparade uppgifter och kontextval behålls vid uppdatering. Om personnamn redan har publicerats i tidigare commits kan de finnas kvar i Git-historiken även efter denna uppdatering.

## Färger i version 1.3
Accentfärgen är magenta (#b12b83) och bakgrunden är kall lavendelgrå (#f3f1f8). Färginställningarna finns i `styles.css`; appikonen i `icon.svg`.
