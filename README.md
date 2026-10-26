# Les meves fitxes de funcions de Google Sheets

> Copia aquesta plantilla al teu repositori com a `funcions.md`. Fes una fitxa per funció.
> Escriu amb les teves paraules. Els exemples de la lliga, provats al teu full.

---

## COUNTIFS

**Documentació:** <https://support.google.com/docs/answer/3256550?hl=ca>

**Què fa:** Aquesta funció conta les cel·les d'un interval de criteris segons més d'un criteri i/o interval

**Sintaxi:**

```
COUNTIFS(interval_de_criteris1, criteri1, [interval_de_criteris2, criteri2, etc.])
```

| Argument | Obligatori? | Què és |
|---|---|---|
| `interval_de_criteris1` | Sí | valor que cal cercar |
| `criteri1` | Sí | Prova que s'aplica a interval_de_criteris1 |
|`interval_de_criteris2`|No|Interval adicional|
|`criteri2`|No|Criteri adicional|

**Exemple de la documentació:** `COUNTIFS(A7:A24, ">6", B7:B24, "<"&DATE(1969,7,20))`

**El meu exemple amb la lliga:** 

```
=COUNTIF('Jornada 1'!$G$2:$G$49,A2)
```

Resultat: `16` (Vol dir que al full "Jornada 1" entre les cel·les G2:G49 hi ha 16 cel·les que tenen el mateix contingut que la cel·la A2 del full actual)

**Compte!** Els intervals addicionals han de contenir el mateix nombre de files i columnes que interval_de_criteris1.

---

## SUMIFS

**Documentació:** <https://support.google.com/docs/answer/3238496?hl=ca&sjid=12507546114658161523-EU>

**Què fa:** Aquesta funció suma el contingut les cel·les d'un interval de criteris segons més d'un criteri i/o interval

**Sintaxi:**

```
SUMIFS(interval_de_suma, interval_de_criteris1, criteri1, [interval_de_criteris2, criteri2, etc.])
```

| Argument | Obligatori? | Què és |
|---|---|---|
| `interval_de_suma` | Sí | interval que es suma |
| `interval_de_criteris1` | Sí | Interval del criteri1 |
|`criteri1`|Sí| prova que cal aplicar a l'argument interval_de_criteris1 |
|`interval_de_criteris2`|No| Interval adicional |
|`criteri2`|No| Criteri adicional |

**Exemple de la documentació:** `SUMIFS(A1:A10, B1:B10, ">20", C1:C10, "<30")`

**El meu exemple amb la lliga:** 

```
=SUMIFS('Jornada 1'!$M$2:$M$49, 'Jornada 1'!$G$2:$G$49, A2)
```

Resultat: `846.94` (Vol dir que la suma de les les cel·les G2:G49 del full "Jornada 1" que estan a la mateixa fila que les cel·les G2:G49 del full "Jornada 1" que tenen el mateix contingut que la cel·la actual dona 846.94.)

---

## IFS

**Documentació:** <https://support.google.com/docs/answer/7014145?hl=ca&sjid=12507546114658161523-EU>

**Què fa:** Evalua diferents condicions i es queda amb el primer encert.

**Sintaxi:**

```
IFS(condició, valor1, [condició2, valor2, …])
```

| Argument | Obligatori? | Què és |
|---|---|---|
| `condició` | Sí | Condició a tenir en conte |
| `valor1` | Sí | Retorn si és cert |
|`condició2`|No| Condició opcional |
|`valor2`|No| valor adicional |

**Exemple de la documentació:** `IFS(A1:A5 > 3, "més gran", A1:A5 = 3, "igual")`

**El meu exemple amb la lliga:** 

```
=IFS(AND(G2 = "Seguidor de línia", L2<1000),"OK",AND(G2 = "Laberint", L2<1200),"OK",AND(G2 = "Velocitat", L2<900),"OK", TRUE,"EXCÉS")
```

Resultat: `OK` (Si G2 és igual a "Seguidor de línia" i L2 és més petit que 1000 mostra "OK", si no, si G2 és igual a "Laberint" i L2 és més petit que 1200 mostra "OK", si no, si G2 és igual a si G2 és igual a Laberint i L2 és més petit que 1200 mostra "OK", si no,"Velocitat" i L2 és més petit que 900 mostra "OK", si no, mostra "EXCÉS" )

---

## XLOOKUP

**Documentació:** <https://support.google.com/docs/answer/12405947?hl=en&sjid=13015510690200445691-EU>

**Què fa:** La funció XLOOKUP torna els valors de l'interval de resultats d'acord amb la posició en què s'ha trobat una coincidència a l'interval de cerca. Si no es troba cap coincidència, torna la coincidència més propera.

**Sintaxi:**

```
XLOOKUP(valor_de_cerca; interval_cerca; interval_de_resultats, valor_no_trobat; mode_de_coincidència; mode_de_cerca)
```

| Argument | Obligatori? | Què és |
|---|---|---|
| `valor_de_cerca` | Sí | Valor que es vusca |
| `interval_cerca` | Sí | Interval en el que es cerca el valor |
|`interval_de_resultats`|Sí| interval que cal tenir en compte per al resultat. La mida de la fila o de la columna d'aquest interval hauria de ser la mateixa que la d'interval_cerca, segons com es faci la cerca. |
|`valor_no_trobat`|No| Resposta si no es troba el valor |
|`mode_de_coincidència`|No| Troba una coincidencia amb el valor |
|`mode_de_cerca`|No| Mode de vuscar el interval de cerca |

**Exemple de la documentació:** `XLOOKUP("Poma"; A2:A; E2:E)`

**El meu exemple amb la lliga:** 

```
=XLOOKUP($Q$3,'Jornada 1'!$A$2:$A$49,'Jornada 1'!$E$2:$E$49,"NO EXISTEIX")
```

Resultat: `OK` (Vusca el valor que està a la columna E2:E49 del full "Jornada 1" que comparteix fila amb el valor Q3 del full actual a la columna A2:A49 del full "Jornada 1", si no es troba el valor mostra " NO EXISTEIX")

**Compte!** Si interval_de_resultats té més d'una fila o columna, la sortida serà la fila o columna sencera de l'índex en què s'hagi trobat una coincidència a interval_cerca.

---

## ⭐ Extres: AVERAGEIFS, MAXIFS, UNIQUE, SORT

(mateixa estructura)

---

## Preguntes de lectura

1. Què passa amb `SUMIFS` si l'interval de suma i l'interval del criteri no tenen la mateixa mida?

Aquest dona error #VALUE! ja que no es pot sumar correctament.

2. Què torna `IFS` si cap de les condicions és certa? Com ho podeu evitar?

Torna error #N/A! ja que no sap que mostrar. Per solucionar-ho, al final de la fòrmula posa: ,TRUE, "El que es mostra quan no hi ha encerts".

3. Per a què serveix el quart argument de `XLOOKUP`? Què passa si no el poseu i no es troba res?

Serveix per a mostrar alguna cosa si no es troba el valor, si no es posa i no es trova el valor surt l'error #N/A!.

4. Escriu la sintaxi de `SUMIF` i la de `SUMIFS` una sota l'altra. Què canvia de lloc?

SUMIF(interval, criteri, [interval_de_suma])

SUMIFS(interval_de_suma, interval_de_criteris1, criteri1, [interval_de_criteris2, criteri2, etc.])

En el segon, l'iterval_de_suma pasa a ser obligatori a vanda de tots els criteris extres disponibles.