# CarbonViewer

**NOTE**: The application supports both the English and Norwegian language. To change the language, click on the `Change language` box and choose `en` for English or `no` for Norwegian. 

**MERK**: Applikasjonen støtter både engelsk og norsk. For å endre språk, klikk på `Endre språk`-boksen og velg `en` for engelsk eller `no` for norsk.

Description of CarbonViewer in [English](#what-is-the-carbonviewer)

Beskrivelse av appen på [Norsk](#hva-er-carbonviewer)

---

## Hva er CarbonViewer

**CarbonViewer** er en [R Shiny](https://shiny.rstudio.com/)-applikasjon som beregner og visualiserer karbonmengde i torvlaget for et gitt areal av myr-naturtyper. Kalkulatoren estimerer det totale karboninnholdet bundet opp i organisk jord som kan frigjøres som atmosfærisk karbondioksid (CO2) dersom arealet blir påvirket. Utbygging i myr kan gi høye klimagassutslipp og formålet med kalkulatoren er å gi beslutningstakere et bedre kunnskapsgrunnlag om karbonet som er bundet opp i torv. Kalkulatoren bør brukes i tidlig planlegging og som et verktøy for å kartlegge jordbundet karbon i myr. Dette for å unngå utbygging i karbonrike områder og minimere klimagassutslipp fra naturinngrep.

## Hvordan bruker jeg denne applikasjonen?

### Lage kartene

**Etter å ha fulgt alle trinnene beskrevet nedenfor, klikk på fanen `Resultater` for å visualisere resultatene**

- I menyen 'volumberegning' må brukeren laste opp en 'zip'-fil som inneholder både en 'shapefil' som avgrenser det aktuelle området og en 'csv'-fil med torvdybder (m), samt koordinater (gitt i UTM 32 N, EPSG:25832) for hvert prøvepunkt tatt i det aktuelle området. En eksempelfil for notering av torvdybder vises nedenfor. Torvdybder bør- for best mulig resultat - bli tatt med regelmessige intervaller med maksimum avstand på 20m mellom hvert punkt (for mindre myrarealer bør en avstand på mindre enn 20m benyttes).

- Brukeren kan deretter klikke på `Last inn datasett`. Etter noen sekunder vil et kart over området vises. Det totale arealet (i m2) beregnes.

- Hvis kartet som beskriver området er riktig, klikk på `Beregn volum`. Dette er en funksjon som beregner det totale volumet (m3) for hele området basert på tordybdene ved bruk av interpolering. Etter noen sekunder eller minutter (avhengig av størrelsen på området ditt og antall prøvepunkter) vil et kart vises. **Merk** at en fremdriftslinje vises nederst til høyre i applikasjonen.

- Når volumberegningen er utført, vises et relieff-kart med de interpolerte torvdybdene. Beregnet totalvolum av torv vises i topp-panelet.

### Beregning av total karbonmengde i området

Det siste trinnet beregner den totale karbonmengden i det aktuelle området. Brukeren kan legge inn egne data med torvegenskaper dersom dette er tilgjengelig. Alternativt velger brukeren å benytte data for karboninnhold fra en innebygd database. Når du klikker på `Torvegenskaper`, tilbys de to alternativene:

- 1) `Standardverdier`: Når dette alternativet er valgt, trenger brukeren kun å velge myrtype for området. Her vil brukeren få flere alternative detaljnivåer for myrtype, gitt den kunnskapen som brukeren innehar om det angitte området. Beregningen av karbonmengden baseres på eksisterende data for **massetetthet**, og **andel organisk materiale** for oppgitt myrtype, samt standardverdi på 0.5 for **andel karboninnhold i organisk materiale** (se artikkel for kilder).

- 2) `Egendefinerte verdier`: Dette alternativet forutsetter at brukeren kjenner verdiene for **massetetthet** (i g/cm3 eller tonn/m3, vanligvis mindre enn 1 og ofte så lite som 0.1 for myr), **andel organisk materiale** (verdi 0-1) og **andel karboninnhold i organisk materiale** (verdi 0-1) i det aktuelle området eller ønsker å teste datasettet med egne inngangsverdier. Her er det mulig å legge inn egne tall. Når tallene er lagt inn, kan brukeren klikke på "Last inn verdier".

Den totale karbonmengden (kg) i området vises øverst til høyre i applikasjonen.

### Last ned dataene

Når volumet er beregnet, er det mulig å laste ned kartfigurer. Videre vil resultater fra karbonberegningen bli tilgjengelig ved neste steg i kalkulatoren.
I applikasjonen kan brukeren klikke på `Last ned resultater` og `Last ned`. Dette vil returnere en `.zip`-fil som inneholder:

- `map_descriptive.png` : et kart over området med punkter for dybdemål.
- `map_interpolation.png` : et kart med interpolerte torvdybder.
- `interpolation_raster.tif` : et raster av resultatet fra volumberegningen - klar til bruk i enten **QGIS eller ArcGIS!**
- `results.csv` : en csv-fil med resultater fra volum- og karbonberegningene.

---

## What is the CarbonViewer

**CarbonViewer** is a [R Shiny](https://shiny.rstudio.com/) application designed to calculate and visualize the amount of carbon stored in a given peatland area. 
The application estimates the total carbon content in the peat body, which can be used to evaluate the soil carbon storage at any given peatland site and the potential impact land-use change can have on CO2 emission. As development in peatland areas may give cause to high greenhouse gas emissions, the aim of this application is to support area planners with an improved knowledge base of the soil carbon in potentially impacted areas. The application should be applied during early planning phases as a tool to map soil carbon stocks in peatlands, to avoid, reduce or mitigate the impact of development in peatlands areas.

## How to use this application?

### Creating the maps

**After following all the steps described below, please click on the `Results` tab to vizualise the results**

- In the menu 'Volume calculation' the user must upload a `zip` file containing both a `shapefile` with the extent of the area of interest and a `csv` file containing peat depth measures (in m) taken at the site with coordinates for each measure (given in UTM 32 N, EPSG:25832). An example file for notation of peat depths is provided below. Peat depth measurements should -for best results- be taken at regular intervals at a maximum distance of 20m between each sample point (if a small peatland area are sampled, less than 20m is needed).

- The user can then click on `Load dataset`. After a few seconds a map of the given area with black points indicating where peat depth have been measured, should be displayed . The total area (in m2) will be computed.

- If the map describing the given area is correct click on `Calculate volume`. This is a feature that, based on the depth of the samples, interpolates the depths of the entire area of interest. After a few seconds or minutes (depending on the size of your area and the number of samples) a map of the interpolated peat depths should be displayed. **Note** that a progress bar is displayed on the bottom right of the application.

- After the volume calculation is done, a relief map showing peat depths should be displayed. The estimated total volume of peat (m3) should also appear on the top panel.

### Calculating the carbon content of the area

The final step lies in calculating the carbon content of the given area. When clicking on `Peat properties`, two options are offered to the user:

- 1) `Default values`: Using this option, the user choose the peatland type of the area. The calculation of the carbon content will then be done using a database of peat properties from Norwegian mires, that contain values for **bulk density** and **fraction organic matter** representing the chosen peatland type, and a set value of 0.5 for **fraction of carbon content in organic matter** (see paper for references).

- 2) `Custom values`: This option requires that the user knows the values of **bulk density** (in g/cm3 or tonne/m3, commonly less than 1 and often as small as 0.1 for peatlands), **fraction organic matter** (values of 0-1) and **fraction carbon content** (values of 0-1) in the given area, or that the user is interested in testing with specific values. The input values are specified in the three boxes. Once the values are inserted, the user can click on `Load values`.

