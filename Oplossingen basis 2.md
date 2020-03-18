# Oplosingen Basis 2 SQL

## Opgave 1
Maak een lijst van alle wedstrijden, die gespeeld werden voor het tweede team (teamnr: 2) en die gewonnen zijn door een speler van onze club (let op de benamingen van de kolomkoppen).
### Oplossing
```
SELECT WEDSTRIJDNR, SPELERSNR,GEWONNEN as gewonnen_sets,VERLOREN as verloren_sets
FROM WEDSTRIJDEN
WHERE TEAMNR = 2 AND GEWONNEN > VERLOREN
```

## Opgave 2
Maak een overzicht van alle wedstrijden van speler met nummer 6 waarbij je berekent met welk aantal sets verschil hij de wedstrijd gewonnen of verloren heeft.
### Oplossing
```
SELECT spelersnr, gewonnen, verloren, (gewonnen - verloren) AS verschil
FROM wedstrijden
WHERE spelersnr = 6
```

## Opgave 3
Maak een lijst van alle actieve bestuursleden.  
Een actief bestuurslid is een bestuurslid met een lege eind_datum.  
Sorteer op begin_datum oplopend.
### Oplossing
```
SELECT spelersnr, functie
FROM bestuursleden
WHERE eind_datum IS NULL
ORDER BY begin_datum ASC
```

## Opgave 4
Maak een lijst met de wedstrijden van speler nummer 6 waarbij je aangeeft of de wedstrijd gewonnen (toon: 'gewonnen') of verloren (toon: verloren) werd door de betreffende speler.
### Oplossing
```
select spelersnr, wedstrijdnr, gewonnen, verloren,
case WHEN gewonnen > verloren THEN 'gewonnen'
	WHEN gewonnen < verloren THEN 'verloren'
END
as resultaat
from wedstrijden
where spelersnr = 6
```

## Opgave 5
Maak een lijst van alle boetes met een boetebedrag boven 75 euro die betaald werden in 1980, 1981, 1982 of 1983.  
  
Let op:  
1) de titels van de kolommen moeten gebruikersvriendelijk zijn en geen afkortingen bevatten (spelersnr wordt speler, jaar van de boete verschijnt als jaar en het bedrag wordt weergegeven als bedrag).  
2) Geef geen date als jaar terug, maar een int.
### Oplossing
```
SELECT spelersnr as speler, EXTRACT(YEAR FROM datum) as jaar, bedrag
FROM boetes
WHERE bedrag > 75 AND EXTRACT(YEAR FROM datum) IN (1980, 1981, 1982, 1983);
```

## Opgave 6
Maak een lijst van alle vrouwelijke aanvoerders van een team. Hierbij toon je voor deze spelers het spelersnummer en de volledige naam.
### Oplossing
```
SELECT spelers.spelersnr, naam, voorletters
FROM spelers, teams
WHERE geslacht = 'V' AND teams.spelersnr = spelers.spelersnr
```

## Opgave 7
Geef een lijst met het spelersnummer, de naam van de speler, de datum van de boete van al de spelers die in 1980 een boete gekregen hebben en in Rijswijk wonen.  
  
Zorg voor de juiste opmaak van de datum in het resultaat (niet YYYY-MM-DD maar DD/MM/YYYY) waarbij je de to_char functie gebruikt.  
  
Sorteer op spelersnr.
### Oplossing
```
select spelersnr, voorletters, naam, to_char(boetes.datum, 'DD/MM/YYYY') as boetedatum
from spelers
inner join boetes using(spelersnr)
where EXTRACT(YEAR from datum) = 1980 and plaats = 'Rijswijk'
order by spelersnr
```

## Opgave 8
Maak een lijst van alle spelers die al een wedstrijd gespeeld hebben.  
Alleen spelers met een 'e' (hoofdletter of kleine letter) in de naam moeten getoond worden. Zorg dat deze laatste voorwaarde met één WHERE-conditie gerealiseerd wordt.  
Let ook op de juiste kolomhoofdingen.  
Sorteer op spelersnr en zorg dat elke speler maar één keer voorkomt.  
Gebruik geen concat, maar wel ||.
### Oplossing
```
select spelers.spelersnr, (spelers.voorletters || ' ' || spelers.naam) as spelersnaam
from spelers
join wedstrijden using(spelersnr)
where spelers.naam ilike '%e%'
group by spelersnr
order by spelersnr
```

## Opgave 9
Geef alle boetes groter dan 25 euro voor aanvoerders die meegespeeld hebben in een winnende wedstrijd met het team waarvan ze aanvoerder zijn.  
Sorteer op datum van de boete (de tekstuele waarde, niet de echte datum).
### Oplossing
```
select distinct spelersnr, betalingsnr, to_char(boetes.datum, 'DD/MM/YYYY') as boetedatum
from boetes
inner join wedstrijden using(spelersnr)
inner join teams using(spelersnr, teamnr)
where boetes.bedrag > 25 and gewonnen > verloren 
order by boetedatum
```

## Opgave 10
Geef een overzicht van alle divisies waar wedstrijden voor gespeeld zijn met spelers die actief bestuurslid zijn en minstens één boete hebben.  
Zorg dat elke divisie maar één keer voorkomt en sorteer de lijst alfabetisch.
### Oplossing
```
select distinct teams.divisie
from teams
inner join wedstrijden on teams.teamnr = wedstrijden.teamnr
inner join bestuursleden on wedstrijden.spelersnr = bestuursleden.spelersnr and bestuursleden.eind_datum is null
inner join boetes on bestuursleden.spelersnr = boetes.spelersnr
order by divisie ASC
```
