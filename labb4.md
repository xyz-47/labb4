# Föreläsningar
### Felhantering
[Exceptios](https://kauplay.kau.se/media/t/0_7denai71)

I denna sektion går vi igenom felhantering, och hur du undviker att ditt program krashar. 


### Introduktion till UWP
[UWP Intro](https://kauplay.kau.se/media/t/0_zuu2aohh)

Detta är en kort introduktion till UWP där vi skriver ett enkelt hello-world program. 

### Grunder
[Grid](https://kauplay.kau.se/media/t/0_ymz7o6ri) | [Kontroller](https://kauplay.kau.se/media/t/0_zt3hgn6b) | [Händelser](https://kauplay.kau.se/media/t/0_8t3193u0) | [Händelser 2](https://kauplay.kau.se/media/t/0_haq9rnyy) | [Mer komplex layout](https://kauplay.kau.se/media/t/0_vl5layjc)

Denna sektion går igenom hur man positionerar kontroller i ett fönster. Vi går även igenom några enkla kontroller och två av de vanligaste händelserna (events). Slutligen tittar vi på en mer komplex layout, och hur man blir bättre på att bygga layouter. 

### Dialogrutor
[Meddelanden](https://kauplay.kau.se/media/t/0_974td6yz) | [Spara Fil](https://kauplay.kau.se/media/t/0_fai7c8jm) | [Öppna Fil](https://kauplay.kau.se/media/t/0_1car8qzn)

Här går vi igenom hur man presenterar olika meddelanderutor för användaren, som exempelvis kan visa information, ställa frågor och interagera med filsystemet. 

### Menyer
[Command Bar](https://kauplay.kau.se/media/t/0_3kgws96m)

Här går vi igenom command bars, vilket är en av de menyer som finns i UWP. 

### Klasser
[Video 1](https://kauplay.kau.se/media/t/0_obwhi5vi) | [Video 2](https://kauplay.kau.se/media/t/0_7aqab1tc)

Här går vi igenom grunderna i hur man konstruerar egna klasser. (dessa filmer är från visual studio 2019, men klasser fungerar samma, så onödigt att spela in igen)

### List och Dictionary
[Video](https://kauplay.kau.se/media/t/0_8akdkqon)

Här går vi igenom datatyperna List och Dictionary, som både används för att lagra listor av data. (dessa filmer är från visual studio 2019, men klasserna fungerar samma, så onödigt att spela in igen)

### UWP ListView
[Video](https://kauplay.kau.se/media/t/0_aoitxtr1)

Här går jag igenom kontroller för att visa information i listor. Lite annat format då jag var tvungen att spela in ljudet i efterhand. Hoppas det funkar ändå

### Local Storage
[Video](https://kauplay.kau.se/media/t/0_tdp2t0kg)

Här går jag igenom hur man läser filer på datorn, utan att behöva fråga användaren om lov, eller vilken fil den vill läsa från. Det går även att använda samma tekniker för att spara.

# Lab 4
Denna laboration går ut på att både **designa** och **implementera** ett affärssystem. Affärssystemet ska användas till en fysisk affär som säljer media (t.ex. böcker, cd-skivor, spel). Systemet ska användas av anställda i affären och kunna hantera både kassahantering och lagerhållning.

Börja med att rita upp en klasstruktur för programmet, med ett förslag på klassdiagram och beskrivning av klasser. När programmet sen är färdigprogrammerat ska du diskutera skillnaden mellan din design och den faktiska implementationen i rapporten. **Rapporten ska innehålla både ett klassdiagram före och efter programmet implementerades.**

**Det inlämnade programmet ska:**

- Vara implementerade i C#.NET med UWP, WPF eller WinForms som grafiskt bibliotek.
- Vara implementerade i .NET 6.0 eller nyare.
- Ska gå att köra på en svensk dator, med ett svenskt operativsystem.
- Ska inte under rimliga omständigheter krasha. Vi kommer att [monkey testa](https://en.wikipedia.org/wiki/Monkey_testing) alla program, men vi kommer inte göra underliga ändringar i exekveringsmiljön eller liknande. Hantera alla fel med exceptions.
- Vara användarvänliga, med tydliga och beskrivande felmeddelanden, och inte bryta allvarligt mot [Microsofts rekommendationer för gränssnittsprogrammering](https://docs.microsoft.com/en-us/windows/win32/uxguide/guidelines).
___
### Grundversion (för 3 poäng)
Följande funktionalitet ska finnas i systemet:

1. Lägga till nya produkter.
2. Ta bort produkter.
3. Lägga till en leverans av en eller flera produkter från grossist. Här räcker det med att antalet uppdateras, leveransen behöver inte loggas.
4. Försäljning av produkt

Systemet ska ha två separata vyer (t.ex. flikar eller fönster), en för **lagerarbete** och en för **kassabruk** (dock **max en instans** av varje vy). Vyerna ska båda ha en lättöverskådlig produktlista, och endast tillgång till relevant funktionalitet. Vyerna ska arbeta mot samma data som ni ska lagra i en **CSV-fil**. Vid försäljning ska varor kunna läggas till i en kundkorg innan köpet genomförs. Vid uppstart av programmet ska denna fil läsas in, och när programmet stängs av ska filen sparas. 

<ins>**Ni som använder UWP skall låta användaren av programmet välja fil med hjälp av FileOpenPicker då filhanteringen i UWP skiljer sig en hel del från WinForms och WPF.**</ins>
Databasen (CSV-filen) ska ligga i samma katalogstruktur som er källkod 
<ins>**(OBS! Gäller INTE er som använder UWP)**</ins>
så att den följer med när ni zippar projektet vid inlämning (inga hårdkodade absoluta sökvägar, men hårdkodade relativa sökvägar är ok). Kundkorgen är _tillfällig_ och behöver inte sparas till fil.

Tänk på att göra systemet så generellt som möjligt, och se till att det är estetiskt tilltalande och användarvänligt för butikspersonal utan dataerfarenhet.

Kontrollfunktioner ska finnas så att:

- Om någon försöker lägga till en ny vara i sortimentet med ett redan upptaget varunummer ska detta ej godkännas.
- Om någon i personalen försöker ta bort en vara ur sortimentet, och dess lagerstatus inte är noll, ska en dialogruta dyka upp om man verkligen vill ta bort varan. I dialogrutan ska det gå att svara Ja eller Nej.
- Man ska inte kunna sälja varor som inte finns på lager.
- Produkter får inte kunna ha felaktig information (exempelvis avsaknad av obligatoriskt fält, negativa priser, bokstäver i varunumret, en speltid som är negativ eller inte en siffra)
- Varje varunummer ska vara unikt.

**Produkterna i affären ska vara följande från start (* = obligatoriskt fält, grå bakgrund = ingen data från grossist):**

|**Böcker**||||||
|------|-|-|-|-|-|
|Namn* | Pris* |Författare	|Genre	|Format	|Språk
|Bello Gallico et Civili	|449	|Julius Caesar	|Historia	|Inbunden	|Latin|
|How to Read a Book	|149	|Mortimer J. Adler	|Kursliteratur	|Pocket	|
|Moby Dick	|49	|Herman Melville	|Äventyr	|Pocket	|
|Great Gatsby	|79	|F. Scott Fitzgerald	|Noir	|E-Bok	|
|House of Leaves	|49	|Mark Z. Danielewski	|Skräck		|
|**Dataspel**||||||
|Namn*	|Pris*	|Plattform|
|Elden Ring	|599	|Playstation 5|
|Demon's Souls	|499	|Playstation 5|
|Microsoft Flight Simulator	|499	|PC|
|Planescape Torment	|99	|PC
|Disco Elysium	|399	|PC|
|**Filmer**|
|Namn*	|Pris*	|Format	|Speltid|
|Nyckeln till frihet	|99	|DVD	|142 min|
|Gudfadern	|99	|DVD	|152 min|
|Konungens återkomst	|199	|Blu-Ray	|154 min|
|Pulp fiction	|199	|Blu-Ray	|
|Schindlers list	|99	|DVD|
