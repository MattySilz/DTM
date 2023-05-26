# Value by Alpha maps in QGIS

## Datenquelle (Geometrien & Wahlergebnisse)
[Bundestagswahl 2021](https://www.bundeswahlleiterin.de/bundestagswahlen/2021/ergebnisse.html)

Tabelle mit Wahlergebnissen bereinigen:
![Screenshot 2023-05-26 095517](https://github.com/MattySilz/DTM/assets/134683739/a96f2010-dc11-4485-a0bd-ebed10133e1f)

## QGIS

1.) Vergleich SPD vs. CDU: Stimmen stärkere Parte regelbasiert darstellen
Regel Olaf:
```
 "BTW_SPD" > "BTW_CDU" 
```
Regel Armin:
```
 "BTW_SPD" < "BTW_CDU" 
 ```
 
 2.) Ebene "Alpha" ergänzen und auf Symbolebene 1 setzen
 
![image](https://github.com/MattySilz/DTM/assets/134683739/10f0a6eb-c310-4f4b-9192-bf12708882f7)

3.) Regel für Ebene "Alpha": Über Einfache Füllung unter "Füllfarbe" -> "Datendefinierte Übersteuerung" -> "Bearbeiten"

![image](https://github.com/MattySilz/DTM/assets/134683739/dd4782ad-5628-4cb0-a705-b05fccf31562)

Grundprinzip: 
```
set_color_part('black','alpha',126)
```
Statt einem festen Alpha-Wert wird dieser wertebasierte aus einem anderen Attribut für jede Bezugseinheit berechnet.
```
set_color_part('black','alpha',
scale_linear( "BTW_G" ,100000,200000,200,0))
```
