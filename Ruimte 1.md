# Oplosingen Ruimte 1 SQL

## Opgave
Welke reizigers hebben al meer dan 1 reis ondernomen waarvoor ze meer dan 2,5 miljoen euro moesten betalen?  
Sorteer op naam
### Oplossing
```
select naam, count(reisnr) as aantal_reizen
from reizen
inner join deelnames using(reisnr)
inner join klanten using(klantnr)
where prijs > 2.50
group by klantnr, naam
having count(reisnr) > 1
order by naam

```
## Opgave
Bereken voor de klant wiens naam begint met G en eindigt met s hoeveel hij in totaal al besteed heeft aan reizen.
### Oplossing
```

```
## Opgave
Maak een lijst met een overzicht van de reizen en het aantal deelnemers van elke reis. Orden de lijst dalend op basis van het aantal deelnemers, als er eenzelfde aantal deelnemers is, moeten deze stijgend geordend worden volgens reisnummer.
### Oplossing
```
select reisnr, count(klantnr) AS deelnemers
from deelnames
group by reisnr
order by deelnemers DESC, reisnr;
```
## Opgave

### Oplossing
```

```
## Opgave
Maak een lijst met een overzicht van de reizen en het aantal deelnemers van elke reis. Orden de lijst dalend op basis van het aantal deelnemers, als er eenzelfde aantal deelnemers is, moeten deze stijgend geordend worden volgens reisnummer.
Zorg dat reizen zonder deelnames ook in het resultaat staan.
### Oplossing
```
select r.reisnr, count(d.klantnr) as deelnemers
from reizen as r left outer join deelnames as d using(reisnr)
group by r.reisnr
order by deelnemers desc, r.reisnr
```
## Opgave
Op welke planeten verblijft men gemiddeld langer dan 2 dagen?
Sorteer op objectnaam.
### Oplossing
```
select h.objectnaam, avg(b.verblijfsduur)
from bezoeken AS b
inner join hemelobjecten AS h using(objectnaam)
where h.satellietvan = 'Zon'
group by h.objectnaam
having avg(b.verblijfsduur) > 2
order by h.objectnaam
```
## Opgave
Welke planeten met meer dan 7 manen worden bezocht (met of zonder verblijf)?
Sorteer aflopend op basis van het aantal manen.
Let erop dat je planeten die meerdere keren bezocht worden, niet dubbel telt.
### Oplossing
```
select p.objectnaam
from hemelobjecten AS p
inner join hemelobjecten AS m ON m.satellietvan = p.objectnaam
inner join bezoeken AS b ON b.objectnaam = p.objectnaam
inner join hemelobjecten AS zon ON zon.objectnaam = p.satellietvan and zon.satellietvan IS NULL
group by p.objectnaam
having count(distinct m.objectnaam) > 7
order by count(distinct m.objectnaam) DESC
```
## Opgave

### Oplossing
```

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MDI1MDI2NCwxNjM0NjEzMDQxXX0=
-->
