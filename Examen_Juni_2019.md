# Examen Juni 2019
## ERD en Datbase gegevens
Voor dit examen maken we gebruiken van een eenvoudig model van een hogeschoolbibliotheek.Deze hogeschool beschikt over verschillende campussen. Elke campus heeft juist één bib. Wegeven hieronder eerst het EERD. Onder de figuur volgt wat uitleg over de verschillende tabellen.

![ERD](https://github.com/lemmensangeloucll/Databanken-Dataquerying-MBI63x/blob/master/img/ERD.png)

Een boek heeft een unieke titelcode (zoals een ISBN nummer dat we hier wat vereenvoudigdvoorstellen door een gewoon geheel getal). Het wordt uitgegeven door een uitgeverij. Elk boekkan meerder categorieën hebben. De mogelijkheden zijn informatica, economie, marketing, taal,wetenschap, pedagogie, cursus, fictie en non-fictie.Van een boek kunnen verschillende exemplaren aanwezig zijn in de verschillende campusbi-bliotheken. Een ontlener kan een welbepaald fysiek exemplaar van een boek ontlenen.Op de volgende pagina krijg je de eerste regels van het resultaat vanSELECT * FROM . . .bij7 van de 8 tabellen.

![Database gegevens](https://github.com/lemmensangeloucll/Databanken-Dataquerying-MBI63x/blob/master/img/DBPrint.png)
## Vraag 1. Schema aanpassen
De hoofdbibliothecaris bekijkt je EERD en merkt op dat het eigenlijk wel handig voor hen zouzijn dat ze van elke ontlener weten wat de ‘hoofdbib’ is. Een student die zowel op CampusProximus als op Campus Gasthuisberg lessen volgt, kiest dan bvb. die campusbib waar hij hetmeest komt. Elke ontlener moet verplicht zo’n hoofdbib hebben. De student kan natuurlijkwel verder boeken blijven ontlenen van elke campus.

 1. Teken op het schema op de vorige pagina een efficiënte uitbreiding die deze opmerkingimplementeert.
 2. Welke regel(s) code moet je toevoegen aan de CREATE SQL statements bij het aanmaken van alle tabellen? Geef de regel(s) + vermeld duidelijk in welke tabel(len) je de aanpassing doet.
 3. Geef één voorbeeld van een INSERT statement voor de gewijzigde tabel(len).

## Vraag 2. Populairste uitgeverij
Van welke uitgeverij hadden we de meeste boek-exemplaren in de bib van campus Gasthuis-berg op 25-10-2017? Figuur 1 toont de uitvoer voor onze databank.


![Figuur 1](https://github.com/lemmensangeloucll/Databanken-Dataquerying-MBI63x/blob/master/img/Figuur1.png)

> **Figuur 1** Van deze uitgeverij hadden we op 25-10-2017 het meeste exemplaren

## Vraag 3. Alle IT-exemplaren op plaats 'Haasrode'
De opleiding ‘Toegepaste informatica’ verhuist volgend academiejaar van de campus metlocatie ‘Haasrode’ naar een andere plaats. Daarom is het nodig om een inventaris op temaken van alle exemplaren met categorienaam ‘informatica’ in Haasrode. Resultaat dat moetgetoond worden: enkel de boekcode en de categorie, fig 2.


![Figuur 2](https://github.com/lemmensangeloucll/Databanken-Dataquerying-MBI63x/blob/master/img/Figuur2.png)

> **Figuur 2** Alle exemplaren met categorie ‘informatica’ in de campusbib die in Haasrode gelegen is



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk0NzM1NTI3MSwtMTU5MTE0OTQxNSw5OT
U2ODMxMDgsLTIxNDUxMjAxNTFdfQ==
-->