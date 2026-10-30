# En sak i taget – 2.0

Mobilanpassad PWA för en privat att göra-lista med ett fokusobjekt i taget. Inga externa tjänster behövs.

## Nytt i 2.0

- Urgent idag: en tillfällig markering som upphör automatiskt nästa dag.
- Överblick med upp-/nedknappar och drag-and-drop (dragning fungerar bäst på dator; använd pilar på mobilen).
- Återkommande uppgifter har valet **Visa tills den är klar** (för nya uppgifter påslaget; befintliga behåller tidigare beteende).
- Fokusläge med föregående/nästa, **Inte idag** och tidsfilter.
- Tidsåtgång krävs för aktiva uppgifter. Uppgifter som saknar tidsåtgång placeras i inkorgen.
- Projekt med arbetspass, som visas när vanliga uppgifter inte passar.
- Ingen gamification eller deadline i redigeringsformuläret.

## Uppdatering och data

**Exportera en säkerhetskopia i Inställningar före uppdatering.** Samma localStorage-nyckel som i 1.x används, så data finns normalt kvar på samma installerade app/ursprung. Vid första öppningen flyttas befintliga aktiva uppgifter som saknar tidsåtgång till inkorgen (inte borttagna). Gamla deadlines lämnas i säkerhetskopian men används inte för sortering. Personliga uppgifter och kontextnamn ligger bara i lokal lagring.

Ladda upp filerna i denna mapp i roten på ditt GitHub Pages-repository. Publicera från main / root. Öppna appen på mobilen och starta om den om gammal version ligger i cache.

## Utveckling

Kör `python3 -m http.server 8000` i mappen och öppna `http://localhost:8000`. Appen består av vanilla HTML, CSS och JS. Ingen build behövs.

## Kända begränsningar

- Ingen synk mellan enheter.
- iOS stöder inte alltid HTML drag-and-drop; använd flyttpilarna i överblicken.
- Ingen automatiserad webbläsartestsvit medföljer. Testa återkommande regler och import med säkerhetskopia innan du använder 2.0 skarpt.
