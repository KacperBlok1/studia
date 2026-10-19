---
tags: [studia, si, notatki]
aliases: [Sieci neuronowe, Uczenie maszynowe, Propagacja wsteczna]
created: 2026-10-19
updated: 2026-10-19
---

# SI LAB5 – uczenie maszynowe i sieci neuronowe

> [!abstract] W skrócie
> Zamiast pisać reguły ręcznie, **pokazujemy programowi przykłady**, a on sam dobiera parametry modelu. Na labie: sieć neuronowa napisana od zera w NumPy (funkcja XOR) i gotowa sieć ze scikit-learn (rozpoznawanie cyfr).

## Rodzaje uczenia

- **Nadzorowane** – przykłady z poprawnymi odpowiedziami.
- **Nienadzorowane** – szukanie struktury w danych.
- **Ze wzmocnieniem** – nagrody za dobre działania.

## Neuron

Suma ważona wejść + **bias** → **funkcja aktywacji** (sigmoida 0–1, tanh, ReLU). **Wagi** to to, czego sieć się uczy.

## Jak sieć się uczy – propagacja wsteczna

1. **Strata** – miara błędu (np. błąd średniokwadratowy).
2. **Gradient** – mówi, w którą stronę zmienić każdą wagę, żeby błąd malał.
3. Błąd „płynie" od wyjścia do wejścia, wagi są poprawiane.
4. **Współczynnik uczenia (lr)** = wielkość kroku (za duży → chaos, za mały → wolno).

**Dlaczego XOR?** W 1969 Minsky i Papert pokazali, że pojedynczy neuron go nie nauczy (punktów nie da się rozdzielić jedną prostą) – potrzebna jest warstwa ukryta. Po ok. 1000 epok sieć uczy się XOR poprawnie.

## Cyfry w scikit-learn

~1800 obrazków cyfr → podział na część **uczącą** i **testową** → standaryzacja cech → uczenie. Ocena: **dokładność** i **macierz pomyłek** (wiersze = prawdziwa cyfra, kolumny = odpowiedź modelu, poza przekątną = błędy).

## Uwaga: przeuczenie

Model świetny na danych uczących, słaby na nowych = **przeuczenie**. Dlatego zawsze test na osobnych danych, **walidacja krzyżowa**, regularyzacja, wczesne zatrzymanie.

## Do projektu

- dane z CSV, klasyfikacja → `MLPClassifier`,
- prognoza liczby (cena, czas) → `MLPRegressor`,
- obrazy i tekst → gotowe modele (transfer learning).

## Zadania z laba

1. Zmiana `lr` (0,1 i 5,0) i liczby neuronów ukrytych (2 i 8).
2. Tanh zamiast sigmoidy.
3. Porównanie architektur (16,), (64,), (128, 64) z 5-krotną walidacją krzyżową.
4. Najczęściej mylone cyfry + 5 błędnych klasyfikacji.

> [!warning] Termin projektu
> Oddanie w Moodle **11.01.2027, 23:59**, prezentacje 12.01.2027 – szczegóły w [[SI – zasady zaliczenia i projekt]].

## Powiązane

- [[Sztuczna inteligencja – S. Guzik]] – strona główna
- Poprzedni: [[SI LAB4 – logika rozmyta]], następny: [[SI LAB6 – prezentacje i obrona projektów]]
- Materiały: [[Studia/Sztuczna inteligencja S. Guzik/Materiały/SI_LAB05_Uczenie_maszynowe_i_sztuczne_sieci_neuronowe.pptx|prezentacja]], [[Studia/Sztuczna inteligencja S. Guzik/Materiały/SI_LAB05_Uczenie_maszynowe_i_sztuczne_sieci_neuronowe.pdf|instrukcja PDF]]
