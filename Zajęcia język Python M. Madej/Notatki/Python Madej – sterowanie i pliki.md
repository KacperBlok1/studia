---
tags: [studia, python, notatki]
aliases: [Python Madej pętle i pliki]
created: 2026-10-19
updated: 2026-10-19
---

# Python (M. Madej) – warunki, pętle, pliki

> [!abstract] W skrócie
> Jak sterować programem (`if`, `for`, `while`) i jak czytać/zapisywać pliki.

## Warunki

```python
if x > 50:
    print("za szybko")
elif x == 50:
    print("limit")
else:
    print("ok")
```

> [!warning] Wcięcia
> Kod w `if`, `else` i pętlach **musi mieć wcięcie**. Brak wcięcia = `IndentationError`.

## Pętle

- `for zmienna in zbiór:` – po liście, tekście, zakresie.
- `range(1, 5)` daje 1,2,3,4 (**bez** końca); `range(2, 11, 2)` → co 2; `range(10)` → 0..9.
- `while warunek:` – działa, dopóki warunek prawdziwy.
- `break` – wyjdź z pętli, `continue` – następny obieg, `pass` – „nic nie rób" (wypełniacz).

## Pliki

```python
with open("plik.txt", "r") as file:    # with sam zamknie plik
    tekst = file.read()
```

| Tryb | Znaczenie |
|---|---|
| `'r'` | odczyt (błąd, jeśli pliku nie ma) |
| `'w'` | zapis (tworzy plik, **nadpisuje** zawartość) |
| `'a'` | dopisywanie na końcu (tworzy, jeśli brak) |

- Czytanie linia po linii: `for line in file:` albo `file.readlines()`.
- Zapis: `file.write(tekst + "\n")` lub `print(x, file=file)`.

> [!tip] Zapamiętaj
> `with open(...) as file:` to bezpieczny sposób – nie musisz pamiętać o `close()`.

## Powiązane

- [[Język Python – M. Madej]] – strona główna
- [[Python Madej – podstawy i struktury danych]] – poprzedni temat
- [[Python Madej – funkcje i moduły]] – następny temat
- [[Python Lewandowski – moduł 2 (pętle, warunki, listy)]] – pętle u drugiego prowadzącego
- Źródło: [[Studia/Zajęcia język Python M. Madej/Materiały/język python.pdf|język python.pdf]]
