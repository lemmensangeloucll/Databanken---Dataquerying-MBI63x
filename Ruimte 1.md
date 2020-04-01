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
eyJoaXN0b3J5IjpbMTMzNjg0MjYzOSwxNjM0NjEzMDQxXX0=
-->