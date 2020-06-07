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

### Antwoord
```
select uigeverij.naam
from exemplaar
inner join boek using(titelcode)
inner join uitgeverij on boek.uitgever = uitgeverij.uitgeverij_id
where exemplaar.campus = 'Gasthuisberg' and aanschafdatum < '2017-10-25' 
group by uitgeverij.uitgeverij_id
order by count(exemplaar.boekcode) ASC
limit 1
```

## Vraag 3. Alle IT-exemplaren op plaats 'Haasrode'
De opleiding ‘Toegepaste informatica’ verhuist volgend academiejaar van de campus metlocatie ‘Haasrode’ naar een andere plaats. Daarom is het nodig om een inventaris op temaken van alle exemplaren met categorienaam ‘informatica’ in Haasrode. Resultaat dat moetgetoond worden: enkel de boekcode en de categorie, fig 2.


![Figuur 2](https://github.com/lemmensangeloucll/Databanken-Dataquerying-MBI63x/blob/master/img/Figuur2.png)

> **Figuur 2** Alle exemplaren met categorie ‘informatica’ in de campusbib die in Haasrode gelegen is

### Antwoord
```
select exemplaar.boekcode, categorie.naam
from exemplaar
inner join boek using(titelcode)
inner join boek_heeft_categorie on boek.titelcode = boek_heeft_categorie.boek
inner join categorie on boek_heeft_categorie.categorie = categorie.code
inner join campus on exemplaar.campus = campus.naam
where categorie.naam = 'informatice' and campus.plaats = 'Haasrode'
```

## Vraag 4. Overzicht boeken te laat
Je mag een ontleend boek 70 dagen bijhouden. Vanaf dag 71 betaal je€0,10 per boek perdag te laat. We willen een lijst met per ontlener de totale boete (gerekend tot op de dag vanvandaag) enkel berekend voor boeken die nog niet teruggebracht zijn. Alleen de mensendie in een gemeente wonen die minstens twee keer de kleine letter ‘a’ bevat mogen in hetoverzicht voorkomen. Zorg dat je ook die ontleners vermeldt die nog nooit een boek ontleendhebben (de totale boete van deze ontleners mag opnullblijven staan). Toon lener_id, naam,gemeente, totale boete in euro, aantal boeken te laat. Sorteert oplopend naar aantal boekente laat. Zorg dat je de tabel van figuur 3 bekomt.

![Figuur 3](https://github.com/lemmensangeloucll/Databanken-Dataquerying-MBI63x/blob/master/img/Figuur3.png)

> **Figuur 3** Lijst met de totale boete per persoon

### Antwoord
```
select lener_id, naam, gemeente, CASE WHEN DATEDIFF(day, retourdatum, uitleendatum) > 70 THEN 0.1 * DATADIFF(day, retourdatum + 1, GETDATE()) * count(boekcode) END AS "totale boete", count(boekcode) AS "aantal boeken te laat" 
from ontlener 
left outer join uitlening on lener_id = ontlener 
where ontlener.gemeente ILIKE '%a%a%' 
group by lener_id 
having retourdatum IS NULL 
order by count(boekcode) ASC
```

## Vraag 5. Volgorde bewerkingen
In welke volgorde worden de SQL-instructies van een query uitgevoerd door de databaseserver? Zorg dat je alle instructies vermeldt die in de lessen aan bod kwamen:SELECT, ...

### Antwoord

 1. From
 2. Where
 3. Group by
 4. Having
 5. Select
 6. Distinct
 7. Order by
 8. Limit/offset

## Vraag 6. Wat was de vraag?
Onderstaande query is het antwoord op een bepaalde vraag. Geef zo nauwkeurig mogelijkwat er gevraagd was.
```
select gemeente ,count(*)
from(campus c
inner join exemplaar eon(c.naam = e.campus)
inner joinuitlening uon(u.boekcode = e.boekcode ))
right outer join ontlener o on(o.lener_id = u.ontlener)and c.naam <>'Campus Gasthuisberg'
where c.naam isnullgroup bygemeente
```

### Antwoord
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQwMzgyNjU1NCw3ODMzNDMyNjcsMTk4MD
k0MjY2OSwtNTQzNzk2ODkzLC02NDgxOTI5MDAsLTE1OTExNDk0
MTUsOTk1NjgzMTA4LC0yMTQ1MTIwMTUxXX0=
-->