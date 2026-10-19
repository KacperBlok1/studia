---
tags: [studia, zagrozenia-sieci, kryptografia]
aliases: [Hash, HMAC, Szyfrowanie plików, Integralność danych]
created: 2026-10-19
updated: 2026-10-19
---

# Szyfrowanie i integralność danych

> [!abstract] W skrócie
> **Szyfrowanie** chroni poufność (nikt obcy nie przeczyta). **Hash / HMAC** chroni integralność (można sprawdzić, że plik nie został zmieniony). Ćwiczenia w Packet Tracerze pokazują to na przykładzie przesyłania plików przez FTP.

## Poufność – szyfrowanie

- Dane wysyłane jawnie (FTP, HTTP, Telnet) może przeczytać każdy, kto podsłuchuje ruch (sniffer).
- Zaszyfrowany plik jest bezużyteczny bez hasła/klucza – na ćwiczeniu odszyfrowuje się zawartość w narzędziu online za pomocą hasła.
- Zamiast FTP/HTTP używaj **szyfrowanych odpowiedników**: HTTPS, SSH/SFTP, VPN.

## Integralność – hash i HMAC

- **Hash** (funkcja skrótu, np. MD5, SHA) zamienia plik w krótki „odcisk palca". Zmiana jednego bajta zmienia cały hash.
- Weryfikacja: policz hash pobranego pliku i **porównaj z hashem podanym przez źródło**. Inny hash = plik zmieniony (np. serwer włamany).
- **HMAC** = hash **z kluczem tajnym**. Daje i integralność, i pewność, że skrót mógł wyliczyć tylko ktoś znający klucz (zwykły hash może podmienić atakujący razem z plikiem).

> [!example] Scenariusz z ćwiczenia
> Serwer plików został zhakowany. Pobierasz pliki klienta, liczysz hashe, porównujesz z listą na serwerze kopii zapasowej → jeden plik ma inny hash = zmanipulowany, trafia do analizy. Krytyczne pliki dodatkowo sprawdzasz HMAC-iem.

## Trzy filary (CIA)

| Cel | Czym zapewniamy |
|---|---|
| Poufność | szyfrowanie, VPN, HTTPS |
| Integralność | hash, HMAC |
| Dostępność | redundancja, kopie zapasowe ([[Redundancja, odporność IOS i firewalle]]) |

## Powiązane

- [[Zagrożenia sieci teleinformatycznych]] – strona główna
- [[VPN i IPsec]] – szyfrowanie całego ruchu
- [[Zagrożenia – lista ćwiczeń Packet Tracer]]
- Materiały: [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Exploring File and Data Encryption.pdf|Exploring File and Data Encryption]], [[Studia/Zagrożenia sieci teleinformatycznych/Materiały/Using File and Data Integrity Checks.pdf|Using File and Data Integrity Checks]]
