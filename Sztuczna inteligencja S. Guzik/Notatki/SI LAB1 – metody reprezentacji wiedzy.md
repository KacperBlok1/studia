---
tags: [studia, si, notatki]
aliases: [Reprezentacja wiedzy, Sieć semantyczna, Ramki]
created: 2026-10-19
updated: 2026-10-19
---

# SI LAB1 – metody reprezentacji wiedzy

> [!abstract] W skrócie
> Program nie rozumie świata – operuje na jego **modelu**. Reprezentacja wiedzy to sposób zapisania faktów i zależności tak, by program mógł **wyciągać nowe wnioski**. Trzy metody: sieć semantyczna, ramki, logika i reguły.

## Dane a wiedza

Dane: „Tweety jest pingwinem". Wiedza: pingwin to ptak, ptaki zwykle latają, **ale** pingwin nie lata. Wnioskowanie daje odpowiedzi, których nie było wprost w danych.

## Dobra reprezentacja to taka, która jest…

- **adekwatna** – da się zapisać wszystko, co trzeba (też wyjątki),
- **umożliwia wnioskowanie** – wyprowadzisz nową wiedzę,
- **efektywna** – wnioskowanie jest szybkie,
- **czytelna** – człowiek może sprawdzić zapis.

## 1. Sieć semantyczna

Graf: **węzły = pojęcia**, **krawędzie = relacje**. Kluczowa relacja „jest" (pingwin jest ptakiem, ptak jest zwierzęciem) buduje hierarchię. Cechy się **dziedziczą** od przodków, a **wyjątek nadpisuje** cechę ogólną (ptak lata, pingwin nie). W kodzie: wiedza jako trójki *(podmiot, relacja, obiekt)*.

## 2. Ramki (frames)

Pomysł Marvina Minsky'ego. Obiekt = zestaw **slotów** (pól) z wartościami, w tym domyślnymi odziedziczonymi z ramki ogólniejszej.

- **demon if-needed** – liczy wartość dopiero na żądanie (np. powierzchnia = długość × szerokość),
- **demon if-added** – pilnuje poprawności przy dodawaniu wartości.

Przykład z lab: sala B214 → sala laboratoryjna → pokój. Ramki to przodek programowania obiektowego.

## 3. Logika i reguły

- Fakt: `rodzic(Anna, Bartek)`
- Reguła: `dziadek(X,Z) ← rodzic(X,Y) ∧ rodzic(Y,Z)`
- **Wnioskowanie w przód** – od faktów do wniosków, aż nic nowego nie powstaje.
- **Wnioskowanie wstecz** – od pytania do faktów, które je potwierdzają.

## Zadania z laba

1. Dodać gałąź „ssaki" do sieci (np. nietoperz).
2. Metoda `czy_jest(a, b)` – czy pojęcie a jest (pośrednio) b.
3. Ramki dla pojazdów z demonem na zasięg.
4. Reguła pradziadka.
5. Wnioskowanie wstecz dla `dziadek(Anna, ?)`.

> [!tip] Projekt
> Na tych zajęciach wybiera się zespół, temat i zakłada repozytorium (link w Moodle) – patrz [[SI – zasady zaliczenia i projekt]].

## Powiązane

- [[Sztuczna inteligencja – S. Guzik]] – strona główna
- Następny lab: [[SI LAB2 – algorytmy genetyczne]]; reguły wrócą w [[SI LAB3 – systemy regułowe]]
- Materiały: [[Studia/Sztuczna inteligencja S. Guzik/Materiały/SI_LAB01_Metody_reprezentacji_wiedzy.pptx|prezentacja]], [[Studia/Sztuczna inteligencja S. Guzik/Materiały/SI_LAB01_Metody_reprezentacji_wiedzy.pdf|instrukcja PDF]]
