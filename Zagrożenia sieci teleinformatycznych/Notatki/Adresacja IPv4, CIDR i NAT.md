---
tags: [studia, zagrozenia-sieci, ipv4]
aliases: [IPv4, CIDR, Maska podsieci, NAT, Subnetting]
created: 2026-10-19
updated: 2026-10-19
---

# Adresacja IPv4, CIDR i NAT

> [!abstract] W skrócie
> Adres IPv4 to **32 bity** = 4 oktety (0–255). Składa się z części **sieci** i części **hosta**, a granicę wyznacza **maska** (np. `/24` = 255.255.255.0). Dwa adresy w każdej podsieci są zarezerwowane: **adres sieci** (pierwszy) i **broadcast** (ostatni).

## Rodzaje adresów w sieci

| Adres | Przykład | Do czego |
|---|---|---|
| MAC | `00-1A-2B-3C-4D-5E` | identyfikacja urządzenia w sieci lokalnej |
| IPv4 / IPv6 | `192.168.1.10` | identyfikacja hosta i sieci, routing |
| Port TCP/UDP | 80, 443, 25 | identyfikacja aplikacji |

## Zapis binarny

Wartości bitów w oktecie: `128 64 32 16 8 4 2 1`. Np. `192 = 128 + 64 = 11000000`. Adres `192.168.1.10` = `11000000.10101000.00000001.00001010`.

## Klasy (historyczne)

| Klasa | Pierwszy oktet | Domyślnie sieć/host | Uwagi |
|---|---|---|---|
| A | 1–126 | 8/24 bity | duże sieci |
| B | 128–191 | 16/16 | średnie |
| C | 192–223 | 24/8 | małe sieci LAN |
| D | 224–239 | – | multicast |
| E | 240–255 | – | eksperymentalne |

Dziś używa się adresacji **bezklasowej (CIDR)**, np. `10.10.0.0/16`.

## Adresy prywatne i publiczne

Prywatne (tylko w LAN, nie są routowane w Internecie): `10.0.0.0/8`, `172.16.0.0 – 172.31.255.255` (`/12`), `192.168.0.0/16`. Reszta (poza specjalnymi) to adresy publiczne.

## Podsieci – 5 kroków (zawsze tak samo)

1. `/n` → bity hosta = **32 − n**.
2. Liczba adresów = **2^(32−n)**.
3. Krok bloku = **256 − wartość maski** w „częściowym" oktecie.
4. Znajdź blok, do którego należy adres.
5. Pierwszy adres = sieć, ostatni = broadcast, środek = hosty (liczba hostów = adresy − 2).

| Prefiks | Maska | Adresów | Hostów |
|---|---|---|---|
| /30 | 255.255.255.252 | 4 | 2 |
| /29 | …248 | 8 | 6 |
| /28 | …240 | 16 | 14 |
| /27 | …224 | 32 | 30 |
| /24 | 255.255.255.0 | 256 | 254 |
| /23 | 255.255.254.0 | 512 | 510 |
| /22 | 255.255.252.0 | 1024 | 1022 |
| /21 | 255.255.248.0 | 2048 | 2046 |
| /16 | 255.255.0.0 | 65 536 | 65 534 |

> [!example] Przykład
> `192.168.10.77/27`: 5 bitów hosta → 32 adresy, krok 32 → blok `192.168.10.64`–`.95`; sieć `.64`, hosty `.65–.94`, broadcast `.95`.
>
> `172.16.35.100/23`: krok 2 w 3. oktecie → blok `172.16.34.0`–`172.16.35.255`.

## NAT – jak to działa

Router zamienia prywatny adres źródłowy na swój publiczny, **zapamiętuje to w tablicy NAT** (razem z numerem portu) i przy odpowiedzi tłumaczy z powrotem.

1. PC `192.168.1.10:50000` → Internet.
2. Router wysyła pakiet jako `83.21.150.45:30001` (wpis w tablicy NAT).
3. Serwer odpowiada na `83.21.150.45:30001`.
4. Router sprawdza tablicę i oddaje pakiet do `192.168.1.10`.

Kilka urządzeń naraz = różne **porty publiczne**. Dzięki NAT wiele urządzeń prywatnych używa jednego adresu publicznego.

> [!tip] Jak rozpoznać adres prywatny
> Zaczyna się od `10.`, `172.16`–`172.31` albo `192.168.`.

## Powiązane

- [[Zagrożenia sieci teleinformatycznych]] – strona główna
- [[IPv6 – adresowanie, trasy i migracja]] – następca IPv4
- [[ACL – listy kontroli dostępu]] – filtrowanie po adresach (maski wildcard)
- Materiały: [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Adresacja_IPv4_Prefiksy_Maski_Bity_Hosta.pptx|prezentacja prefiksów]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/IPv4-Rola adresacji w sieciach komputerowych.pdf|IPv4 – rola adresacji (PDF)]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Adresacja_IPv4_Ściąga.pptx|Ściąga (grafiki)]]
