Rapport: laddningstid
=======================

Uppgiftens syftet är att analysera olika webbsidors prestation, det vill säga
bland annat laddningstid, storlek och hur mycket tid det tar innan
användaren kan se sidans primärt innehåll.

Urval
-----------------------

Eftersom syftet är att utvärdera och sätta ett betyg på laddningstiden, och den
påverkas av innehåll, jag tyckte det skulle vara ointressant att jämföra helt
olika webbsidor: en sångerskas sida som har
massor med bilder, ljud och specialeffekter tar självklart mer tid att ladda
än Försäkringskassans hemsida.
Då valde jag att analysera sidor skapade för samma branschen, nämligen
officiella turistinformation sidor: [Visit Umeå](https://visitumea.se/sv)
[Visit Stockhokm](https://www.visitstockholm.com/) och [Göteborg](https://www.goteborg.com/).
Det verkar som en utmaning att skapa en sida riktad till turister: å ena sidan
vill man ha en sida som laddar innehållet så snabbt som möjligt, å andra sidan
är det väldigt viktigt att locka potentiella turister med stora, högkvalitativa
bilder, då ska det vara intressant att se om det är just det som saktar ner
en sida eller om utvecklaren har hittat lösningar som gör sidan snygg men snabb
ändå.

Metod
-----------------------

Jag valde sidorna genom att skriva "visit" i Googles sökfältet och valde de 3 första
städer som dök upp. PageSpeed Insight (PSI), är verktyget som hjälte mig
att utvärdera en sidans genom att visa vad är det som saktar ner sidan,
hur mycket tid förloras och dessutom ger förslag om hur man kan fixa det.
Jag använder Google devtools och en extension som heter Page Size Inspector för
att få information kring sidans storlek.
För att skriva ner resultatet använde jag Google kalkylark. Jag också analyserade andra 10 webbsidor bara för att få en idé av vad
jag upplever som snabbt eller långsamt och jag bestämde mig att 7-10s (eller < 50
betyg på PageSpeed Insight) laddningstid är det långsamt, 5-6s (eller 51-79 betyg
på PageSpeed Insight) jag märker att sidan laddar inte "snabbt", men knappt.
mindre än 5s (eller 80-100 som betyg på PageSpeed Insight) upplever jag som väldigt snabbt.

Resultat
-----------------------

**Göteborg**

- PSI betyg (mobil) : 47
- PSI betyg (dator): 74
- laddningstid: 6s
- Storlek: 79,627 bytes.

Sidan fick det absolut värsta betyg och det är den "tyngsta" sidan bland de 3.
Det innehåller väldigt många bilder och mycket text och en inbyggd chatt.
Tiden för att få "First Meaningful Paint" (eller Första meningsfulla skärmuppritningen
på svenska), det vill säga tiden som tar för att sidans primärt innehåll visas,
är också ganska långt och det kan verkligen driva bort användare.
Ett par förslag är att minska responstiden på server och absolut, speciellt
när det gäller mobilsidan, optimera bilder och spara dom i nyare filformat.
WebP är till exempel en google produkt som ger 26% mindre filstorlek jämfört
med PNG, samt runt 25% mindre jämfört med JPG, och en webbsida med så mycket
innehåll kan säkert dra nytta av det.

[FIGURE src="img/gotet1.PNG"]
[FIGURE src="img/gotet2.PNG"]
[FIGURE src="img/gotet3.PNG"]
[FIGURE src="img/gotet4.PNG"]

**VisitUmeå**


- PSI betyg (mobil): 58
- PSI betyg (dator): 95
- laddningstid: 1.09 s
- storlek: 19,055 bytes

Sidan fick absolut bästa PSI betyget för webbbrowsern sida och en okej betyg
för mobilsidan, första meningsfulla skärmuppritningen är kort och får ett bra betyg
från PSI. Sidan för mobila enheter har lite värre betyg och möjliga lösningar
kan vara att spara filer i modernare bildformat, eller att skjuta upp inläsningen
av bilderna som är inte synliga i hemsidan. Det finns också en del oanvänd
CSS som möjligen saktar sidan ner av 0.6 sekunder och det skulle tas bort.
PageSpeed Insight också noterar att det finns saker som kan förbättras i Javascript filerna:
ett onödigt stort DOM-träd (1000+ element) och att det tar mycket tid att kompilera,
tolka och köra JS kod.

[FIGURE src="img/ume1.PNG"]
[FIGURE src="img/ume2.PNG"]
[FIGURE src="img/ume3.PNG"]

**visitstockholm**

- PSI betyg (mobil): 58
- PSI betyg (dator): 86
- laddningstid: 1.30 s
- storlek: 13,261 bytes

Sidan får ett bra betyg från PageSpeed Insight och ett okej betyg för vad det
gäller mobilversionen. Första meningsfulla skärmuppritningen dyker upp efter
1,4 s, som är inte det värsta men inte bra heller. Däremot första innehållet
dyker upp snabbt (0,5 s) som är väldigt bra för att få användare att stanna.
Mobilsidan har inget sådant problem istället, men har däremot mycket oanvänd
CSS som stör och långa körningstider för JavaScript.  
Någonting som kan fixas, är den stora nätverksbelastningen, och långa svarstiden
från servern.

[FIGURE src="img/sthlm1.PNG"]
[FIGURE src="img/sthlm2.PNG"]
[FIGURE src="img/sthlm3.PNG"]

Analys
-----------------------

Från resultaten vi kan se att en av de allra vanligaste problem när det gäller
desktopssidor är nätverksbelastning, stora DOM träd och onödig CSS. Vissa
problem med bilderna och server också dyker upp.
Faktorn som spelar störst roll i mobilsidornas laddningstid är i stället bilderna:
de skulle (enligt google tools och PSI) kodas i modernare bildformat, men det
låter inte möjligt just nu, många webbrowser stödjer inte (eller
bara vissa av) de nya format, och de "stora" browsers supporterar olika: chrome
stödjer bara WebP och APNG, Edge stödjer bara JpegXR och så vidare, och
att skapa olika bildfiler som visas i olika webbrowser låter möjlig men
jobbig och det troligen kommer skapa andra problem. Ett annat problem som förekommer
ofta är "onödiga" CSS regler som enligt PSI skulle tas bort (och det finns Javascript bibliotek som PurifyCSS som hjälper göra det).

Finala betyg är:

1. VisitUmeå

2. VisitStockholm

3. Göteborg



Referenser
-----------------------

[Page speed](https://moz.com/learn/seo/page-speed)
[Evaluate performance](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/timeline-tool)
[Jämforelse av bildformaten](https://www.metamatrix.se/aktuellt/jamforelse-av-bildformaten-webp-jpeg-2000-jpeg-xr-apng/)
[PurifyCSS](https://purifycss.online/)

Övrigt
-----------------------

Elisa Melis Gencten