The total carbon content (kg) of the area will be displayed on the top right panel of this application.

### Download the data

Once the peat volum map is computed, it is possible to download the output maps. The results from the carbon calculation will also be available by completing the next step in the calculator.
In the application, the user can click on `Download results` and `Download`. This will return a `.zip` file containing:

- `map_descriptive.png` : a map of the given area including peat depth measurement points.
- `map_interpolation.png` : a map with interpolated values of peat depths.
- `interpolation_raster.tif` : a raster of the result from the interpolation of volume - ready to use in either **QGIS or ArcGIS!**
- `results.csv` : a csv-file with results from the volume and carbon calculations. 

---

### Author / Forfatter

The application has been created by [Benjamin Cretois](https://www.nina.no/english/Contact/Employees/Employee-info?AnsattID=15849), [Marte Fandrem](https://www.ntnu.no/ansatte/marte.fandrem) and [Magni Olsen Kyrkjeeide](https://www.nina.no/Kontakt/Ansatte/Ansattinformasjon.aspx?AnsattID=12110). This project was funded by Norwegian Research Council under Grant number 282327 and Statnett.

<img src="man/figures/logo_nina.png" alt="drawing" width="100"/>
<img src="man/figures/ntnu.png" alt="drawing" width="100"/>
<img src="man/figures/statnett.png" alt="drawing" width="100"/>


### Copyright / Opphavsrett

[![License](https://img.shields.io/badge/Licence-GPL%20v2.0-orange.svg)]() CarbonViewer is licensed under the GNU General Public License (GPL) v2.0. 

### How to cite us:

