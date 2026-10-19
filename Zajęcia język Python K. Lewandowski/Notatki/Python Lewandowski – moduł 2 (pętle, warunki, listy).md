---
tags: [studia, python, notatki]
aliases: [Python moduł 2, Pętle w Pythonie]
created: 2026-10-19
updated: 2026-10-19
---

# Python – moduł 2: pętle, warunki, listy

> [!abstract] W skrócie
> Jak powtarzać kod (`while`, `for`), jak podejmować decyzje (`if`, operatory logiczne), czym jest algorytm i jak używać list.

## Pętla `while`

Powtarza kod, **dopóki warunek jest prawdziwy**. Kod w pętli musi mieć wcięcie.

```python
counter = 0
while counter < 4:
    print(counter)
    counter += 1
```

> [!warning] Pętla nieskończona
> `while True:` albo warunek, który nigdy nie stanie się fałszem (np. `counter != 0`, gdy licznik omija zero), będzie działać w nieskończoność.

## Pętla `for`

Przechodzi po zakresie, tekście albo liście.

```python
for i in range(10):      # 0..9
    print(i)
for c in "Ala ma kota":  # litera po literze
    print(c, end="")
```

## Sterowanie pętlą

- `break` – przerywa całą pętlę.
- `continue` – przeskakuje do następnego obiegu.
- `else` przy pętli – wykona się, gdy pętla skończyła się **normalnie** (bez `break`).

## Warunki i logika

- `if / elif / else` – wybiera jedną ścieżkę.
- `and` (i), `or` (lub), `not` (nie). Kolejność: najpierw `not`, potem `and`, na końcu `or` – nawiasy porządkują.
- Operatory bitowe: `&` (i), `|` (lub), `~` (negacja), `^` (xor), przesunięcia `<<` i `>>` (np. `8 << 1 = 16`, `8 >> 2 = 2`).

## Algorytmy

Algorytm = jasno opisana lista kroków prowadząca do wyniku. Można go zapisać jako: opis słowny, listę kroków, pseudokod, **drzewo algorytmu** albo **schemat blokowy** (Start/Stop, prostokąty = czynności, romby = decyzje TAK/NIE).

## Listy

```python
lista = [1, 2, 3, 4]
lista[0]       # pierwszy element (indeksy od 0)
lista[-1]      # ostatni element
len(lista)     # ile elementów
del lista[1]   # usuń element
lista.append(5)       # dodaj na końcu
lista.insert(1, 99)   # dodaj w wybranym miejscu
```

> [!tip] Zapamiętaj
> Indeksy zaczynają się od **0**, a ujemne liczą od końca.

## Powiązane

- [[Język Python – K. Lewandowski]] – strona główna
- [[Python Lewandowski – moduł 3 (funkcje, słowniki, moduły)]] – dalszy ciąg
- [[Python Madej – sterowanie i pliki]] – to samo z innej perspektywy (też `if`, `for`, `while`)
- Źródło: [[Studia/Zajęcia język Python K. Lewandowski/Materiały/Python Moduł 2 2.pdf|Python Moduł 2 (PDF)]]
