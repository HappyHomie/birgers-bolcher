2.1 Udskriv alle informationer om alle bolcher.
```SELECT * FROM `bolcher` ```

2.2 Find og udskriv navnene på alle de røde bolcher.
``` SELECT * FROM `bolcher` WHERE `farve` = "Rød" ```

2.3 Find og udskriv navnene på alle de røde og de blå bolcher, i samme SQL udtræk.
``` SELECT * FROM `bolcher` WHERE `farve` = "Rød" OR `farve` = "Blå" ```

2.4 Find og udskriv navnene på alle bolcher, der ikke er røde, sorteret alfabetisk.
``` SELECT * FROM `bolcher` WHERE NOT `farve` = "Rød" ORDER BY navn ASC ```

2.5 Find og udskriv navnene på alle bolcher som starter med et “B”.
``` SELECT * FROM `bolcher` WHERE `navn` LIKE 'B%' ```

2.6 Find og udskriv navnene på alle bolcher, hvor der i navnet findes mindst ét “e”.
``` SELECT * FROM `bolcher` WHERE `navn` LIKE '%e%' ```

2.7 Find og udskriv navn og vægt på alle bolcher der vejer mindre end 10 gram, sorter stigende efter vægt.
``` SELECT `navn`, `vaegt` FROM `bolcher` HAVING `vaegt` < 10 ORDER BY `vaegt` ASC ```

2.8 Find og udskriv navne på alle bolcher, der vejer mellem 10 og 12 gram (begge tal inklusiv), sorteret alfabetisk og derefter vægt.
``` SELECT * FROM `bolcher` WHERE `vaegt` BETWEEN 10 AND 12 ORDER BY `navn`, `vaegt` ASC ```

2.9 Find og udskriv de tre største (tungeste) bolcher
``` SELECT * FROM `bolcher` ORDER BY `vaegt` DESC LIMIT 3 ```

2.10 Udskriv alle informationer om et tilfældigt bolche, udvalgt af systemet (sql).
``` SELECT * FROM `bolcher` ORDER BY RAND() LIMIT 1 ```
