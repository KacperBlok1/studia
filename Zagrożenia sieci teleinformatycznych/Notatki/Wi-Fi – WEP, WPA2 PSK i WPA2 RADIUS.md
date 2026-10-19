---
tags: [studia, zagrozenia-sieci, wifi]
aliases: [WEP, WPA2, Wi-Fi security, WPA2 Enterprise]
created: 2026-10-19
updated: 2026-10-19
---

# Wi‑Fi – WEP, WPA2 PSK i WPA2 RADIUS

> [!abstract] W skrócie
> Trzy sposoby zabezpieczenia sieci bezprzewodowej, od najsłabszego do najlepszego: **WEP** (przestarzały, nie używać) → **WPA2 Personal (PSK)** (jedno wspólne hasło) → **WPA2 Enterprise (RADIUS)** (osobne konto każdego użytkownika).

| Metoda | Jak działa | Ocena |
|---|---|---|
| **WEP** | stały klucz (np. 40/64 bity), łatwy do złamania | niebezpieczny, **nie zalecany** |
| **WPA2‑PSK** (Personal) | wspólne hasło (passphrase) + szyfrowanie **AES** | dobre dla domu i małych oddziałów |
| **WPA2‑Enterprise** | uwierzytelnianie każdego użytkownika na serwerze **RADIUS**, AES | najlepsze dla firm |

## Dlaczego RADIUS lepszy w dużej firmie

- Każdy ma **własny login**, więc można odebrać dostęp jednej osobie bez zmiany hasła dla wszystkich.
- Wspólne hasło PSK trzeba zmieniać u wszystkich, gdy ktoś odejdzie albo hasło wycieknie.
- Centralna kontrola i logi (kto, kiedy się łączył).

## Co się konfiguruje w ćwiczeniu (Packet Tracer)

1. Router bezprzewodowy: SSID (nazwa sieci), rozgłaszanie SSID, kanał (np. 6 – 2,437 GHz).
2. Zakładka **Wireless → Wireless Security**: tryb WEP / WPA2 Personal / WPA2‑Enterprise, szyfrowanie AES.
3. Dla Enterprise: adres serwera RADIUS + wspólny sekret, a na serwerze AAA dodajesz klienta (router) i użytkowników.
4. Klienci łączą się przez *PC Wireless* → Connect.

> [!tip] Zapamiętaj
> WEP – nie. PSK – wspólne hasło. RADIUS – konto na osobę. Szyfrowanie: **AES**.

## Powiązane

- [[Zagrożenia sieci teleinformatycznych]] – strona główna
- [[Zabezpieczanie routerów – SSH, AAA, NTP, Syslog]] – RADIUS i AAA
- Materiały: [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/WEP WPA2 PSK WPA2 RADIUS.pdf|WEP WPA2 PSK WPA2 RADIUS (PDF)]]
