# Oplosingen Basis SQL

## Opgave 1
Maak een lijst met alle spelers die in Zoetermeer wonen.
### Oplossing
```
SELECT spelersnr, naam, jaartoe
FROM spelers
WHERE plaats = 'Zoetermeer'
```

## Opgave 2
Maak een lijst met alle teams waarvan speler 27 de aanvoerder is.
### Oplossing
```
SELECT teamnr, spelersnr, divisie
FROM teams
WHERE spelersnr = 27
```

## Opgave 3
Geef een lijst met alle boetes kleiner dan 75 euro.  
Zorg dat de oudste boete bovenaan staat.
### Oplossing
```
Select datum, bedrag
from boetes
where bedrag < 75
order by datum asc
```

## Opgave 4
Geef een lijst van de spelernummers die momenteel nog bestuurslid zijn. Toon per spelersnummer ook de functie.  
Hint: EIND_DATUM IS NULL.
### Oplossing
```
SELECT spelersnr, functie
FROM bestuursleden
WHERE eind_datum IS NULL
```

## Opgave 5
Geef een lijst van spelersnummers die nu geen bestuurslid meer zijn, maar die het wel ooit geweest zijn. Toon per spelersnummer zijn functie en de eind datum.  
Hint: EIND_DATUM NOT NULL
### Oplossing
```
SELECT spelersnr, functie, eind_datum
FROM bestuursleden
WHERE eind_datum IS NOT NULL
```

## Opgave 6
Schrijf de query die het aantal rijen in boetes telt.
### Oplossing
```
SELECT COUNT(spelersnr) AS count
FROM boetes
```

## Opgave 7
Schrijf de query die het aantal gespeelde wedstrijden telt.
### Oplossing
```
SELECT count(wedstrijdnr) as count
FROM wedstrijden
```

## Opgave 8
Schrijf de query die het aantal teams in de tweede divisie toont.
### Oplossing
```
SELECT count(teamnr) as count
FROM teams
WHERE divisie = 'tweede'
```

## Opgave 9
Geef een lijst van de spelers hun postcodes.
### Oplossing
```
SELECT postcode
FROM spelers
```

## Opgave 10
Schrijf de query die je het jaar geeft waarop het eerste lid toegetreden is.
### Oplossing
```
SELECT min(jaartoe) as min
FROM spelers
```
