---
tags: [studia, python, notatki]
aliases: [Python moduł 3, Funkcje w Pythonie, Klasy w Pythonie]
created: 2026-10-19
updated: 2026-10-19
---

# Python – moduł 3: funkcje, słowniki, moduły, napisy, wyjątki, klasy, generatory

> [!abstract] W skrócie
> Największy moduł: własne funkcje, krotki/słowniki/zbiory, moduły, metody na tekście, obsługa błędów (`try/except`), klasy z dziedziczeniem i generatory.

## 1. Funkcje

```python
def powitaj(imie, nazwisko="Kowalski"):   # nazwisko ma wartość domyślną
    return "Hej " + imie + " " + nazwisko

powitaj("Adam")
powitaj(nazwisko="Nowak", imie="Ola")     # argumenty nazwane – kolejność dowolna
```

- Parametry: pozycyjne, nazwane, domyślne. `return` zwraca wynik; bez `return` funkcja zwraca `None`.
- **Zakresy**: zmienna utworzona w funkcji jest lokalna. Żeby zmienić globalną: `global zmienna`.
- **Rekurencja** – funkcja wywołuje samą siebie, musi mieć warunek zakończenia.

## 2. Krotka, słownik, zbiór

- **Krotka** `(1, 2, 3)` – jak lista, ale niemutowalna. **Zbiór** `{3, 4, 2}` – unikalne elementy.
- **Słownik** – pary klucz → wartość (klucze unikalne):

```python
tel = {"Adam": 555865500}
tel["Ola"] = 123456789       # dodanie / zmiana
tel.update({"Ola": 111})
del tel["Adam"]
for k, v in tel.items():
    print(k, v)
```

## 3. Moduły

`import math` → `math.sqrt(4)`; `from math import pow, pi`; `import math as matma`. Własny moduł = własny plik `.py`. Przydatne: `math` (`sqrt`, `floor`, `ceil`, `factorial`), `random` (`randint`, `choice`, `sample`), `dir(modul)`.

## 4. Napisy (stringi)

- Znaki to liczby: `ord("A")` → 65, `chr(65)` → `"A"` (ASCII / Unicode, najczęściej UTF-8).
- Napisy są **niemutowalne** – zmiana = nadpisanie nowym napisem.
- Metody: `find()` (zwraca -1, gdy brak), `index()` (błąd, gdy brak), `lower()`, `upper()`, `title()`, `replace()`, `split()`, `strip()`, `startswith()`, `endswith()`, `isdigit()`, `isalpha()`, `isalnum()`.
- Porównywanie napisów działa po kodach znaków (`"tekst" > "Tekst"` → `True`).

## 5. Wyjątki (obsługa błędów)

```python
try:
    print(a / b)
except ZeroDivisionError:
    print("dzielenie przez 0")
except Exception as e:
    print(e)
else:
    print("bez błędu")          # tylko gdy nie było wyjątku
finally:
    print("zawsze")             # zawsze na końcu
```

- Pasuje **pierwszy** pasujący `except` – szczegółowe wyjątki dawaj przed ogólnymi (`ZeroDivisionError` < `ArithmeticError` < `Exception` < `BaseException`).
- `raise` – zgłaszasz wyjątek sam; `assert warunek` – rzuca `AssertionError`, gdy warunek fałszywy.
- Własny wyjątek: `class MojBlad(Exception): pass`.

## 6. Klasy i obiekty

```python
class Pojazd:
    def __init__(self, kolor, marka):      # konstruktor
        self.kolor = kolor
        self.marka = marka
        self.__czy_jedzie = False          # pole prywatne (dwa podkreślniki)
    def jedz(self):
        self.__czy_jedzie = True

class Samochod(Pojazd):                    # dziedziczenie
    def __init__(self, kolor, marka, nadwozie):
        super().__init__(kolor, marka)
        self.nadwozie = nadwozie
```

- **Klasa** = wzór, **obiekt** (instancja) = konkretny egzemplarz.
- `__str__` – jak obiekt ma się wyświetlać w `print`.
- Przydatne: `isinstance()`, `issubclass()`, `hasattr()`, `getattr()`, `setattr()`, `is` (czy to ten sam obiekt).
- Zmienne klasy (np. licznik) są wspólne dla wszystkich instancji.

## 7. Generatory

Funkcja z `yield` – zwraca wartości po kolei i **pamięta stan**, więc nie trzyma całej listy w pamięci.

```python
def fn(n):
    for i in range(n):
        yield i
list(fn(5))   # [0, 1, 2, 3, 4]
```

> [!tip] Na zaliczenie
> Ten moduł dostarcza prawie wszystkie elementy wymagane w projekcie: funkcje, słowniki, moduły, wyjątki, klasy, generatory. Brakuje jeszcze plików i wyrażeń regularnych.

## Powiązane

- [[Język Python – K. Lewandowski]] – strona główna
- [[Python Lewandowski – moduł 2 (pętle, warunki, listy)]] – poprzedni moduł
- [[Python Madej – funkcje i moduły]] – lambda, `*args`, generatory z drugiego kursu
- [[Python Lewandowski – zaliczenie]] – wymagania projektu
- Źródło: [[Studia/Zajęcia język Python K. Lewandowski/Materiały/Python Moduł 3.pdf|Python Moduł 3 (PDF)]]
