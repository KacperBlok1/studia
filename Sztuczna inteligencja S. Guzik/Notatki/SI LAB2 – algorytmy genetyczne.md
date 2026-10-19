---
tags: [studia, si, notatki]
aliases: [Algorytmy genetyczne, GA]
created: 2026-10-19
updated: 2026-10-19
---

# SI LAB2 – algorytmy genetyczne

> [!abstract] W skrócie
> Optymalizacja wzorowana na **ewolucji**: zamiast jednego rozwiązania trzymamy **populację**, lepsze rozwiązania częściej „mają dzieci", a **krzyżowanie + mutacja** tworzą nowe. Nie gwarantuje optimum, ale działa tam, gdzie sprawdzenie wszystkiego (brute force) jest za wolne.

## Pętla algorytmu

1. Losowa populacja.
2. Ocena każdego osobnika (**funkcja oceny / fitness**).
3. Jeśli koniec (np. liczba pokoleń) → stop.
4. Wybór rodziców → **krzyżowanie** → **mutacja** → nowa populacja → wracamy do 2.

(Metodę zaproponował John Holland w latach 70.)

## Kodowanie rozwiązania

To najważniejsza decyzja.

- **Plecak**: ciąg bitów (bierzemy przedmiot / nie).
- **Komiwojażer (TSP)**: permutacja miast. Zwykłe krzyżowanie zepsułoby trasę (powtórzone miasta), więc używa się specjalnego, np. **OX**.

## Selekcja i ograniczenia

- **Ruletka** – szansa proporcjonalna do oceny.
- **Turniej** – najlepszy z k losowych (odporniejszy, łatwiejszy w strojeniu).
- Rozwiązania niepoprawne (np. plecak za ciężki): **kara**, **kara śmierci** albo **naprawa**.

## Przykłady z laba

- **Plecak**: 12 przedmiotów, nośność 7 kg, 4096 kombinacji – dało się sprawdzić wszystkie i porównać z wynikiem algorytmu.
- **Komiwojażer**: 10 miast Pomorza, powrót do Gdańska, ponad 180 tys. tras. Losowa populacja ~550 km, po ewolucji wyraźnie krócej.

## Parametry mają znaczenie

- Za mała populacja → przedwczesna zbieżność (utknięcie).
- Za duża mutacja → błądzenie losowe.
- **Elitaryzm** chroni najlepszych osobników.
- Wynik zależy od losowości, więc **uśredniaj kilka uruchomień**.

## Zadania z laba

1. Naprawa zamiast kary śmierci w plecaku.
2. Ruletka vs turniej – kiedy ruletka zawodzi?
3. Mutacja inwersji w TSP.
4. Tabela: populacja {20, 60, 150} × prawdopodobieństwo mutacji.

## Powiązane

- [[Sztuczna inteligencja – S. Guzik]] – strona główna
- Poprzedni: [[SI LAB1 – metody reprezentacji wiedzy]], następny: [[SI LAB3 – systemy regułowe]]
- Dobry kandydat na jedną z dwóch metod w projekcie – [[SI – zasady zaliczenia i projekt]]
- Materiały: [[Studia/Sztuczna inteligencja S. Guzik/Materiały/SI_LAB02_Algorytmy_genetyczne.pptx|prezentacja]], [[Studia/Sztuczna inteligencja S. Guzik/Materiały/SI_LAB02_Algorytmy_genetyczne.pdf|instrukcja PDF]]
