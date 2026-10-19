---
tags: [studia, zagrozenia-sieci, cisco]
aliases: [Komendy IOS, Skrypty konfiguracyjne, Cisco IOS]
created: 2026-10-19
updated: 2026-10-19
---

# Komendy IOS i skrypty konfiguracyjne

> [!abstract] W skrócie
> Komendy w Cisco IOS można pisać w **pełnej** albo **skróconej** formie, a całą konfigurację da się przygotować jako **skrypt** w Notatniku i wkleić do routera. Przy większej topologii oszczędza to mnóstwo czasu.

## Najważniejsze komendy (pełna → skrót)

| Pełna | Skrót | Co robi |
|---|---|---|
| `enable` | `en` | wejście do trybu uprzywilejowanego |
| `configure terminal` | `conf t` | tryb konfiguracji globalnej |
| `interface` | `int` | konfiguracja interfejsu |
| `ip address` | `ip ad` | adres IP interfejsu |
| `no shutdown` | `no sh` | włączenie interfejsu |
| `description` | `desc` | opis interfejsu |
| `hostname` | `h` | nazwa urządzenia |
| `exit` / `end` | `ex` / `end` | wyjście poziom wyżej / do trybu uprzywilejowanego |
| `network` | `net` | sąsiednia sieć w routingu |
| `clock rate` | `cl r` | taktowanie interfejsu DCE |
| `reload` | `rel` | restart |
| `ping` | `p` | test ICMP |

## Skrypty konfiguracyjne

Konfigurację można wpisywać: **pełnymi komendami**, **skróconymi** albo **załadować z pliku skryptu**.

**Zalety**: dużo szybsze (np. routing statyczny na 6 routerach ~20 min ze skryptem vs. znacznie dłużej ręcznie), prosta metoda „kopiuj‑wklej" z Notatnika.
**Wady**: autor musi znać tryby i poziomy konfiguracji IOS oraz pisać komendy **bez błędów**.

Wklejanie: w oknie routera zakładka **CLI** → przycisk **Paste**, albo zakładka **Config** → Load.

> [!tip] Wskazówka
> Skrypt dla każdego routera trzymaj osobno (np. po nazwie miasta) i zaczynaj od `enable` / `configure terminal`. Komentarze w skrypcie zaczynają się od `!`. Przy pomyłce przygotuj też skrypt kasujący (`no ...`).

## Przydatne polecenia diagnostyczne

`show ip route`, `show ipv6 route`, `show running-config`, `show ntp status`, `show ip interface brief`, `ping`, `tracert` (na PC).

## Powiązane

- [[Zagrożenia sieci teleinformatycznych]] – strona główna
- [[IPv6 – adresowanie, trasy i migracja]] – skrypty dla topologii IPv6
- Materiały: [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Network Engineer-Shortened IOS Commands.pdf|Shortened IOS Commands]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Network Engineer-configuration-scripts.pptx|configuration-scripts]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/ipv6-rozdzial6-skrypty-konfiguracyjne.pptx|IPv6 – skrypty konfiguracyjne]]
