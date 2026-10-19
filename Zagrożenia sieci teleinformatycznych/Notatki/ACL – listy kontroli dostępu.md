---
tags: [studia, zagrozenia-sieci, acl]
aliases: [ACL, Access Control List, Listy kontroli dostępu]
created: 2026-10-19
updated: 2026-10-19
---

# ACL – listy kontroli dostępu

> [!abstract] W skrócie
> ACL to lista reguł **permit/deny** na routerze, która filtruje ruch według adresów, protokołów i portów. Działa **dopiero po przypisaniu do interfejsu** i kierunku (`in` / `out`). Reguły czytane są **od góry**, pierwsze pasujące wygrywa, a na końcu jest **niewidoczny `deny`**.

## Rodzaje

| Typ | Numery | Filtruje po |
|---|---|---|
| **Standardowa** | 1–99, 1300–1999 | tylko **adres źródłowy** |
| **Rozszerzona** | 100–199, 2000–2699 | źródło, cel, protokół (TCP/UDP/ICMP/IP), port |
| **Nazwana** | nazwa zamiast numeru | standardowa lub rozszerzona |

## Składnia

```
access-list <nr> {permit|deny} <źródło> <wildcard>          # standardowa
access-list <nr> {permit|deny} <protokół> <źródło> <cel> [eq <port>]   # rozszerzona
ip access-list {standard|extended} NAZWA                      # nazwana (wchodzi w tryb nacl)
ip access-group <nr|NAZWA> {in|out}                           # przypisanie do interfejsu
no access-list <nr>                                           # usunięcie
```

- **Wildcard** to odwrotność maski: dla `/24` jest `0.0.0.255`.
- Na interfejsie może być po jednej ACL na kierunek (wejściowa i wyjściowa).
- Domyślny koniec listy: standardowa `deny any`, rozszerzona `deny ip any any`.

## Zasady

1. **Kolejność reguł ma kluczowe znaczenie** – szczegółowe wyjątki na górę, ogólne na dół.
2. Bez ACL router przepuszcza wszystko.
3. **Gdzie umieścić:** standardowa **blisko celu**, rozszerzona **blisko źródła**.
4. `in` = ruch wchodzący do routera (sprawdzany przed tablicą routingu), `out` = wychodzący (już po routingu).

## Planowanie ACL – 4 kroki

1. Określ wymagania filtrowania.
2. Wybierz typ ACL (standardowa prostsza, rozszerzona dokładniejsza).
3. Wybierz router i interfejs.
4. Wybierz kierunek (myśl z perspektywy routera).

> [!example] Przykład z zajęć
> Blokada nieszyfrowanego HTTP na wyjściu z sieci:
> ```
> access-list 101 deny tcp any any eq 80
> access-list 101 permit ip any any
> interface gig0/0
>  ip access-group 101 in
> ```
> Bez ostatniej linii `permit ip any any` zablokowałby się cały ruch (niejawny deny).

## ACL w IPv6

Inaczej: tylko rozszerzone nazwane, `ipv6 traffic-filter`, szczegóły w [[IPv6 – adresowanie, trasy i migracja]].

## Ćwiczenia Moduł 2 (Packet Tracer)

Named standard ACL · Extended ACL (scenariusz 1 i 2) · ACL przeciw atakom · IPv6 ACL.

## Powiązane

- [[Zagrożenia sieci teleinformatycznych]] – strona główna
- [[Adresacja IPv4, CIDR i NAT]] – maski i wildcard
- [[Redundancja, odporność IOS i firewalle]] – ACL jako zapora
- [[VPN i IPsec]] – ACL wyznacza ruch objęty tunelem
- Materiały: [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/MODUŁ2_ACL.pptx|MODUŁ2_ACL]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Konfigurowanie ACL.pdf|Konfigurowanie ACL (PDF)]]
