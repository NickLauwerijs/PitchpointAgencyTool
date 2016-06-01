# website Fukushima
Mijn 2de opdracht was al wat groter als de eerste. Ik moest een website maken voor het nucleaire forum over Fukushima. 
## Gebruikte technologieën en tools.
Bij het ontwikkelen van deze website heb ik gebruik gemaakt van verscheidene technologieën en tools. 

### Gulp
Gulp is een build systeem die de ontwikkeling van websites kan verbeteren door het automatiseren van algemene taken zoals : compilen van preprocessed CSS (sass) , het minifyen van JavaScript , reloaden van de browser,...

De installatie gaat als volgt:
- Installeren van Node.js.
- Gulp installeren aan de hand van de package manager van Node.js genaamd npm.

Bij het gebruik van gulp hebben we een src (=source) folder en een build folder nodig. De source folder gebruiken we om alles in te coderen en in de build folder word alle gecompileerde code gezet door middel van gulp zijn streams. 

Gulp doet niet veel op zich maar maakt gebruik van plug-ins die men kan installeren om specifieke taken uit te voeren. Deze plugins kan men installeren via de npm package manager.
Hierna kan men taken declareren in de file 'gulpfile.js' die in de root van de website folder staat. De plug-ins die men wil gebruiken moeten toegevoegd worden bovenaan deze file , daarna worden de taken gedeclareerd. Een taak word opgebouwd in 3 delen :
1. Source files selecteren waarop taken moeten worden uitgevoerd.
2. Files die geselecteerd zijn worden door een pipe stream gestuurd die alle taken zal uitvoeren die gedeclareerd werden.
3. De aangepaste files zullen geplaatst worden in de build map.

In onze gulpfile hadden we verschillende taken :
- templates
 - Content nemen uit json file en in html file toevoegen zodat we 2 json files kunnen gebruiken één voor de franse en nederlandse versie van de content. Er worden nu 2 index.html files gegenereerd in de build map 1 fr en 1 nl.
 - Alle js files toevoegen aan 1 main.js.
- styles
 - Alle partials bundelen in 1 css file.
 - Sass omzetten naar css.
 - Autoprefix, produceert code zodat alles ook ondersteunt is door oudere browsers
- watch
 - voert styles en template taak uit als er iets verandert in de projectmap.

### Sass

Sass is een extentie van CSS3 , omdat web applicaties en websites uitgebreider worden met de jaren kunnen we gebruiken maken van deze css preprocessor om onze stylesheets onderhoudbaarder en gestructureerder te maken. Waarom ? Omdat Sass enkele nieuwe features aanbied die men momenteel niet kan gebruiken bij normale CSS , zoals :
- Variabelen:
Door deze feature kunnen we een aantal variabelen aanmaken die we zullen gebruiken doorheen het maken van de website zoals : kleuren ,fonts , margins , line-heights , breakpoints. Het handige aan deze feature is dat als de klant wilt dat bv. een kleur of bv de margins wilt veranderen dan moet dit maar op 1 plaats aangepast worden.

- Partials
Deze feature staat ons toe om onze stylesheets op te delen in verschillende delen zodat we onze css op een heel modulaire manier konden schrijven. Dit is mogelijk door partials aan te maken 
die allemaal worden toegevoegd aan een main.scss bestand op deze manier : `@import('filepath')`. De partials worden aangeduid met een _ voor hun naam zodat sass weet dat dit partials zijn en niet mee moeten gecompileerd worden. Wat er nu wel gecompileerd word is de main.scss file waarin alle partials worden toegevoegd. Zo maakten we voor alles dat logisch gescheiden kon worden van elkaar een partial , dit zorgt voor een overzichtelijker project. Het voordeel van alles te compilen in 1 file is dat het aantal HTTP requests enorm zal dalen tegenover al deze verschillende partials apart.

- Mixins
Omdat sommige css declaraties veel terugkomen kan men gebruik maken van mixins , dit zijn groepjes van css declaraties die men kan hergebruiken doorheen de website. 

- Extends
Met extend kan je de css declaraties van een klasse extenden naar een andere klasse. bv als je een button maakt dan kan je deze extenden en zo een groene en rode knop klasse maken die de button klasse extenden. Op deze manier moet je veel minder code schrijven.

### Susy

Susy is een set van Sass Mixins die dienen om een responsive grid op te stellen. Het leuke hieraan is dat je volledig zelf je grid definieert en dat susy al de nodige berekeningen doet. De sass compiler zal kijken naar de mixin definities in de susy bestanden en zal deze omzetten naar css.
De mixin die het meeste word gebruikt is de span mixin :
```
.picblock {

    @include span(4 of 12);
```

deze mixin word gebruikt om de breedte van een kolom te bepalen en word berekend aan de hand van de container mixin (wrapper).
Susy staat het toe om een aantal settings in te stellen zodat je het grid helemaal kunt afstellen naar jou wensen , hieronder enkele settings die aan te passen zijn:
```
$susy: (
  flow: ltr,
  math: fluid,
  output: float,
  gutter-position: after,
  container: auto,
  container-position: center,
  columns: 4,
  gutters: .25,
  column-width: false,
  global-box-sizing: content-box,
  last-flow: to,
  debug: (
    image: hide,
    color: rgba(#66f, .25),
    output: background,
    toggle: top right,
  ),
 );

```
### Tweenmax.js
Er waren enkele DOM elementen die geanimeerd moesten worden. Hierbij hebben we gebruik gemaakt van Tweenmax.js
Tweenmax.js is een javascript animatie library die onderdeel is van GSAP (Greensock Animation Platform) , Tweenmax is een uitbreiding van tweenlite.js. Om deze library te gebruiken steken we deze gewoon mee in de package.json file zodat deze mee word geinstalleerd met het npm-install command , hierna hoeven we deze enkel nog te requiren in de main javascript file en alles is gereed om gebruikt te worden. Waarom GSAP ? Omdat deze library goed gedocumenteerd en dus makkelijk in gebruik is en bovendien zijn de animaties ook heel soepel (hoge framerate) dit kan je makkelijk zien met deze tool [SpeedTest](http://www.greensock.com/js/speed.html)

Hoe werkt dit nu juist ? 
Een Tweenmax instantie zal 1 of meerdere properties van eender welk DOM object aanpassen over een bepaalde tijdsperiode.
Bv: 2 markers die op de map moeten 'vliegen'
```
TweenMax.fromTo([".map__pin",".map__pin"] ,0.7 , {top:"40%", opacity:"0", visibility:"hidden"} , {top:"54%", opacity:"1", visibility:"visible"} );
```
Dit stukje code zal het object aanspreken met het ID map__pin , en de properties :top:40% , opacity:0 en visibility:hidden veranderen naar top:54% , opacity:1 en visibility:visible over de tijd van 0.7 seconden.
Zoals je ziet is hier helemaal niet veel code voor nodig , waardoor ik tweenmax.js heel aangenaam vind om mee te werken.

Al de animaties die gebeuren op de website zijn getriggerd op een bepaalde scroll hoogte die word gemeten vanaf de bovenzijde van de pagina.



##  Verloop 
Hier vertel ik hoe het verloop is gegaan bij het maken van deze website , van begin tot einde (wat heb ik eerst gedaan ? en wat daarna ? ) + moeilijkheden/problemen








