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

```


## Opgave
### Oplossing
```
```


## Opgave
### Oplossing
```
```


## Opgave
### Oplossing
```
```


## Opgave
### Oplossing
```
```


## Opgave
### Oplossing
```
```


## Opgave
### Oplossing
```
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMxNTczMDY5OSw4Njc3NzIwMzVdfQ==
-->