---
tags: [studia, python, notatki]
aliases: [Python Madej podstawy]
created: 2026-10-19
updated: 2026-10-19
---

# Python (M. Madej) – podstawy i struktury danych

> [!abstract] W skrócie
> Zmienne, typy, napisy, operatory oraz cztery struktury danych: lista, krotka, słownik, zbiór.

## Zmienne i typy

- Nazwy: litery, cyfry, `_`; **nie zaczynaj od cyfry**, bez spacji, wielkość liter ma znaczenie. Styl: `snake_case`.
- Typy: `str` (tekst), `int` (całkowite), `float` (ułamki), `bool` (`True`/`False`), `None` (brak wartości).
- Stałe nazywamy WIELKIMI literami (`MAX_LENGTH = 1000`) – to tylko umowa, Python ich nie pilnuje.
- Wiele przypisań naraz: `x, y, z = 1, 2, 3`.
- `import this` pokazuje „Zen Pythona" (m.in. „Prostota jest lepsza od zawiłości").

## Tekst (`str`)

- `f"{imie} {nazwisko}"` – **f-string**, wstawia zmienne do tekstu.
- `\n` nowa linia, `\t` tabulator.
- Wycinanie: `tekst[1:4]`, `tekst[-1]` (ostatni znak), `tekst[::2]` (co drugi).
- `+` skleja teksty, `in` sprawdza zawieranie, `len()` długość.

> [!warning] Częsty błąd
> `"rok " + 2000` da `TypeError` – liczby i tekstu nie dodasz. Użyj przecinka w `print("rok", 2000)` albo f-stringa.

## Wejście/wyjście i operatory

- `input()` zawsze zwraca **tekst** → liczbę uzyskasz przez `int(input(...))`.
- Arytmetyka: `+ - * /`, `//` (dzielenie całkowite), `%` (reszta), `**` (potęga).
- Porównania: `== != < > <= >=`. Logika: `not`, `and`, `or`.

## Struktury danych

| Struktura | Zapis | Cechy |
|---|---|---|
| **Lista** | `[1, 2, 3]` | uporządkowana, **zmienna** |
| **Krotka** | `(1, 2, 3)` | uporządkowana, **niezmienna** |
| **Słownik** | `{"imie": "Jan"}` | pary klucz→wartość |
| **Zbiór** | `{1, 2, 3}` | unikalne elementy |

**Lista** – metody: `append`, `extend`, `insert`, `remove`, `pop`, `clear`, `index`, `count`, `sort`, `reverse`, `copy`. Funkcje: `len`, `min`, `max`, `sum`. Łączenie: `lista1 + lista2`.

**Słownik** – `d["klucz"] = wartość` dodaje, `del d["klucz"]` usuwa; metody `get`, `pop`, `update`, `keys`, `clear`.

**List comprehension** – lista w jednej linii:

```python
kwadraty = [x ** 2 for x in range(20) if x % 2 == 0]
```

Podobnie zbiór: `{i**2 for i in range(5)}`.

> [!tip] Podpowiedź
> `dir(list)` pokazuje wszystkie metody listy, `help(list)` – opis.

## Powiązane

- [[Język Python – M. Madej]] – strona główna
- [[Python Madej – sterowanie i pliki]] – następny temat
- [[Python Lewandowski – moduł 3 (funkcje, słowniki, moduły)]] – słowniki i krotki u drugiego prowadzącego
- Źródło: [[Studia/Zajęcia język Python M. Madej/Materiały/język python.pdf|język python.pdf]]
