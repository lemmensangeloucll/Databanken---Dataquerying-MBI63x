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


## Opgave
### Oplossing
```
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAyMDE2NDU5Myw4Njc3NzIwMzVdfQ==
-->