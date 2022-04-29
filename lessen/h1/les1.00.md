---
tags: vwo4, h1 
---

# Les 1.01 - Programmeren in C
In hoofdstuk 0 hebben we gekeken naar hoe computers werken en hoe we ze kunnen gebruiken om onze problemen op te lossen. Ook is er geïntroduceerd hoe je programeert, dit hebben we toen gedaan door het slepen van blokjes en het invullen van wat waardes. Nu gaan we werken met ons toetsenbord, dit doen we in dit hoofdstuk in de **programeertaal C**. Kijk bijvoorbeeld in het venster onder dit paragraaf, hier zie je een programma geschreven in de taal C

<iframe src="https://replit.com/@126511/les00-hallo?lite=true" frameborder="0" width="100%" height="500px"></iframe>
  
:::    warning
**1. Druk op de groene pijl bovenin, als het goed is zie je onderin het donkerblauwe venster `Hallo!` verschijnen.**
:::
## Programmeren en uitvoeren
De code, geschreven in de taal C, heeft als functie het uitprinten van de tekst `Hallo!`. Waarom dit werkt en hoe je zelf zo'n programma maakt leren we in Les 1. Voor programma's gebruiken we vanaf nu (bijna) altijd ReplIt. Dit is een online **IDE** (Integrated Development Environment): een programma waarmee je de code kan aanpassen en je met commando's je programma uitvoeren. Als je weer even naar de Repl hierboven kijkt zie je een wit venster (de **editor**) met daarin 6 regels aan code. Daaronder is een blauw venster (de **terminal**) met nu `Hallo!` (dit heb je in Opdracht 1 gedaan). Je ziet dat er voor de output twee commando's staan. De eerste ziet er ongeveer zo uit: `clang-7 -o main main.c` en de tweede zo `./main`.

In Hoofdstuk 0 hebben we het gehad over de taal die computers spreken: binair. Deze taal bestond alleen maar uit 1 en 0. Het programma in het witte venster, ook wel de text-editor genoemd, snapt de computer dus niet. We hebben nu C-code en dat moet vertaald worden naar 0 en 1, dit doet een **compiler**. Je stopt er een bepaalde taal in, dit noem je de **source code**. De compiler vertaalt dat tot **machine code**: enen en nullen. Dit begrijpt de computer wel.
De compiler die ReplIt gebruikt heet *Clang*. De stukjes tekst erachter zorgen ervoor dat Clang weet wat hij moet gaan vertalen en hoe hij het nieuwe bestand moet noemen (met daarin de binaire code). Hoe dit werkt en waarom het werkt maakt voor nu niet uit, de Run-knop doet het allemaal automatisch voor je! Daarna zie je het commando `./main` staan. De computer zoekt in het huidige mapje het bestand `main` (dat heeft de compiler zojuist gemaakt) en voert het uit.

:::warning
:question: Hoe heet de vertaler die van source code machine code maakt? 
::: spoiler Antwoord
Compiler
:::info
:::

:::warning
**2. Typ zelf is in de terminal `./main`: als het goed is zie je als output weer `Hallo!`.**
:::spoiler :bulb: Tip
Als er een error komt zoals "Permission denied", moet je eerst het programma runnen via de Run-button. Dan compilet het programma, zodat jij het vervolgens kan runnen.
:::

::: warning
**3. Vanaf volgende les gaan we ook zelf programmeren, hiervoor heb je een account nodig bij ReplIt, dit is volledig gratis. Voer de stappen op deze pagina uit zodat jij vanaf nu ook zelf kan gaan programmeren!**
:::

::: danger
:exclamation: Om de volgende lessen te kunnen doen, MOET je een ReplIt account hebben. Die maak je aan in opdracht 3.
:::

Als je nu weer op `open in Replit` drukt kan je op `fork` drukken. Fork betekent dat jij de Repl die wij voor je hebben gemaakt kopieert, zodat je hem zelf kan aanpassen. Ook hier kan je op Run drukken en in de terminal commando's typen. Je kan nu ook de code aanpassen. 

:::warning
**4. Fork de Repl en vervang `printf("Hallo!\n");` door `printf("Welkom!\n");`. Als je nu op Run drukt zie je dat het programma "Welkom!" uitprint.**
:::

:::warning
:question: Welke term drukt het kopiëren van een stuk code uit zodat jij het voor jezelf kan aanpassen uit?
:::spoiler Antwoord
Fork
:::

## Het programmeerproces
Dadelijk ga je aan de slag met je allereerste programmeeropdracht! Tijdens het programmeren is het belangrijk om dit stappenplan in je achterhoofd te houden.
1. De broncode (source code) schrijven.
2. De broncode compileren.
3. Fouten verbeteren en stap 1 en 2 herhalen.
4. De broncode uitvoeren.
5. Fouten en ongewenst gedrag (bugs) verbeteren en het hele proces herhalen.

Hoe je de broncode schrijft leer je in de komende lessen. Het compileren van de broncode die je via de Run button in Replit. Het kan zijn dat er een foutje in je code zit, waardoor de compiler het programma niet snapt, er komt dan een error. Deze errors zijn vaak cryptisch omschreven, probeer er chocola van te maken of vraag je docent om hulp. Later gaan we in meer detail kijken naar foutmeldingen. Als er geen foutmeldingen zijn (gefeliciteerd!) voert de Run button je broncode uit. Nu is het aan jou de taak om erachter te komen of het programma werkt zoals het hoort. Dit doe je door te bedenken wat de output zou moeten zijn en vervolgens kijkt wat de daadwerkelijke output is.

:::warning
**4. Fork onze Repl zodat jij hem kan aanpassen en pas het aan zodat hij niet meer "Hallo!" print maar "Gegroet, gebruiker!" Lever deze opdracht in. Weet je niet hoe dat moet? Kijk dan op deze pagina.**
:::

[toc]
