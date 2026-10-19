---
tags: [studia, zagrozenia-sieci, aaa]
aliases: [AAA, RADIUS, TACACS+, SSH, NTP, Syslog, OSPF authentication]
created: 2026-10-19
updated: 2026-10-19
---

# Zabezpieczanie routerów – SSH, AAA, NTP, Syslog, OSPF

> [!abstract] W skrócie
> Moduł 1: jak zabezpieczyć **dostęp administracyjny** do urządzeń Cisco i ich komunikację. Zamiast jednego hasła `enable` – konta, uwierzytelnianie lokalne lub przez serwer (RADIUS / TACACS+), szyfrowany dostęp przez SSH, zsynchronizowany czas i logi.

## SSH zamiast Telnetu

Telnet wysyła wszystko jawnie, SSH szyfruje. Kroki na routerze:

1. nazwa hosta i **domena** (`ip domain-name …`),
2. użytkownik z hasłem **`secret`** (szyfrowanym),
3. klucze RSA (`crypto key generate rsa`, np. 1024 lub 2048 bitów),
4. linie VTY: `transport input ssh`, `login local`,
5. dodatkowo: `ip ssh version 2`, limit czasu i prób, `login block-for … attempts …` (blokada po nieudanych logowaniach).

Test: `ssh -l <użytkownik> <IP>` z innego komputera.

## NTP – wspólny czas

`ntp server <IP>` na routerze, potem `show ntp status` (ma być „synchronized") i `show ntp associations`. Czas musi się zgadzać, żeby logi z różnych urządzeń dało się porównać.

## Syslog – zdalne logi

`logging <IP serwera syslog>` oraz `service timestamps log datetime msec` (znaczniki czasu w logach). Urządzenia wysyłają zdarzenia na jeden serwer.

## Lokalne AAA (Authentication, Authorization, Accounting)

```
username <nazwa> secret <hasło>
aaa new-model
aaa authentication login default local
line console 0
 login authentication default
```

Dzięki temu konsola i VTY wymagają **loginu i hasła z lokalnej bazy**. Dodatkowo `banner` z ostrzeżeniem o dostępie tylko dla upoważnionych.

## AAA przez serwer: RADIUS i TACACS+

```
aaa authentication login default group tacacs+ local     # lub: group radius local
tacacs-server host <IP>   +   tacacs-server key <klucz>
radius-server host <IP>   +   radius-server key <klucz>
```

- Na końcu zostaje **`local`** jako zapasowa metoda, gdy serwer nie odpowiada.
- **TACACS+** (Cisco) – szyfruje całość, rozdziela uwierzytelnianie i autoryzację. **RADIUS** – szyfruje tylko hasło, łączy uwierzytelnianie z autoryzacją, używany też w Wi‑Fi i VPN.

## Uwierzytelnianie OSPF

W obszarze: `area 0 authentication message-digest`, na interfejsie `ip ospf message-digest-key 1 md5 <klucz>`. Sąsiedzi muszą mieć ten sam klucz, inaczej nie nawiążą relacji – chroni przed podstawieniem fałszywego routera.

> [!warning] Nie wpisuj haseł z ćwiczeń do prawdziwych urządzeń
> Hasła w materiałach to dane testowe do Packet Tracera. W realnej sieci używaj silnych, unikalnych haseł.

## Powiązane

- [[Zagrożenia sieci teleinformatycznych]] – strona główna
- [[Redundancja, odporność IOS i firewalle]] – dalsze hartowanie IOS
- [[VPN i IPsec]] – AAA/RADIUS dla zdalnego dostępu
- [[Wi-Fi – WEP, WPA2 PSK i WPA2 RADIUS]] – RADIUS w sieci bezprzewodowej
- Materiały: [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/MODUŁ1_2MERITO-Configure OSPF Authentication.pptx|OSPF auth]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/MODUŁ1_3MERITO-Configure and Verify NTP.pptx|NTP]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/MODUŁ1_4MERITO-Configure Cisco Devices for Syslog, NTP, and SSH Operations.pptx|Syslog+NTP+SSH]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/MODUŁ1_5MERITO-Configure Local AAA for Console and VTY Access.pptx|lokalne AAA]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/MODUŁ1_6MERITO-Configure Server-based Authentication with TACACS+ and RADIUS.pptx|TACACS+/RADIUS]]
