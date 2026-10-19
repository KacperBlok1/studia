---
tags: [studia, python, notatki]
aliases: [Python Madej funkcje]
created: 2026-10-19
updated: 2026-10-19
---

# Python (M. Madej) – funkcje, lambda, generatory, moduły

> [!abstract] W skrócie
> Własne funkcje, skrócony zapis `lambda`, generatory (`yield`) i organizacja kodu w moduły i pakiety.

## Funkcje wbudowane (te, które wracają)

`print`, `input`, `len`, `type`, `int`/`float`/`str` (zmiana typu), `range`, `sum`, `min`, `max`, `sorted`, `enumerate()` (numeruje elementy), `zip()` (łączy kilka list), `map()` (funkcja na każdym elemencie).

## Własne funkcje

```python
def dziel_przez_3(x):
    return x / 3
```

- Mogą mieć parametry domyślne (`def f(a, b=2)`) – parametry z wartością domyślną **muszą być na końcu**.
- `*args` – dowolna liczba argumentów (trafiają do krotki):

```python
def srednia(*args):
    return sum(args) / len(args)
```

> [!warning] Typowe błędy
> Zła liczba argumentów, literówka w nazwie (wielkość liter!), dwie funkcje o tej samej nazwie (druga nadpisze pierwszą), zły typ argumentu.

## Lambda

Krótka funkcja jednowyrażeniowa:

```python
f = lambda x: x ** 2 + 3
list(map(lambda x: x ** 2, range(10)))
sorted(liczby, key=lambda x: abs(x))
```

## Generatory

Funkcja z `yield` zamiast `return`. **Pamięta stan** i zwraca kolejne wartości na żądanie (`next()`):

```python
def gen_parzyste(N):
    for i in range(N):
        if i % 2 == 0:
            yield i
```

## Moduły i pakiety

- **Moduł** = plik `.py`. `import modul` → `modul.funkcja()`; `from modul import funkcja`.
- **Pakiet** = folder z plikiem `__init__.py` (może być pusty), zawiera moduły.
- Wbudowane moduły: `os` (system plików: `getcwd`, `listdir`), `math` (`floor`, `ceil`), `datetime` (data i czas), `random` (`random`, `choice`).
- Pełna lista: dokumentacja `docs.python.org/3/library`.

> [!tip] Na zaliczenie
> Na ocenę 4,5 aplikacja ma się składać z kilku modułów – patrz [[Python Madej – zaliczenie]].

## Powiązane

- [[Język Python – M. Madej]] – strona główna
- [[Python Madej – sterowanie i pliki]] – poprzedni temat
- [[Python Lewandowski – moduł 3 (funkcje, słowniki, moduły)]] – to samo z drugiego kursu
- Źródło: [[Studia/Zajęcia język Python M. Madej/Materiały/język python.pdf|język python.pdf]]
