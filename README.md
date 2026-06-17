# (Titlul)
Generator muzical in Max

Proiectul este un generator de muzica realizat in Cycling '74 Max/MSP, care produce
linii melodice MIDI intr-un mod partial aleatoriu.
## (Instalare)
Se deschide in MAX.

## (Utilizare)
Se seteaza Patternul , volumul si durata notelor, BPM, Gama si grupa de note initiala.

# Dezvoltarea proiectului

  Patch-ul este compus din 2 matrici (matrixctrl) ce pot seta diverse patternuri pentru 
notele redate de cele 2 clape. Timpul de redare (BPM) se poate seta in ms de catre utilizator.
Patch-ul are 3 game disponibile in care toate notele generate vor fi convertite automat prin 
snapping la cea mai apropiata nota mai mare. Pentru fiecare serie de clape exista un selector 
pentru deciderea unui pattern default de note sub forma de liste.

  Pentru a face rezultatul relevant muzical, a fost adaugat un modul de repetitie imediat dupa
zl.slice, acolo unde notele ies sub forma de numere, una cate una. Functionarea este organizata
pe cicluri de 8 pasi, impartite in doua ture de cate 4, gestionate de un counter 0 7. lasa sirul
sa ajunga la generator, care produce 4 note noi. Acestea se aud live si, in paralel, sunt colectate
cu zl.group 4 si retinute intr-un zl.reg. acelasi gate 2 ruteaza calea catre registru in loc de 
generator, intrerupand circuitul de generare. In acest interval, zl.nth reda exact cele 4 note 
retinute, in aceeasi ordine.
