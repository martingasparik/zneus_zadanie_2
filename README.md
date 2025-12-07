# Documentation
## EDA
In the first phase, the "Animals-10" dataset, which contains images of 10 different animal species, was analyzed.
Firstly, Loading and translation - (and correcting it)
Vlastnosti obrázkov:
- Dataset obsahuje celkovo 26 179 obrázkov.
- Dominantný formát súborov je .jpeg (~24 000+), nasleduje .jpg a malé množstvo .png.
- Väčšina obrázkov (26 128) používa farebný model RGB.
- Rozmery obrázkov nie sú jednotné, s priemernou šírkou cca 320 px a výškou 252 px.
Distribúcia tried: Pôvodný dataset bol značne nevyvážený. Najpočetnejšie triedy (pes a pavúk) mali takmer 5000 obrázkov, zatiaľ čo najmenej početné (slon) len okolo 1400.
___
## Preprocessing
- Filtrovanie: Boli ponechané iba obrázky s farebným režimom RGB.
- Vyváženie datasetu: Aby sa eliminovala nevyváženosť tried, bol počet obrázkov pre každú triedu upravený na 2000. Pre triedy s vyšším počtom sa použila metóda undersample (náhodný výber bez opakovania).
- Split: 0.7/0.15/0.15
___
## Augmentácia a Generátory dát
- Na načítanie a úpravu obrázkov počas trénovania sa používa ImageDataGenerator 
- Parametre obrázkov: Všetky obrázky sú počas načítania zmenšené na veľkosť 224, 224px alebo menšie a spracovávané v batch po 32.
- Tréningový generátor: Aplikuje normalizáciu (hodnoty pixelov 0-1) a rôzne augmentačné techniky na zvýšenie robustnosti modelu:
  - Rotácia (do 20°)
  - Horizontálny a vertikálny posun (0.2)
  - Horizontálne prevrátenie (flip)
  - Zoom a skosenie (shear)

Validačný a Testovací generátor: Aplikujú iba normalizáciu (rescale=1./255) bez ďalších deformácií obrazu, aby sa zachovala objektívnosť pri vyhodnocovaní.
