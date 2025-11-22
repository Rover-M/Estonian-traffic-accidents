# Inimkannatanutega liiklusõnnetuste andmed

Inimkannatanutega liiklusõnnetuste andmed, mille kogumisega tegeleb Politsei- ja Piirivalveamet. Statistilise analüüsi ning talletamise eest vastutab Transpordiamet. Liiklusõnnetuste arvestamist reguleerib vastav [määrus](https://www.riigiteataja.ee/akt/110072018009?leiaKehtiv).

Aasta 2023 suvel korrastati 2013-2022 liiklusõnnetuste asukohaandmed. Varasemate aastate andmeid ei korrastatud. Ümberarvutused tehti, et arvestada teevõrgus toimunud muutusi, nt trassimuutust Tallinn-Tartu-Võru-Luhamaa maanteel kus varasem tee nr 2, mis läbis Kose-Uuemõisat ja Ardut on täna tee nr 11720 ja 11141. Edaspidi korrastatakse lõppenud aasta andmed järgneva aasta I kvartalis.

Vaata ka:

- [Transpordiamet - Liiklusõnnetuste statistika](https://transpordiamet.ee/liiklusonnetuste-statistika)

## Andmestikus olevad failid

- `lo_2011_<aasta>.csv` - Liiklusõnnetuste andmed alates 2011 kuni jooksva kuu alguseni
- `lo_2011_<aasta>.csv töödeldud` - Avaandmete poolt töödeldud versioon failist; API tarbimine võib töötada, aga ei soovita faili ennast alla laadida
- `lo_metadata.json` - Veerupõhised metaandmed lo csv faili kohta, mis peaks olema ka kättesaadav kui tarbida andmeid läbi API
- `Liiklusõnnetused_2011_2021.csv` & `Liiklus6nnetused_2011_2022.csv` - Eelmistel aastatel tehtud väljavõtted andmetest

## Andmete kuju

Liiklusõnnetuste csv failis on igal real üks liiklusõnnetus, kus on vähemalt 1 kannatanu:

- `Juhtumi nr` - Juhtumi unikaalne võti, võib sisaldada teksti
- `Toimumisaeg` - Kuupäev kujul `YYYY-MM-DD hh:mm:ss`
  - Kui kellaaeg on 00:00:00, siis on tõenäoliselt kellaaja andmed puudu
- `Isikuid` - Õnnetuses osalenud isikute arv sõltumata vigastatute olemasolust
- `Hukkunuid` - Õnnetuse tagajärjel hukkunud isikute arv
  - Siia sisse ei arvestata isikuid, kelle surm ei ole õnnetusest tulenev (näiteks kui õnnetuses osaleja suri enne õnnetust teistel põhjustel, nt terviserikke tagajärjel)
- `Sõidukeid` - Õnnetuses osalenud sõidukite arv
- `Vigastatuid` - Õnnetuses vigastatud isikute arv
- `Aadress` - Politsei märgitud õnnetuse toimumiskoha aadress
- `Tänav` - Toimumiskoha tee või tänava nimi (PPA)
- `Maja nr` - Toimumiskoha maja number (PPA); linnas toimunud õnnetuste puhul märgitakse tee km asemel maja nr kui see on võimalik
- `Ristuv tänav` - Toimumiskohaga ristuv tänav (PPA)
- `Tee nr` - Teede nimekirjast tulev number
  - Teede nimekirjad on leitavad [Transpordiameti veebilehel](https://www.transpordiamet.ee/teeregister) ja [Riigi Teatajas](https://www.riigiteataja.ee/akt/128062015003?leiaKehtiv=)
  - Arvutatakse ümber teeregistri kehtivale seisule iga aasta
- `Tee km` - Mitmendal tee kilomeetril toimus õnnetus
  - Arvutatakse ümber iga aasta
- `Maakond` - Toimumiskoha maakond hetkel kehtiva haldusjaotuse järgi
- `Omavalitsus` - Toimumiskoha omavalitsus hetkel kehtiva haldusjaotuse järgi
- `Asustusüksus` - Toimumiskoha asustusüksus hetkel kehtiva haldusjaotuse järgi
- `Asula` - Kas õnnetus toimus asulas
- `Liiklusõnnetuse liik`
- `Liiklusõnnetuse liik (detailne)`
- `Joobes mootorsõidukijuhi osalusel` - Õnnetuses osales isik(uid), kes oli joobes, ning kes oli mootorsõiduki juht (1 = õnnetuses osales selline isik, 0 = ei osalenud)
  - Siin ei loeta kokku, mitu inimest osales; ainult kas osales vähemalt 1
  - (Sama loogika kehtib ka teiste osaluste kohta)
- `Kergliikurijuhi osalusel` - Isiku roll õnnetuses oli tasakaaluliikuri juht (pärast 2021) või kergliikuri juht
  - Liikluses osalejate mõisteid [muudeti aastal 2021](https://www.riigiteataja.ee/redaktsioonide_vordlus.html?grupiId=344969&vasakAktId=130062020019&paremAktId=110122020015)
- `Jalakäija osalusel` - Isiku roll oli tasakaaluliikuri juht (kuni 2021) või jalakäija või rulluisutaja
- `Kaassõitja osalusel` - Isiku roll sisaldas sõna "sõitja"
- `Maastikusõiduki juhi osalusel` - Isiku roll oli ATV juht või maastikusõiduki juht
- `Eaka (65+) mootorsõidukijuhi osalusel` - Isiku vanus oli vähemalt 65 ning isik oli mootorsõiduki juht
- `Bussijuhi osalusel` - Isiku roll oli bussijuht
- `Veoautojuhi osalusel` - Isiku roll oli veoautojuht
- `Ühissõidukijuhi osalusel` - Isiku roll oli bussijuht / trammijuht / trollijuht
- `Sõiduautojuhi osalusel` - Isiku roll oli sõiduautojuht
- `Mootorratturi osalusel` - Isiku roll oli mootorrattur
- `Mopeedijuhi osalusel` - Isiku roll oli mopeedijuht / pisimopeedi juht
- `Jalgratturi osalusel` - Isiku roll oli jalgrattur
- `Alaealise osalusel` - Isiku vanus oli vahemikus 0-18 (välja arvatud)
- `Esmase juhiloa omaniku osalusel` - Isiku juhiloa tüüp oli ESMANE ning isik oli mootorsõiduki juht
- `Turvavarustust mitte kasutanud isiku osalusel` - Isiku turvavarustuse staatus oli helkur puudub / turvavarustus puudub / turvavarustust ei kasutatud
- `Mootorsõidukijuhi osalusel` - Isiku roll oli ATV juht / bussijuht / liikurmasina juht / maastikusõiduki juht / mootorrattur / mopeedijuht / pisimopeedi juht / sõiduautojuht / traktorist / trammijuht / trollijuht / veoautojuht
  - Sama loogikat kasutavad ka teised osalused mootorsõiduki juhi tuvastamiseks
- `Tüüpskeemi nr`
- `Tüüpskeem`
- `Tee tüüp`
- `Tee tüüp (detailne)`
- `Tee liik` - Teeregistrile vastav tee liik
- `Tee element`
- `Tee element (detailne)`
- `Tee objekt`
- `Kurvilisus`
- `Tee tasasus`
- `Tee seisund`
- `Teekate`
- `Teekatte seisund`
- `Sõiduradade arv`
- `Lubatud sõidukiirus`
- `Ilmastik`
- `Valgustus`
- `Valgustus (detailne)`
- `X koordinaat` - Toimumiskoha GPS koordinaadid (L-EST97 süsteemis)
  - Eelmainitud andmete korrastamise käigus arvutati õnnetuse toimumise aastal kehtinud teevõrgu järgi õnnetusele uued koordinaadid kui need olid puudu või asusid teeaadressist kaugemal kui 1 km
  - Korrektsed koordinaadid on aluseks teeaadressi ja haldusjaotuse ümberarvutamisel
- `Y koordinaat` - Toimumiskoha GPS koordinaadid (L-EST97 süsteemis)

## Andmete Excelisse importimine

Seda faili ei ole soovitatav topelt klõpsuga eesti regiooni Excelis avada: ta ei oska täpitähti õigesti välja lugeda otse.

Parima tulemuse jaoks:

- Ava Excelis tühi töövihik
- Vali Andmed - Too Andmed - Failist - Teksti-/CSV-failist
- Impordi `lo_2011_<aasta>.csv` fail
- Määra õiged parameetrid:
  - Faili päritolu: `65001: Unicode (UTF-8)`
  - Eraldaja: Semikoolon
- Klõpsa "Andmeid transformeerima"
  - Klõpsa "Kasuta esimest rida päistena" kui "Esiletõstetud päised" ei ole juba rakendatud etappides
  - Kontrolli, et andmetüübid on õiged
    - Andmetüübi muutmiseks klõpsa veeru nimest vasakule jäävat tüübi ikooni, ning peale tüübi valimist klõpsa "Asenda praegune"
    - Juhtumi nr, Maja nr, Tee nr, Tüüpskeemi nr, Sõiduradade arv, Lubatud sõidukiirus on tekst
    - Tee km, X koordinaat, Y koordinaat on komaga arvud, mida vajadusel peab märkima tekstiks
  - Klõpsa "Sule ja laadi"
- Kui "Päringud ja ühendused" kaardil ei ole näha ühtegi tõrget, siis läks laadimine loodetavasti edukalt

## Avaandmete lehe masintöötlusest

Ehk näiteid sellest, kuidas meie e-riik, nagu Tallinngi, ei ole veel valmis.

- Avaandmete leht nõuab pealkirja ja kirjeldust nii eesti kui inglise keeles, aga ikkagi automaatselt tõlgib eestikeelse teksti ingliskeelseks ja siis veel on tal jultumust öelda et "Metaandmete tõlkimiseks on kasutatud masintõlget ning nende kvaliteet võib seega olla kohati ebakorrektne"
- Failide järjekord ei ole sama kui üleslaadimise järjekord; ma ei tea miks ta neid sellises järjekorras näitab
- Ära lae alla töödeldud faili
  - Abivalmilt pannakse igale väärtusele jutumärgid ümber, ehk fail läheb suuremaks ja midagi ei muutu paremaks
  - Veerud järjestatakse ümber mingis järjekorras, sest see polnud ju tähtis kuidas need algselt olid, ega ju?
  - Kui laadida csv fail üles läbi veebilehe (mitte API), siis lähevad andmed veel rohkem katki; aga selle detailid jätaksin juba lugeja avastada

# Road accidents with injuries

Data for crashes resulting in death or injury, which has been collected by Estonian Police and Border Guard Board. Estonian Transport Administration is responsible for statistical analysis and storage of the data. Recording of road accidents is regulated by the corresponding [regulation](https://www.riigiteataja.ee/akt/110072018009?leiaKehtiv) (only available in Estonian).

Location data for years 2013-2022 was corrected in summer 2023. Prior years data was not corrected. Recalculations were made to harmonize data with changes made to the road network. In the future, such corrections will be made in the first quarter of a year.

See also:

- [Transport Administration - Road accident statistics](https://transpordiamet.ee/liiklusonnetuste-statistika) (only in Estonian)

## Files in the dataset

- `lo_2011_<year>.csv` - Crash data from 2011 until start of current month
- `lo_2011_<year>.csv` - Version of the file that has been processed by the open data website; consuming via API may work, but downloading this file is not advised
- `lo_metadata.json` - Column-based metadata about lo csv file which should also be available via API
- `Liiklusõnnetused_2011_2021.csv` & `Liiklus6nnetused_2011_2022.csv` - Previous versions of crash data

## Data structure

Every row is one accident with at least one injured or dead person:

- `Juhtumi nr` - Case ID
- `Toimumisaeg` - Time of accident, format `YYYY-MM-DD hh:mm:ss`
  - If time is 00:00:00, it is probably unknown
- `Isikuid` - Amount of persons
- `Hukkunuid` - Amount of dead persons
  - This does not include people, whose death is not caused by the accident (e.g. if a participant died before the accident for other reasons)
- `Sõidukeid` - Amount of vehicles
- `Vigastatuid` - Amount of injured persons
- `Aadress` - Address (from PPA)
  - PPA is short for Estonian Police and Border Guard Board
- `Tänav` - Street (PPA)
- `Maja nr` - House number (PPA)
- `Ristuv tänav` - Crossing street (PPA)
- `Tee nr` - Road number from the list of roads in Estonia (PPA data with TRAM recalculations)
  - Road lists can be found on the [Transport Administration webpage](https://www.transpordiamet.ee/en/node/143) (untranslated at time of writing) or [Riigi Teataja](https://www.riigiteataja.ee/akt/128062015003?leiaKehtiv=) (also only in Estonian)
  - TRAM = Estonian Transport Administration
  - Recalculated to current road registry status every year
- `Tee km` - Which kilometer the accident occurred on (PPA+TRAM)
- `Maakond` - County (PPA+TRAM)
- `Omavalitsus` - Commune / Local Government (PPA+TRAM)
- `Asustusüksus` - Village (PPA+TRAM)
- `Asula` - Is the location a settlement (JAH=true, EI=false)
- `Liiklusõnnetuse liik` - Generalized version of `Liiklusõnnetuse liik (detailne)`
  - Jalakäijaõnnetus - Crashing into a pedestrian
  - Kokkupõrge - Two vehicles colliding
  - Ühesõidukiõnnetus - A vehicle drove off the road or into an obstacle
  - Muu liiklusõnnetus - Falling in public transit, crashing into an animal, or other confusing matters
  - Teadmata - Unknown
- `Liiklusõnnetuse liik (detailne)` - Type of accident
- `Joobes mootorsõidukijuhi osalusel` - Drunk driver participated - In the accident was at least one person who was drunk and who was driving a motor vehicle (1 = there were such participants, 0 = there were not)
  - This column does not count such persons, only if at least one exists
  - (The same logic goes for all "osalusel" type columns, which find specific people)
  - (Also keep in mind that the vehicle type translations may be inaccurate)
- `Kergliikurijuhi osalusel` - Light vehicle driver participated - Persons role in the accident was hoverboard driver (after 2021) or light vehicle driver
  - A light vehicle is an electric vehicle without a seat that is meant for transporting one person
  - The definitions for traffic participants were [changed in 2021](https://www.riigiteataja.ee/redaktsioonide_vordlus.html?grupiId=344969&vasakAktId=130062020019&paremAktId=110122020015) (only in Estonian)
- `Jalakäija osalusel` - Pedestrian participated - Persons role was hoverboard driver (before 2021) or pedestrian or roller skater
- `Kaassõitja osalusel` - Passenger participated - Persons role contained word "sõitja"
- `Maastikusõiduki juhi osalusel` - Terrain vehicle driver participated - Role was ATV driver or terrain vehicle driver
- `Eaka (65+) mootorsõidukijuhi osalusel` - Elder driver participated - Age was 65+ and person was driving a motor vehicle
- `Bussijuhi osalusel` - Bus driver participated - Role was bus driver
- `Veoautojuhi osalusel` - Truck driver participated
- `Ühissõidukijuhi osalusel` - Public transport driver participated - Role was bus driver / tram driver / trolley driver
- `Sõiduautojuhi osalusel` - Car driver participated
- `Mootorratturi osalusel` - Motorcyclist participated
- `Mopeedijuhi osalusel` - Moped driver participated - Role was moped / small moped driver
- `Jalgratturi osalusel` - Cyclist participated
- `Alaealise osalusel` - Underage participated - Age was between 0 and 18 (not included)
- `Esmase juhiloa omaniku osalusel` - Provisional driving license participated - Driving license type was provisional (beginner's license) and person was driving a motor vehicle
- `Turvavarustust mitte kasutanud isiku osalusel` - Safety equipment not used - A persons safety equipment status was Reflector missing / Safety equipment missing / Safety equipment not used
- `Mootorsõidukijuhi osalusel` - Role was ATV driver / bus driver / heavy machinery driver / terrain vehicle driver / motorcyclist / moped driver / small moped driver / car driver / tractor driver / tram driver / trolley driver / truck driver
  - The same logic is used by other participations to find motor vehicle drivers
  - Heavy machinery - Motor vehicle that is meant for a specific job, with a maker speed of 6-40 km/h
- `Tüüpskeemi nr` - Type scheme code
- `Tüüpskeem` - Type scheme name
- `Tee tüüp` - Generalized version of `Tee tüüp (detailne)`
- `Tee tüüp (detailne)` - Road type
- `Tee liik` - Road kind according to the road registry
- `Tee element` - Generalized version of `Tee element (detailne)`
- `Tee element (detailne)` - Road element
- `Tee objekt` - Road object
- `Kurvilisus` - Road curvature
- `Tee tasasus` - Road hill type
- `Tee seisund` - Road condition
- `Teekate` - Road paving
- `Teekatte seisund` - Road paving condition
- `Sõiduradade arv` - Number of lanes
- `Lubatud sõidukiirus` - Allowed driving speed
- `Ilmastik` - Weather
- `Valgustus` - Generalized version of `Valgustus (detailne)`
- `Valgustus (detailne)` - Lighting
- `X koordinaat` - GPS coordinates in L-EST97 system
  - As part of previously mentioned recalculations, if no coordinates were given or they were more than 1km from the road address, they were replaced
  - Correct coordinates are used as a basis for recalculating road address and village/commune/county
- `Y koordinaat` - GPS coordinates in L-EST97 system

## Importing data into Excel

This file is not recommended to be opened in Estonian regional Excel by way of double clicking on it.

For best results (keep in mind I do not have English language Excel and some labels may be different):

- Open an empty spreadsheet in Excel
- Click on Data - Get Data - From File - From Text/CSV
- Import the desired `lo_2011_<year>.csv` file
- Pick the correct parameters:
  - File Origin: `65001: Unicode (UTF-8)`
  - Delimiter: Semicolon
- Click "Transform Data"
  - Click "Use First Row as Header" if such a step is not already in applied steps
  - Check that column types are correct
    - To change type, click the type icon to the left of the column name, pick a type, and click "Replace current" in the window that opens
    - Juhtumi nr, Maja nr, Tee nr, Tee km, Sõiduradade arv, Lubatud kiirus, GPS X, GPS Y should be text
      - Tee nr, Tee km (if the commas are the right flavor), Lubatud kiirus, GPS X, GPS Y should work as numbers as well, but this is not guaranteed
  - Click "Close & Load"
- If the card on the right does not show any issues, then hopefully the loading was successful

## About Estonian open data machine processing

Or, how our e-country, just like Tallinn, is still a work in progress.

- The open data page requires a title and description both in Estonian and English, but then proceeds to overwrite the English text with an automatic translation; it then has the gall to say "Metadata is machine translated and may thus be of poor quality"
- The ordering of files is not the same as the order they were uploaded; I have no idea what order this is
- Do not download a processed file
  - Ever-so-helpfully every value gets quotation marks around it, which only serves to inflate the file size and do nothing else
  - Columns are reordered in some god-only-knows order, because it's not like that was an important part of the file that you spent time designing, right?
  - If you upload a csv file through the website (not the API), then the data is even more broken; but the details of that shall be left to the reader to discover
