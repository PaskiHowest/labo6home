# LaboReeks Git
## **Labo 6**

In dit zesde labo gaan we aan de slag met een eenvoudige GitHub action (.NET build) en enkele van de besproken commando's voor git fixes.
We zullen ook in dit labo weer een lokale repository clonen waar we vervolgens alle lokale wijzigingen gaan synchroniseren met deze remote git repository (GitHub). 

Je eindresultaat van het labo zal op deze manier automatisch in deze GitHub repository terecht komen.
Met andere woorden, voor dit labo **upload je niks manueel** op GitHub! 

Alles wat gevraagd wordt, dien je lokaal toe te voegen en vervolgens via de nodige commando's ook in de online repository te brengen.
Indien er GitHub-specifieke features gevraagd worden dan kan/moet je deze uiteraard uitvoeren op de remote repository zelf.
Dit zal aangeduid worden op de taken die van toepassing zijn op GitHub-specifieke features.

#### **Aanvullende toets op Leho**
Na het afwerken van dit labo heb je op Leho een aanvullende toets met betrekking tot het labo en de leerstof gekoppeld aan het labo.
Je kan/mag de aanvullende toets steeds afleggen gebruik makend van alle bronnen (cursusmateriaal, labo, online bronnen, ...)

### **Labo 6:** *Voorbereiding*

We maken in dit labo een eenvoudige .NET 6 console applicatie geïnspireerd door de iconische film [Monty Python and the Holy Grail](https://www.imdb.com/title/tt0071853/).
In deze remote repo zijn al enkele commits op verschillende branches aanwezig.
Sommige commits gebeurden echter niet op de juiste branches, dat zullen we straks rechtzetten.
Ter voorbereiding voegen we eerst de standaard .NET build actie toe zoals besproken in de cursus.

- [ ] Voeg **op GitHub** via de **Actions** tab de standaard .NET workflow toe die ervoor zorgt dat de code automatisch gecompileerd wordt telkens er een nieuwe commit naar de master branch wordt gepusht.
- [ ] **Opgelet:** de .NET build workflow gebruikt standaard nog .NET 5, maar de console applicatie in deze repo maakt reeds gebruik van .NET 6. **Pas dus het .NET versienummer aan in het build script dat voor je wordt aangemaakt.**

```yaml
- name: Setup .NET
  uses: actions/setup-dotnet@v2
  with:
    dotnet-version: 6.0.x
``` 
- [ ] Commit het GitHub actions script direct naar de `master` branch.
- [ ] Laat de actie lopen en verifieer dat de code op de master branch foutloos kan builden.

### Deel 1: remote repo clonen

- [ ] Open de Git Bash Console op de locatie waar je dit labo wil gaan clonen. Dit kan via een rechtermuisklik op de locatie in kwestie en vervolgens de keuze **Git Bash Here** te selecteren.
- [ ] Zorg ervoor dat de startsituatie *(deze repository)* van het labo op jouw pc **gecloned** wordt. Maak hiervoor gebruik van het passende git commando. 
- [ ] Ga **na het clonen** via de Console naar de gecloonde repository. Dit kan/mag je uiteraard ook doen door de nieuwe aangemaakt folder aan te klikken en hier opnieuw een Git Bash console te openen via de **Git Bash Here** optie.
>**Tip!** Controleer voor je verder werkt of je al dan niet in de juiste git repository zit! Je kan dit snel visueel vaststellen in je console.

### Deel 2: "What is your name?"

Het doel van de console applicatie is om drie vragen te stellen aan een ridder die de "Bridge of Death" wil oversteken.
Als eerste vragen we om de naam van de ridder.
De code die we hiervoor moeten toevoegen, is al uitgewerkt op de branch `feature/ask-name`.
Echter is per vergissing al een gelijkaardige aanpassing gebeurd rechtstreeks op de `dev` branch...
Die aanpassing rechtstreeks op `dev` zullen we eerst ongedaan maken, waarna we de feature branch gaan mergen.

- [ ] Ga lokaal in Git Bash naar de `dev` branch.
- [ ] Open de .NET solution `Cib.Labo6.Holy.Grail.sln` in Visual Studio.

In `Program.cs` zou je onderstaande code te zien moeten krijgen:

```c#
Console.WriteLine("Answer these three questions to cross the Bridge of Death!");


// Question 1
Console.WriteLine("What's your name?");


// Question 2
// ...


// Question 3
// ...
```

- [ ] Zoek uit (via Git Bash of op GitHub) in welke commit de eerste vraag *"What's your name?"* werd toegevoegd.
- [ ] Gebruik een gepast git commando om bovenvermelde commit **volledig ongedaan** te maken op de `dev` branch.
      Zorg ervoor dat er **geen sporen** meer overblijven van deze commit in de git history.
- [ ] Verifieer in Visual Studio dat de vraag *"What's your name?"* verdwenen is.

- [ ] Synchroniseer je lokale `dev` branch naar de remote.

> **Tip!** Aangezien je hebt zitten knoeien met de git history in je lokale repo, zal je hier iets extra moeten doen om de nieuwe history door te kunnen sturen naar de remote.
  
- [ ] Check lokaal even de branch `feature/ask-name` uit, zodat ze lokaal ook beschikbaar wordt.
- [ ] Keer meteen terug naar de branch `dev`.
- [ ] Merge nu lokaal de branch `feature/ask-name` in `dev`.
- [ ] Verifieer dat (de lichtjes anders geformuleerde vraag) *"What is your name?"* nu terug in de console applicatie beland is via de merge.
- [ ] Synchroniseer met de remote repo.

### Deel 3: "What is your favourite colour?"

- [ ] Ga in Git Bash naar de branch `feature/ask-favourite-colour`.
- [ ] Open terug de .NET solution (indien deze niet meer open staat) en bekijk `Program.cs`.

```c#
Console.WriteLine("Answer these three questions to cross the Bridge of Death!");


// Question 1
Console.WriteLine("What's your name?");


// Question 2
Console.WriteLine("What is your favourite colour?");


// Question 3
Console.WriteLine("What is the airspeed velocity of an unladen swallow?")
```

Zoals je ziet, werd op deze branch de tweede vraag *"What is your favourite colour?"* toegevoegd, zoals de naam van de branch ook aangeeft.
Echter werd per vergissing ook al de derde vraag *"What is the airspeed velocity of an unladen swallow?"* toegevoegd.

- [ ] Zoek uit (via Git Bash of op GitHub) in welke commit de derde vraag *"What is the airspeed velocity of an unladen swallow?"* werd toegevoegd. Noteer de **commit hash**.
- [ ] Keer terug naar de `dev` branch.
- [ ] Maak vanaf `dev` een nieuwe branch `feature/ask-swallow-airspeed` en ga meteen ook naar deze nieuwe branch.
- [ ] Gebruik het gepaste git commando om de commit die je hierboven identificeerde over te zetten op de branch `feature/ask-swallow-airspeed`.
- [ ] Verifieer in Visual Studio dat vraag 3 nu in je console applicatie beland is, maar vraag 2 nog **niet**, op de actieve branch `feature/ask-swallow-airspeed`.
- [ ] Synchroniseer de branch `feature/ask-swallow-airspeed` met de remote.

- [ ] Keer lokaal terug naar de branch `feature/ask-favourite-colour`.
- [ ] Maak de commit die vraag 3 onbedoeld toevoegde in deze branch ongedaan, **met behoud** van de reeds bestaande git history.
- [ ] Verifieer in Visual Studio dat vraag 3 nu verdwenen is, terwijl vraag 2 behouden werd.
- [ ] Synchroniseer `feature/ask-favourite-colour` met de remote.

- [ ] Keer terug naar de `dev` branch.
- [ ] Merge lokaal `feature/ask-favourite-colour` in `dev`.

> **Opgelet:** dit zal een merge conflict veroorzaken, omdat we eerder op `dev` hebben zitten knoeien met de git history, **nadat** de branch `feature/ask-favourite-colour` al van `dev` was afgetakt.

- [ ] Los het merge conflict op. We willen de vraagstelling *"What is your name?"* behouden, dus **niet** de alternatieve vraagstelling ~"What's your name?"~.
- [ ] Synchroniseer `dev` met de remote.

### Deel 4: "What is the airspeed of an unladen swallow?"

![](https://y.yarn.co/da1c8b0b-02d3-494f-a2dc-d43019bc7158_text.gif)

- [ ] Merge tot slot nu ook `feature/ask-swallow-airspeed` in `dev` om de vragenlijst te vervolledigen.
- [ ] Verifieer in Visual Studio dat alledrie de vragen nu aanwezig zijn.
- [ ] Synchroniseer `dev` met de remote.

### Deel 5: release van dev naar master

Tijd om onze applicatie te releasen!

- [ ] Ga lokaal naar de `master` branch.
- [ ] Merge `dev` in `master`.
- [ ] Synchroniseer `master` met de remote.

- [ ] Bekijk op GitHub het resultaat van je .NET build workflow. Wacht tot deze klaar is, je zal zien dat de build faalt.
- [ ] Bekijk je code lokaal in Visual Studio (nog steeds op de `master` branch). Je zal zien dat er een `;` vergeten werd bij de laatste vraag.

```c#
...

// Question 3
Console.WriteLine("What is the airspeed velocity of an unladen swallow?")
```

### Deel 6: hotfix

We gaan dit probleem oplossen via een hotfix.

- [ ] Maak een branch `hotfix/compile-error` vanaf `master` en ga meteen naar deze nieuwe branch.
- [ ] Pas de code aan door op het einde een `;` toe te voegen.

```c#
...

// Question 3
Console.WriteLine("What is the airspeed veloctiy of an unladen swallow?");
```

- [ ] Bewaar en commit je wijziging.
- [ ] Synchroniseer `hotfix/compile-error` met de remote.

- [ ] Ga nu lokaal terug naar de `master` branch.
- [ ] Merge `hotfix/compile-error` in `master`.
- [ ] Synchroniseer `master` met de remote.

- [ ] Wacht tot de GitHub action weer klaar is en verifieer dat de build nu terug slaagt.

- [ ] Merge tot slot `master` in `dev` zodat de hotfix ook wordt opgenomen in de huidige development versie.
- [ ] Synchroniseer een laatste keer `dev` met de remote.

