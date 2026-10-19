---
tags: [studia, zagrozenia-sieci, vpn]
aliases: [VPN, IPsec, IKE, ISAKMP, Site-to-site]
created: 2026-10-19
updated: 2026-10-19
---

# VPN i IPsec

> [!abstract] W skrócie
> **VPN** przesyła ruch **zaszyfrowanym tunelem** przez sieć publiczną (Internet), tak jakby dwa odległe punkty były połączone bezpośrednio. Dwa główne rodzaje: **remote access** (pojedynczy użytkownik) i **site-to-site** (cała sieć oddziału).

## Rodzaje VPN

| Rodzaj | Kto się łączy | Jak |
|---|---|---|
| **Remote Access** | telepracownik, kontrahent | klient VPN na komputerze (grupa + klucz + login) lub aplikacja web |
| **Site-to-site** | oddział ↔ centrala | bramy VPN po obu stronach (router, firewall, koncentrator) |

Po co tunel: dostęp do hostów za firewallem/NAT (jeden koniec musi mieć adres publiczny), **szyfrowanie**, czasem kompresja na wolnych łączach.

## IPsec – trzy składniki

- **IKE** (Internet Key Exchange) – uzgadnianie kluczy i parametrów.
- **ESP** (Encapsulating Security Payload) – szyfrowanie i uwierzytelnianie danych.
- **AH** (Authentication Header) – samo uwierzytelnianie (bez szyfrowania).

## Konfiguracja site-to-site na routerze Cisco (schemat)

**Faza 1 (ISAKMP)** – jak router z routerem się dogadują:

```
crypto isakmp policy 10
 encr aes 256
 authentication pre-share
 group 5
crypto isakmp key <klucz> address <IP drugiego końca>
```

**Faza 2 (IPsec)** – jak szyfrowany jest ruch:

```
crypto ipsec transform-set VPN-SET esp-aes esp-sha-hmac
crypto map VPN-MAP 10 ipsec-isakmp
 set peer <IP drugiego końca>
 set transform-set VPN-SET
 match address <ACL>
interface <wyjściowy>
 crypto map VPN-MAP
```

- **ACL** w `match address` wskazuje, jaki ruch ma iść tunelem („interesujący ruch").
- Wymagana licencja pakietu `securityk9`.
- Oba końce muszą mieć **identyczne** parametry (policy, klucz, transform-set).

## Remote Access VPN – co jest potrzebne

Router VPN z AAA (`aaa authentication login … group radius local`), polityką ISAKMP, grupą klienta (nazwa + klucz), **pulą adresów** dla klientów, dynamiczną mapą kryptograficzną, serwer RADIUS/AAA. Klient po połączeniu dostaje adres z puli.

## Co pokazują ćwiczenia

- **Bez VPN**: sniffer widzi FTP w jawnym tekście (login i hasło).
- **Z VPN**: ruch jest zaszyfrowany, sniffer nic użytecznego nie wyczyta.
- Ćwiczenia: tunel IPsec w sieci WAN (Oregon ↔ NY), tunnel mode (Metropolis ↔ Gotham), transport mode (klient VPN).

> [!tip] Różnica tunnel vs transport
> **Tunnel mode** – szyfrowany cały oryginalny pakiet, dodawany nowy nagłówek IP (typowe site-to-site). **Transport mode** – szyfrowana tylko zawartość, nagłówek zostaje (host–host).

## Powiązane

- [[Zagrożenia sieci teleinformatycznych]] – strona główna
- [[ACL – listy kontroli dostępu]] – ACL wskazuje ruch do szyfrowania
- [[Zabezpieczanie routerów – SSH, AAA, NTP, Syslog]] – AAA/RADIUS
- [[Szyfrowanie i integralność danych]] – podstawy kryptografii
- Materiały: [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/VPN-teoria.pdf|VPN-teoria]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/VPN.pdf|VPN – ćwiczenie 8]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Configuring VPN Tunnel Mode.pdf|Tunnel Mode]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Configuring VPN Transport Mode.pdf|Transport Mode]]
