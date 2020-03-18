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
SELECT naam, geslacht, functie
FROM spelers
LEFT OUTER JOIN bestuursleden ON bestuursleden.spelersnr = spelers.spelersnr AND bestuursleden.eind_datum IS NULL
WHERE naam ilike '%e%e%' AND geslacht = 'M'
order by spelers.spelersnr
```

## Opgave 7 (51)
Geef een alfabetisch gesorteerde lijst van de namen van alle leden van de tennisvereniging die ofwel een recreatiespeler zijn (speelt geen wedstrijden) ofwel een wedstrijdspeler die nog geen wedstrijden gespeeld heeft.
### Oplossing
```

```

## Opgave 8 (52)
Geef voor alle huidige bestuurleden hun functie en de lijst van boetes die voor hen werd betaald.
Omdat je dit wil vergelijken met de boetebedragen die betaald werden voor spelers die niet in het bestuur zitten,
wil je deze boetebedragen ook opnemen in de tweede kolom van je resultaat. Sorteer je antwoord eerst op functie en daarna op het boetebedrag.
### Oplossing
```
select functie, bedrag
from boetes
full outer join bestuursleden ON bestuursleden.spelersnr = boetes.spelersnr and eind_datum is NULL
order by functie, bedrag
```

## Opgave 9 (53)
Geef een aflopend gesorteerde lijst van de nummers van alle spelers waarvoor nog geen boete werd betaald en die nog nooit in het bestuur van de tennisvereniging hebben gezeten.
### Oplossing
```
select s.spelersnr
from spelers as s
left outer join boetes as b using(spelersnr)
left outer join bestuursleden as bs using(spelersnr)
where b.spelersnr is NULL and bs.spelersnr IS NULL
order by s.spelersnr DESC
```

## Opgave 10 (204)
Geef een lijst van alle spelers die nog geen wedstrijd gespeeld hebben.
Sorteer op spelersnr
### Oplossing
```

```
