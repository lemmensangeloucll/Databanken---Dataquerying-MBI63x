# Oplosingen Joins SQL

## Opgave 1
Geef een lijst met het spelersnummer, de naam van de speler, de datum van de boete en het bedrag van de boete van al de spelers die een boete gekregen hebben met een bedrag groter dan 45,50 euro en in Rijswijk wonen.
Sorteer op spelersnr en het volgnummer van de boete.
Gebruik expliciete joins.
### Oplossing
```
select spelersnr, spelers.naam, boetes.datum, boetes.bedrag
from spelers
inner join boetes using(spelersnr)
where boetes.bedrag > 45.50 and spelers.plaats = 'Rijswijk'
order by spelersnr, betalingsnr
```

## Opgave 2
Maak een lijst van alle mannelijke aanvoerders van een team. Geef voor die aanvoerders de wedstrijden waarin ze gespeeld hebben.
Geef ook aanvoerders die geen wedstrijd gespeeld hebben.
Hierbij toon je voor deze spelers het spelersnummer en de volledige naam, voor het team de divisie en voor de wedstrijd het wedstrijdnummer.
Sorteer aflopend op het wedstrijdnummer.
### Oplossing
```
select spelersnr, naam, voorletters, divisie, wedstrijdnr
from teams
inner join spelers using(spelersnr)
left outer join wedstrijden using(spelersnr)
where spelers.geslacht = 'M'
order by wedstrijdnr DESC
```

## Opgave 3
Geef het spelersnummer, het jaar van toetreden en bondsnummer van alle spelers en de teams waarvoor ze kapitein zijn. Ook spelers die geen teamkapitein zijn, moeten getoond worden.
Sorteer op spelersnr aflopend.
### Oplossing
```
SELECT spelersnr, jaartoe, bondsnr, teamnr
FROM spelers LEFT OUTER JOIN teams USING(spelersnr)
ORDER BY spelersnr DESC
```

## Opgave 4

### Oplossing
```

```

## Opgave 5

### Oplossing
```

```

## Opgave 6

### Oplossing
```

```

## Opgave 7

### Oplossing
```

```

## Opgave 8

### Oplossing
```

```

## Opgave 9

### Oplossing
```

```

## Opgave 10

### Oplossing
```

```
