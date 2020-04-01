# Oplosingen Basis Ruimte SQL

## Opgave
Geef voor alle effectieve ruimtebezoeken het bezochte hemelobject weer en de verblijfsduur. Sorteer aflopend op verblijfsduur
### Oplossing
```
select objectnaam, verblijfsduur
from bezoeken
where verblijfsduur > 0
order by verblijfsduur desc
```


## Opgave
Geef alle hemelobjecten weer met een diameter groter dan 50 en kleiner dan 10000.  
Sorteer eerst aflopend op diameter en dan alfabetisch op naam
### Oplossing
```
select objectnaam, diameter
from hemelobjecten
where diameter > 50 and diameter < 10000
order by diameter DESC, objectnaam ASC
```


## Opgave
Geef het geboortejaar van de jongste klant
### Oplossing
```
select max(EXTRACT(YEAR from geboortedatum)) as date_part
from klanten
```


## Opgave
Geef het bedrag van de duurste reis als "duurste"
### Oplossing
```
select max(prijs) as duurste
from reizen
```


## Opgave
Geef van alle reizen die langer dan 400 dagen duurden, een lijst van deelnemers. Output is reisnr, klantnr. Sorteer eerst op reisduur en dan op klantnr
### Oplossing
```
select reisnr, klantnr
from reizen
inner join deelnames using(reisnr)
where reisduur > 400
order by reisduur, klantnr
```


## Opgave
Geef de totale verblijfsduur van alle bezoeken samen aan Mars
### Oplossing
```
select sum(verblijfsduur)
from bezoeken
where objectnaam = 'Mars'
```


## Opgave
Geef het aantal satellieten van Jupiter
### Oplossing
```
select count(*)
from hemelobjecten
where satellietvan = 'Jupiter'
```


## Opgave
Geef het aantal satellieten van Jupiter en Saturnus samen
### Oplossing
```
select count(*)
from hemelobjecten
where satellietvan = 'Jupiter' or satellietvan = 'Saturnus'
```


## Opgave
Geef de totale som van alle afstanden tot hun planeet van alle satellieten van Saturnus
### Oplossing
```
select sum(afstand) as "totale afstand"
from hemelobjecten
where satellietvan = 'Saturnus'
```


## Opgave
Geef de gemiddelde afstanden tot hun planeet van alle satellieten van Saturnus, afgerond op 2 getallen na de komma
### Oplossing
```

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzY3MDM2NzQ1LC0zMTU3MzA2OTksODY3Nz
cyMDM1XX0=
-->