---
tags: [studia, zagrozenia-sieci, ipv6]
aliases: [IPv6, SLAAC, NDP, RIPng, OSPFv3, Dual stack]
created: 2026-10-19
updated: 2026-10-19
---

# IPv6 – adresowanie, trasy, ACL i migracja

> [!abstract] W skrócie
> IPv6 ma adresy **128-bitowe**, nie używa NAT ani ARP (zamiast ARP jest **NDP**), a hosty mogą same ustawić adres (**SLAAC**). Na zajęciach: dynamiczne adresowanie, trasy statyczne, routing dynamiczny, ACL, migracja z IPv4.

## Nagłówek IPv6

Version (4 b, wartość 6) · Traffic class (8 b, QoS) · Flow label (20 b) · Payload length (16 b) · Next header (8 b) · **Hop limit** (8 b, odpowiednik TTL) · Source address (128 b) · Destination address (128 b).

## NDP i ICMPv6

**NDP** zastępuje ARP. Cztery komunikaty:

| Komunikat | Typ | Po co |
|---|---|---|
| Router Solicitation (RS) | 133 | host pyta „są tu routery?" |
| Router Advertisement (RA) | 134 | router odpowiada, podaje prefiks |
| Neighbor Solicitation (NS) | 135 | poznanie adresu MAC sąsiada / sprawdzenie dostępności |
| Neighbor Advertisement (NA) | 136 | odpowiedź na NS |

ICMPv6: pole **Type** – 0–127 raporty błędów, 128–255 wiadomości informacyjne.

> [!info] Drobiazg w materiale
> Slajdy podają dla NA także typ 135, ale poprawnie NA to typ 136.

## Dynamiczna konfiguracja adresu GUA

1. **SLAAC** – host sam tworzy adres: prefiks z RA + 64-bitowy identyfikator interfejsu. Brama = adres LLA routera (źródło RA).
2. **SLAAC + bezstanowy DHCPv6** – adres tworzy host, a DNS i nazwę domeny dostaje z DHCPv6.
3. **Stanowy DHCPv6** – serwer daje adres, prefiks, DNS, domenę.

**EUI-64**: weź MAC → wstaw `FFFE` w środek → zamień 7. bit (od lewej) z 0 na 1.

## Trasy statyczne

Rodzaje: **zwykłe**, **domyślne** (`::/0`), **zapasowe/floating** (wyższa AD). Next hop można podać jako: interfejs wyjściowy, adres GUA następnego przeskoku albo adres LLA. **Loopback** to interfejs wirtualny, zawsze „up", dobry do testów.

## Routing dynamiczny

| Protokół | AD | Cechy |
|---|---|---|
| RIPng | 120 | rozszerzenie RIPv2, max 15 przeskoków, bez własnego uwierzytelniania |
| EIGRPv6 | 90 | algorytm DUAL, wymaga router-id |
| OSPFv3 | 110 | algorytm Dijkstry, uwierzytelnianie przez IPsec |

Wspólna komenda startowa: `ipv6 unicast-routing`.

## ACL w IPv6

- Tylko **rozszerzone, nazwane** ACL.
- Do interfejsu: `ipv6 traffic-filter NAZWA in|out` (nie `ip access-group`).
- Na końcu domyślnie: `permit icmp any any nd-na`, `permit icmp any any nd-ns`, `deny ipv6 any any`.

## Migracja IPv4 → IPv6

- **Dual stack** – urządzenia mają oba stosy jednocześnie (rozwiązanie przejściowe).
- **ISATAP** – automatyczne tunele IPv6 przez sieć IPv4 (`tunnel mode ipv6ip isatap`).
- **6over4** – enkapsulacja IPv6 w IPv4.

## Inne

- **SSH** w routerze też na IPv6 (domena, klucze RSA, `transport input ssh`, `login local`).
- **Router on a stick**: jeden fizyczny interfejs, podinterfejsy `Gig0/0.10`, `.20` z `encapsulation dot1Q`; switch z trunkiem i portami access dla VLAN-ów.
- Skrypty konfiguracyjne: patrz [[Komendy IOS i skrypty konfiguracyjne]].

## Powiązane

- [[Zagrożenia sieci teleinformatycznych]] – strona główna
- [[Adresacja IPv4, CIDR i NAT]] – IPv4, z którego migrujemy
- [[ACL – listy kontroli dostępu]] – ACL dla IPv4
- Materiały: pliki `ipv6-rozdzial3…9` w `Materiały/`, np. [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/ipv6-rozdzial3-dynamiczne-adresowanie.pptx|rozdział 3]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/ipv6-rozdzial5-konfigurowanie-routingu-dynamicznego.pptx|rozdział 5]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/ipv6-rozdzial8-migracja-ipv4-do-ipv6.pptx|rozdział 8]]
