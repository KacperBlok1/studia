---
tags: [studia, zagrozenia-sieci, redundancja]
aliases: [Redundancja, Failover, Hardening IOS, Firewall]
created: 2026-10-19
updated: 2026-10-19
---

# Redundancja, odporność IOS i firewalle

> [!abstract] W skrócie
> Trzy tematy o **dostępności i twardnieniu** urządzeń: zapasowe routery/przełączniki (failover), zabezpieczenie konfiguracji IOS i filtrowanie ruchu zaporą/ACL.

## Redundancja (failover)

- **Redundantne routery**: dwa routery dzielą jedną **wirtualną bramę domyślną** (np. 10.44.1.1, a fizycznie R1 `.2` i R2 `.3`). Gdy aktywny router padnie, brama przechodzi na drugi i użytkownicy tego nie zauważają.
- **Redundantne przełączniki**: kilka ścieżek w sieci; po awarii jednej ruch idzie drugą.
- Test w ćwiczeniu: `tracert` do serwera, wyłączenie routera (`shutdown`), `tracert` ponownie – zmienia się pierwszy skok (adres, przez który idzie ruch).

## Hartowanie IOS (resilience)

- **Banner** z ostrzeżeniem prawnym (nieautoryzowany dostęp zabroniony, działania są logowane).
- `service password-encryption` – szyfruje hasła jawne w konfiguracji.
- `security passwords min-length 10` – min. długość nowych haseł.
- **Odporna konfiguracja IOS**: `secure boot-image` (obraz IOS ukryty i chroniony przed usunięciem) oraz `secure boot-config` (kopia konfiguracji).
- Dostęp tylko przez SSH – patrz [[Zabezpieczanie routerów – SSH, AAA, NTP, Syslog]].

## Firewalle i ACL

- Różnica między **HTTP** (jawny) i **HTTPS** (szyfrowany): przy HTTP login i hasło lecą otwartym tekstem.
- ACL na routerze blokuje HTTP wychodzące (`deny tcp any any eq 80`) – patrz [[ACL – listy kontroli dostępu]].
- Serwery mają **własne zapory** (firewall na serwerze e‑mail) z regułami dla usług.

## Zadanie końcowe (Skills Integrated Challenge)

Łączy wszystko: konfiguracja routera bezprzewodowego, wysyłanie plików FTP, **client-to-site VPN**, zabezpieczenie IOS.

## Powiązane

- [[Zagrożenia sieci teleinformatycznych]] – strona główna
- [[VPN i IPsec]], [[Szyfrowanie i integralność danych]]
- Materiały: [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Router and Switch Redundancy.pdf|Redundancy]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Router and Switch Resilience.pdf|Resilience]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Server Firewalls and Router ACLs.pdf|Firewalls and ACLs]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Skills Integrated Challenge.pdf|Skills Integrated Challenge]]
