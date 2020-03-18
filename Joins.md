# Oplosingen Joins SQL

## Opgave 1 (13)
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

## Opgave 2 (14)
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

## Opgave 3 (35)
Geef het spelersnummer, het jaar van toetreden en bondsnummer van alle spelers en de teams waarvoor ze kapitein zijn. Ook spelers die geen teamkapitein zijn, moeten getoond worden.
Sorteer op spelersnr aflopend.
### Oplossing
```
SELECT spelersnr, jaartoe, bondsnr, teamnr
FROM spelers LEFT OUTER JOIN teams USING(spelersnr)
ORDER BY spelersnr DESC
```

## Opgave 4 (36)
Geef voor alle spelers die bestuurslid zijn (of geweest zijn) een lijst van de wedstrijdnummers van alle wedstrijden die ze gespeeld hebben, en het verschil in sets waarmee ze gewonnen hebben.
Bestuursleden zonder wedstrijd moeten ook in het resultaat voorkomen.
Sorteer op bestuurslidfunctie (oplopend), verschil (aflopend), spelersnr (oplopend) en wedstrijdnr (oplopend)
### Oplossing
```

```

## Opgave 5 (37)
Geef voor alle vrouwelijke spelers die in Den Haag, Zoetermeer of Leiden wonen
het spelersnummer, hun woonplaats en een lijst van de teams waarvoor ze ooit gespeeld hebben.
Sorteer op spelersnr
### Oplossing
```
select spelersnr, plaats, teamnr
from spelers
left outer join wedstrijden using(spelersnr)
where plaats in ('Den Haag', 'Zoetermeer', 'Leiden') and geslacht = 'V'
order by spelersnr
```

## Opgave 6 (39)
Geef voor elke mannelijke speler wiens naam minstens 2 keer de letter 'e' bevat een lijst van de functies die hij op dit moment uitoefent.
Ook mannelijke spelers zonder huidige functie moeten getoond worden.
Sorteer op spelersnr.
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
