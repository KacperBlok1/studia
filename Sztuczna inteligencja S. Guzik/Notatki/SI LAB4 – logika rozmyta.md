---
tags: [studia, si, notatki]
aliases: [Logika rozmyta, Fuzzy logic, Sterownik Mamdaniego]
created: 2026-10-19
updated: 2026-10-19
---

# SI LAB4 – logika rozmyta

> [!abstract] W skrócie
> Logika rozmyta radzi sobie z **nieostrymi pojęciami** („ciepło", „szybko"). Nie pyta „tak/nie", tylko **w jakim stopniu** (0–1) coś pasuje. 23 °C to trochę „komfort", trochę „ciepło".

## Czym się różni od CF i prawdopodobieństwa

- Prawdopodobieństwo / CF: *czy* coś zajdzie, *na ile jesteśmy pewni*.
- Logika rozmyta: *w jakim stopniu* pojęcie pasuje.

## Podstawy

- **Zmienna lingwistyczna** – np. temperatura o wartościach *zimno, komfort, gorąco*.
- **Stopień przynależności** μ ∈ [0, 1] – dla każdej wartości jest funkcja (trójkątna, trapezowa, gaussowska). Sąsiednie zbiory **zachodzą na siebie**.
- Operacje: **AND = minimum**, **OR = maksimum**, **NOT = 1 − μ**.

## Sterownik Mamdaniego – 4 kroki

1. **Fuzyfikacja** – liczby z czujników → stopnie przynależności.
2. **Wnioskowanie** – każda reguła ma stopień odpalenia = minimum jej przesłanek.
3. **Agregacja** – łączymy wyniki reguł.
4. **Defuzyfikacja** – z rozmytego wyniku wracamy do jednej liczby (np. środek ciężkości).

Przykład z laba: wentylator – wejścia temperatura i wilgotność, wyjście moc; cały sterownik w <50 linijkach Pythona.

## Jak projektować sterownik

- Zbiory sąsiednie zachodzą na siebie (mniej więcej w połowie) – inaczej powstają „dziury" bez reguły.
- Każda kombinacja wejść ma regułę.
- Zacznij od mało reguł, potem stroisz; testuj przypadki graniczne.
- **Powierzchnia sterowania** (mapa ciepła) – im płynniejsza, tym lepiej; „schodki" = za mało reguł lub za wąskie zbiory.

## Gdzie to spotkasz

Pralki, klimatyzatory, autofokus, metro w Sendai (płynne hamowanie), scoring ryzyka.

## Zadania z laba

1. Powierzchnia sterowania (temperatura 0–40 °C × wilgotność).
2. Funkcje trapezowe zamiast trójkątnych.
3. Własny sterownik (tempomat / napiwek / podlewanie): 2 wejścia × 3 zbiory, 1 wyjście, 7 reguł; porównanie z regułami ostrymi.

## Powiązane

- [[Sztuczna inteligencja – S. Guzik]] – strona główna
- Poprzedni: [[SI LAB3 – systemy regułowe]] (CF), następny: [[SI LAB5 – uczenie maszynowe i sieci neuronowe]]
- Materiały: [[Studia/Sztuczna inteligencja S. Guzik/Materiały/SI_LAB04_Systemy_z_wiedzą_niepewną_logika_rozmyta.pptx|prezentacja]], [[Studia/Sztuczna inteligencja S. Guzik/Materiały/SI_LAB04_Systemy_z_wiedzą_niepewną_logika_rozmyta.pdf|instrukcja PDF]]
