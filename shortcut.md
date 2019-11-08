2.1 Udskriv alle informationer om alle bolcher.
```SELECT * FROM `bolcher` ```

2.2 Find og udskriv navnene på alle de røde bolcher.
``` SELECT navn FROM `bolcher` WHERE `farve` = "Rød" ```
### Inner join
``` SELECT navn FROM `bolcher` INNER JOIN `bolche_farver` ON bolcher.FK_bolche_farve_id = bolche_farver.bolche_farve_id WHERE `bolche_farve_beskrivelse` = "Rød" ```

2.3 Find og udskriv navnene på alle de røde og de blå bolcher, i samme SQL udtræk.
``` SELECT navn FROM `bolcher` WHERE `farve` = "Rød" OR `farve` = "Blå" ```
### Inner join
```  SELECT navn FROM `bolcher` INNER JOIN `bolche_farver` ON bolcher.FK_bolche_farve_id = bolche_farver.bolche_farve_id WHERE `bolche_farve_beskrivelse` = "Rød" OR `bolche_farve_beskrivelse` = "Blå" ```

2.4 Find og udskriv navnene på alle bolcher, der ikke er røde, sorteret alfabetisk.
``` SELECT navn FROM `bolcher` WHERE NOT `farve` = "Rød" ORDER BY navn ASC ```
### Inner join
``` SELECT navn FROM `bolcher` INNER JOIN `bolche_farver` ON bolcher.FK_bolche_farve_id = bolche_farver.bolche_farve_id WHERE NOT `bolche_farve_beskrivelse` = "Rød" ORDER BY navn ASC ```

2.5 Find og udskriv navnene på alle bolcher som starter med et “B”.
``` SELECT navn FROM `bolcher` WHERE `navn` LIKE 'B%' ```
### Inner join
``` SELECT navn FROM `bolcher` WHERE `navn` LIKE 'B%'  ```

2.6 Find og udskriv navnene på alle bolcher, hvor der i navnet findes mindst ét “e”.
``` SELECT * FROM `bolcher` WHERE `navn` LIKE '%e%' ```
### Inner join
``` SELECT navn FROM `bolcher` WHERE `navn` LIKE '%e%' ```

2.7 Find og udskriv navn og vægt på alle bolcher der vejer mindre end 10 gram, sorter stigende efter vægt.
``` SELECT `navn`, `vaegt` FROM `bolcher` HAVING `vaegt` < 10 ORDER BY `vaegt` ASC ```
### Inner join
``` SELECT navn , vaegt FROM `bolcher` HAVING `vaegt` < 10 ORDER BY `vaegt` ASC ```

2.8 Find og udskriv navne på alle bolcher, der vejer mellem 10 og 12 gram (begge tal inklusiv), sorteret alfabetisk og derefter vægt.
``` SELECT * FROM `bolcher` WHERE `vaegt` BETWEEN 10 AND 12 ORDER BY `navn`, `vaegt` ASC ```
### Inner join
``` SELECT navn , vaegt FROM `bolcher` WHERE `vaegt` BETWEEN 10 AND 12 ORDER BY `navn`, `vaegt` ASC ```

2.9 Find og udskriv de tre største (tungeste) bolcher
``` SELECT * FROM `bolcher` ORDER BY `vaegt` DESC LIMIT 3 ```
### Inner join
``` SELECT * FROM `bolcher` ORDER BY `vaegt` DESC LIMIT 3 ```

2.10 Udskriv alle informationer om et tilfældigt bolche, udvalgt af systemet (sql).
``` SELECT * FROM `bolcher` ORDER BY RAND() LIMIT 1 ```
### Inner join
``` SELECT * FROM `bolcher` ORDER BY RAND() LIMIT 1 ```

---

farve | vægt | smags-surhed | smags-styrke | smags-type 
--- | --- | --- | --- | ---
rød | 8 | sødt | mild | jordbær 
gul | - | bittert | medium | citron
 -| - | let bittert | stærk | anis

 ----
## Øvelse 5

``` SELECT navn , raavarepris / vaegt * 1000 * 1.25 , raavarepris / vaegt * 1000 FROM `bolcher` ```

``` SELECT navn , ROUND((((raavarepris / vaegt) * 2.5) * 10) * 1.25,2) AS`m/moms` , ROUND(((raavarepris / vaegt) * 2.5) * 10, 2) AS`u/moms` FROM `bolcher` ```

## Øvelse 6

### 6.1 Find og udskriv navnene på alle de røde og de blå bolcher, i samme SQL udtræk.
``` SELECT navn , bolche_farve_beskrivelse FROM `bolcher` INNER JOIN `bolche_farver` ON bolcher.FK_bolche_farve_id = bolche_farver.bolche_farve_id WHERE `bolche_farve_beskrivelse` IN ("Rød", "Blå") ```

### 6.2 Find og udskriv navnene på alle bolcher, der ikke er røde, sorteret alfabetisk.
``` SELECT navn , bolche_farve_beskrivelse FROM `bolcher` INNER JOIN `bolche_farver` ON bolcher.FK_bolche_farve_id = bolche_farver.bolche_farve_id WHERE `bolche_farve_beskrivelse` NOT IN ("Rød") ```

### 6.3 Udskriv hvor mange bolscher der vejer under 15 g.
``` SELECT COUNT(`vaegt`) FROM `bolcher` WHERE `vaegt` < 15 ```

### 6.4 Udskriv hvor mange forskellige forskellige bolcher der er i tabellen
``` SELECT COUNT(*) FROM `bolcher` ```

### 6.5 Udskriv gennemsnitsprisen per bolche
``` SELECT avg(raavarepris) FROM `bolcher` ```

 ### 6.6 Udskriv navn og pris på det dyreste og billigste bolche
 ``` SELECT * FROM `bolcher` WHERE `raavarepris` = (SELECT MIN(`raavarepris`) FROM `bolcher`) OR `raavarepris` = (SELECT MAX(`raavarepris`) FROM `bolcher`) ORDER BY `raavarepris` DESC ```