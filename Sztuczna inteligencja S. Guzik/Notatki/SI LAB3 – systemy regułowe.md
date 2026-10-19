---
tags: [studia, si, notatki]
aliases: [System ekspertowy, Systemy regułowe, Współczynnik CF]
created: 2026-10-19
updated: 2026-10-19
---

# SI LAB3 – systemy regułowe i wnioskowanie

> [!abstract] W skrócie
> **System ekspertowy** zapisuje wiedzę specjalisty jako reguły „jeżeli–to". Najważniejsze: **wiedza jest oddzielona od silnika** wnioskującego – dodanie reguły nie wymaga zmiany programu. Przykłady: MYCIN, XCON, scoring kredytowy.

## Architektura

- **Baza wiedzy** – reguły (wiedza ogólna).
- **Pamięć robocza** – fakty o bieżącym przypadku (np. konkretny klient).
- **Silnik wnioskujący** – łączy jedno z drugim.
- **Moduł wyjaśniający** – odpowiada „dlaczego?" / „jak doszedłeś do wniosku?".

## Wnioskowanie w przód (cykl rozpoznaj–działaj)

1. Znajdź wszystkie reguły z spełnionymi warunkami → **zbiór konfliktowy**.
2. Wybierz **jedną** regułę według strategii: **priorytet**, **specyficzność** (więcej warunków = pierwszeństwo), **świeżość** faktów, **refrakcja** (ta sama reguła nie odpala dwa razy na tych samych faktach).
3. Odpal, dodaj nowe fakty, powtarzaj.

Przykład z laba: doradca wybierający laptopa (programowanie, VM, budżet, podróże).

## Wnioskowanie wstecz

Start od **hipotezy**, szukamy reguły, która ją wyprowadza. Gdy brakuje faktu i żadna reguła go nie daje – **system pyta użytkownika** (więc zadaje tylko potrzebne pytania). „Dlaczego?" = reguła, którą właśnie dowodzimy.

## Niepewność – współczynnik CF (MYCIN)

- CF od **−1** (fałsz) do **1** (pewne).
- Przesłanki połączone „i" → bierzemy **minimum** (najsłabsze ogniwo).
- Wniosek reguły: **CF przesłanek × CF reguły**.
- Kilka świadectw za tym samym wnioskiem się łączy (wzmacniają się), przeciwne obniżają wynik. Przykład: diagnoza grypy, katar jako lekki dowód przeciw.

## Typowe błędy w bazach reguł

| Błąd | Co to |
|---|---|
| Sprzeczność | z tych samych faktów dwa wykluczające się wnioski |
| Nadmiarowość | jedna reguła zawiera się w drugiej |
| Pętle | A → B i B → A |
| Luki | przypadki bez żadnej rekomendacji |

## Zadania z laba

1. Baza ≥12 reguł + reguła wykluczająca.
2. Strategia specyficzności.
3. Interaktywne wnioskowanie wstecz z pytaniem „dlaczego?".
4. Połączenie przykładu z CF (fakty klienta z pewnością, np. 0,6).

## Powiązane

- [[Sztuczna inteligencja – S. Guzik]] – strona główna
- Poprzedni: [[SI LAB2 – algorytmy genetyczne]], następny: [[SI LAB4 – logika rozmyta]] (inny rodzaj niepewności)
- Podstawy reguł i wnioskowania: [[SI LAB1 – metody reprezentacji wiedzy]]
- Materiały: [[Studia/Sztuczna inteligencja S. Guzik/Materiały/SI_LAB03_Systemy_regułowe_reprezentacja_i_wnioskowanie.pptx|prezentacja]], [[Studia/Sztuczna inteligencja S. Guzik/Materiały/SI_LAB03_Systemy_regułowe_reprezentacja_i_wnioskowanie.pdf|instrukcja PDF]]
