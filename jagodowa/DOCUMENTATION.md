# Dokumentacja Systemu Oświetlenia BoneIO – Dom Jednorodzinny "Jagodowa"

## 1. Architektura Systemu

System oparty jest na rozwiązaniu **BoneIO** (ESPHome) i składa się z trzech głównych jednostek komunikujących się po sieci LAN (przewodowej) przy użyciu protokołu **UDP** (wykorzystując mechanizmy ESPHome).

### Topologia Fizyczna
Instalacja wykonana jest w topologii **gwiazdy**. Wszystkie przewody sterujące (od włączników) oraz zasilające obwody oświetleniowe sprowadzone są do punktów centralnych (rozdzielnic).

### Rozmieszczenie Urządzeń
1.  **Rozdzielnica 1:**
    *   **Główny Sterownik:** `boneio-32-l-07-39d104` – Centralna jednostka sterująca.
    *   **Ściemniacz 1 (Strefa Nocna/Praca):** `boneio-dr-8ch-03-7d86e0` – Obsługa strefy nocnej i gabinetu.
2.  **Rozdzielnica 2:**
    *   **Ściemniacz 2 (Strefa Dzienna/Mokra):** `boneio-dr-8ch-03-7c8500` – Obsługa strefy dziennej i łazienki.

---

## 2. Mapowanie Wyjść (Sterowanie Urządzeniami)

### Urządzenie 1: Główny Sterownik (`boneio-32-l-07-39d104`)
*Lokalizacja: Rozdzielnica 1. Odpowiada za oświetlenie główne (230V), gniazda sterowane i wentylację.*

| ID | Nazwa/Funkcja | Pomieszczenie | Typ |
| :--- | :--- | :--- | :--- |
| **O01 A/B** | Wypoczynek (Główne) | Salon | Przekaźnik |
| **O02 A/B** | Jadalnia | Salon | Przekaźnik |
| **O03 A/B** | Kuchnia (Główne) | Salon | Przekaźnik |
| **O04** | Oświetlenie elewacji/podbitki | Zewnątrz | Przekaźnik |
| **GZ01** | Gniazdo Zewn. (Podbitka) | Zewnątrz | Przekaźnik |
| **GZ02** | Gniazdo Zewn. (Zachód) | Zewnątrz | Przekaźnik |
| **GZ03** | Gniazdo Zewn. (Wejście) | Zewnątrz | Przekaźnik |
| **O06** | Sypialnia Lewa (Lampka) | Sypialnia | Przekaźnik |
| **O07** | Sypialnia Prawa (Lampka) | Sypialnia | Przekaźnik |
| **O08** | Sypialnia Główne | Sypialnia | Przekaźnik |
| **O09** | Łazienka Główne | Łazienka | Przekaźnik |
| **W01** | Wentylator | Łazienka | Przekaźnik (Czasowy) |
| **O10** | Gabinet Główne | Gabinet | Przekaźnik |
| **O11** | Ośw. Wejście Elewacja | Zewnątrz | Przekaźnik |
| **O12** | Ośw. Wejście (Ganek) | Zewnątrz | Przekaźnik |

### Urządzenie 2: Ściemniacz LED 1 (`boneio-dr-8ch-03-7d86e0`)
*Lokalizacja: Rozdzielnica 1. Sterowanie taśmami LED 12/24V.*

| ID | Nazwa/Funkcja | Pomieszczenie | Uwagi |
| :--- | :--- | :--- | :--- |
| **L03** | Blenda (Dekoracyjne) | Sypialnia | |
| **L04** | Łóżko (Dekoracyjne) | Sypialnia | |
| **L11** | Półka | Gabinet | Aktualnie nieużywane |
| **L12** | Blenda | Gabinet | |
| **L09 A/B** | Komunikacja A | Przedpokój | |
| **L10 A/B** | Komunikacja B | Przedpokój | |

### Urządzenie 3: Ściemniacz LED 2 (`boneio-dr-8ch-03-7c8500`)
*Lokalizacja: Rozdzielnica 2. Sterowanie taśmami LED 12/24V.*

| ID | Nazwa/Funkcja | Pomieszczenie |
| :--- | :--- | :--- |
| **L01 A/B** | Blenda Prawa/Lewa | Salon |
| **L02** | LED TV | Salon |
| **L05** | Wanna | Łazienka |
| **L06** | Prysznic | Łazienka |
| **L07** | Szafka/Lustro | Łazienka |
| **L08** | WC | Łazienka |

---

## 3. Mapowanie Wejść (Przyciski i Czujniki)

Wszystkie fizyczne wejścia są podłączone do **Głównego Sterownika** (`boneio-32-l-07-39d104`) w Rozdzielnicy 1.

| ID | Lokalizacja Fizyczna | Pomieszczenie | Funkcja / Skrypt |
| :--- | :--- | :--- | :--- |
| **S01_P** | Przy oknie tarasowym (Prawa) | Salon | Sterowanie gniazdami zewn. (Podbitka) |
| **S01_L** | Przy oknie tarasowym (Lewa) | Salon | Sterowanie ośw. elewacji |
| **S02A_P** | Wyspa A (Prawa) | Salon | Sceny oświetlenia Jadalni |
| **S02A_L** | Wyspa A (Lewa) | Salon | Sceny oświetlenia Kuchni |
| **S02B_P** | Wyspa B (Prawa) | Salon | Sceny LED + Shelly (Kuchnia) |
| **S02B_L** | Wyspa B (Lewa) | Salon | Sceny oświetlenia Wypoczynku |
| **S03A_P** | Wejście A (Prawa) | Salon | Sceny oświetlenia Jadalni |
| **S03A_L** | Wejście A (Lewa) | Salon | Sceny oświetlenia Kuchni |
| **S03B_P** | Wejście B (Prawa) | Salon | Sceny LED + Shelly (Kuchnia) |
| **S03B_L** | Wejście B (Lewa) | Salon | Sceny oświetlenia Wypoczynku |
| **S04_P** | Przy oknie tarasowym (Prawa) | Sypialnia | Sterowanie gniazdami zewn. |
| **S04_L** | Przy oknie tarasowym (Lewa) | Sypialnia | Sterowanie ośw. elewacji |
| **S05_P** | Wejście (Prawa) | Sypialnia | LEDy dekoracyjne (L03, L04) |
| **S05_L** | Wejście (Lewa) | Sypialnia | Główne (O08) |
| **S06_PG** | Łóżko Prawe (Prawa Góra) | Sypialnia | Blenda (L03) |
| **S06_PD** | Łóżko Prawe (Prawa Dół) | Sypialnia | Lampka nocna (O06) |
| **S06_LG** | Łóżko Prawe (Lewa Góra) | Sypialnia | Główne (O08) |
| **S06_LD** | Łóżko Prawe (Lewa Dół) | Sypialnia | Lampka nocna (O06) |
| **S07_PG** | Łóżko Lewe (Prawa Góra) | Sypialnia | Blenda (L03) |
| **S07_PD** | Łóżko Lewe (Prawa Dół) | Sypialnia | Lampka nocna (O07) |
| **S07_LG** | Łóżko Lewe (Lewa Góra) | Sypialnia | Główne (O08) |
| **S07_LD** | Łóżko Lewe (Lewa Dół) | Sypialnia | Lampka nocna (O07) |
| **S08_P** | Lustro (Prawa) | Łazienka | LED Główne (L05, L07, L08) |
| **S08_L** | Lustro (Lewa) | Łazienka | LED Prysznic (L06) / Wentylator (LP) |
| **S09_G** | Wejście (Góra) | Łazienka | Sceny LED / Wyłącz wszystko (LP) |
| **S09_D** | Wejście (Dół) | Łazienka | Przedpokój LED (wymuszenie) |
| **S10** | Wejście Sypialnia/Salon | Przedpokój | Przedpokój LED (wymuszenie) |
| **S11_P** | Wejście do domu (Prawa) | Przedpokój | Ganek (O12) |
| **S11_L** | Wejście do domu (Lewa) | Przedpokój | **Wyłącz Wszystko (3s)** / Przedpokój LED |
| **S12_P** | Gabinet (Prawa) | Gabinet | Blenda (L12) |
| **S12_L** | Gabinet (Lewa) | Gabinet | Główne (O10) |
| **CO_1** | Sufit | Przedpokój | Czujnik Obecności 1 (Auto LED) |
| **CO_2** | Sufit | Przedpokój | Czujnik Obecności 2 (Auto LED) |
| **CZ** | Zewnątrz | Elewacja | Czujnik Zmierzchu (Auto Elewacja) |

---

## 4. Logika Sterowania (Scenariusze)

### Legenda Skrótów
*   **SP** - **Krótkie** wciśnięcie (Short Press)
*   **LP** - **Długie** wciśnięcie > 1s (Long Press)
*   **VLP** - **Bardzo Długie** wciśnięcie > 3s (Very Long Press)

### Salon i Kuchnia
*   **VLP (3s):** Wyłącza wszystko w Salonie (Główne O01-O03 + LED L01-L02 + Shelly).
*   **Logika Przełączania (SP):**
    *   System inteligentnie przełącza strefy (Kuchnia vs Jadalnia vs Wypoczynek).
    *   Przycisk przy Wyspie B (S02B_P) lub Wejściu B (S03B_P) steruje taśmami LED (Blenda + TV) oraz sterownikiem Shelly.

### Sypialnia
*   **Wejście (S05_P):** Przełącza taśmy LED dekoracyjne (L03, L04).
*   **Wejście (S05_L):** Przełącza światło główne (O08).
*   **Przy Łóżku:** Podział na sterowanie lampką nocną (własną), światłem głównym i dekoracyjnym.
*   **Funkcja Wyłącz Wszystko w Sypialni (VLP):** Wyłącza wszystkie światła w tym pomieszczeniu.

### Łazienka i Wentylacja
*   **Automatyka Wentylatora:** Wentylator włącza się z opóźnieniem 1 minuty po zapaleniu światła LED i wyłącza 2 minuty po zgaszeniu.
*   **Sterowanie Ręczne:** Długie przytrzymanie (LP) lewego przycisku przy lustrze (S08_L) ręcznie włącza lub wyłącza wentylator.
*   **Sceny:** Górny przycisk wejściowy steruje grupą LED (Wanna, Lustro, WC). Lewy przycisk przy lustrze steruje niezależnie prysznicem.

### Przedpokój (Komunikacja)
*   **Tryb Auto:** Po wykryciu ruchu przez czujniki obecności (gdy jest ciemno) włącza taśmy LED na **15% jasności** na czas **90 sekund**.
*   **Tryb Ręczny:** Wciśnięcie przycisku (S10, S11, S09_D) włącza taśmy LED na **100% jasności** na 15 minut.

### Gabinet
*   **Główne (O10):** Sterowane przyciskiem w gabinecie (Lewa). Wyłącza się automatycznie przy dłuższym przytrzymaniu dowolnego przycisku w tym pokoju (LP/VLP).
*   **Blenda (L12):** Dekoracyjne oświetlenie LED, przełączane prawym przyciskiem w gabinecie.
*   **Półka (L11):** Wyjście fizycznie dostępne, ale aktualnie nieużywane w logice systemu.

### Zewnątrz (Elewacja i Ogród)
*   **Zmierzch (CZ):** W godzinach 12:00-22:00, jeśli czujnik wykryje zmrok, włącza się oświetlenie elewacji.
*   **Gniazda:** Sterowane przyciskami przy oknach tarasowych (zbiorczo).

### Funkcja Centralnego Wyłączenia (Wyjście z domu)
*   **Wyzwalacz:** Przycisk przy wyjściu (S11_L) przytrzymany przez **3 sekundy**.
*   **Działanie:** Wyłącza oświetlenie w całym domu (Salon, Sypialnie, Łazienki, sterowniki Shelly).

---

## 5. Uwagi Serwisowe

1.  **Synchronizacja Zegara:** Główny sterownik używa modułu RTC `ds1307` (zegar czasu rzeczywistego). Logika zewnętrzna zależy od poprawności tego zegara.
2.  **Alarm Temperatury:** W szafie sterowniczej ustawiony jest próg alarmowy **70°C**. Przekroczenie uruchamia brzęczyk (buzzer).
3.  **Klucze Szyfrowania:** Komunikacja UDP jest szyfrowana kluczami `JAG_BONEIOx_KEY` zdefiniowanymi w plikach konfiguracyjnych.
4.  **Integracja Shelly:** System BoneIO komunikuje się z urządzeniami Shelly w kuchni jednostronnie (wysyła komendy sterujące) poprzez sieć bezprzewodową **Wi-Fi** (wymagany stabilny zasięg w kuchni).

---

## 6. Zasoby Techniczne i Linki

*   **Repozytorium Projektu (Kody źródłowe YAML):** https://github.com/klimas7/boneio_project/tree/jag
*   **Strona Producenta BoneIO:** https://boneio.eu/
*   **Dokumentacja ESPHome:** https://esphome.io/

---

## 7. Szczegóły Techniczne i Struktura Kodu

Projekt wykorzystuje modułową strukturę plików YAML, charakterystyczną dla zaawansowanych projektów ESPHome.

### Struktura Modułowa (YAML)
Zamiast jednego dużego pliku konfiguracyjnego, projekt dzieli się na mniejsze, logiczne części:
*   **Pakiety (`packages`):** Wykorzystywane do importowania gotowych definicji sprzętowych (np. mapowanie pinów dla konkretnej płytki BoneIO) bezpośrednio z zewnętrznych repozytoriów GitHub (`boneIO-eu/esphome`). Dzięki temu główny plik `boneIO_*.yaml` zawiera tylko logikę biznesową, a nie definicje niskopoziomowe.
*   **Szablony Lokalne:** Pliki takie jak `on-multi-click.yaml` działają jak funkcje w programowaniu. Pozwalają na zdefiniowanie logiki obsługi przycisku (rozróżnianie krótkiego, długiego i bardzo długiego wciśnięcia) w jednym miejscu i wielokrotne jej użycie dla każdego wejścia. Zapewnia to spójne zachowanie wszystkich przycisków w domu.

### Logika Biznesowa (Scripting)
Logika sterowania oświetleniem nie jest "zaszyta" w definicjach przycisków, lecz wydzielona do sekcji `script`.
*   **Centralizacja:** Każde pomieszczenie (np. `id: salon`, `id: sypialnia`) posiada własny skrypt sterujący.
*   **Parametryzacja:** Skrypty przyjmują parametry: nazwę przełącznika (`sn`) oraz typ wciśnięcia (`pt`).
*   **Język C++ (Lambdas):** Wewnątrz skryptów wykorzystywane są bloki `lambda`, pozwalające na użycie pełnej mocy języka C++ do obsługi skomplikowanych warunków (np. sprawdzanie stanów wielu lamp naraz, tablice stanów, pętle), co byłoby niemożliwe w czystym YAML.

### Komunikacja Między Urządzeniami
*   **Wewnętrzna (BoneIO):** Urządzenia wymieniają się informacjami (np. naciśnięcie przycisku na Głównym Sterowniku -> włączenie LED na Ściemniaczu) przy użyciu komponentu `packet_transport` opartego na protokole **UDP**. Zapewnia to minimalne opóźnienia, kluczowe dla komfortu użytkowania (brak zauważalnego "laga" po wciśnięciu przycisku).
*   **Zewnętrzna (Shelly):** Integracja z urządzeniami Shelly odbywa się poprzez standardowe żądania HTTP (REST API). BoneIO wysyła zapytania `http_request` do urządzeń Shelly, aby zmienić ich stan lub odczytać status. Logika ta jest wydzielona w plikach `shelly.yaml` oraz `shelly_common.yaml`.

---

## 8. Diagnostyka i Dostęp do Logów (Dla Instalatora)

Każde urządzenie w systemie BoneIO posiada wbudowany serwer WWW (Web Server), który umożliwia podgląd stanu, sterowanie oraz odczyt logów systemowych w czasie rzeczywistym.

### Adresy IP Urządzeń
Poniższe adresy IP są kluczowe dla celów diagnostycznych:

| Urządzenie | Adres IP | Rola |
| :--- | :--- | :--- |
| **Główny Sterownik (Master)** | `192.168.0.104` | Logika przycisków, scenariusze, 230V |
| **Ściemniacz 1 (Nocna/Praca)** | `192.168.0.103` | LED Sypialnia, Gabinet, Przedpokój |
| **Ściemniacz 2 (Dzienna/Mokra)**| `192.168.0.100` | LED Salon, Łazienka |

### Jak uzyskać dostęp do logów?
1.  Upewnij się, że komputer/telefon jest podłączony do tej samej sieci lokalnej co sterowniki.
2.  Otwórz przeglądarkę internetową.
3.  Wpisz adres IP urządzenia, które chcesz zdiagnozować (np. `http://192.168.0.104`).
4.  Na stronie głównej zobaczysz listę wszystkich encji (przełączników, czujników).
5.  Po prawej stronie ekranu (lub na dole w widoku mobilnym) znajduje się sekcja **Logs**. Kliknij przycisk, aby rozwinąć konsolę logów.

### Interpretacja Logów
*   Logi pokazują zdarzenia w czasie rzeczywistym (np. `[I][main:123]: Button pressed`).
*   Szukaj komunikatów o poziomie `WARNING` (żółte) lub `ERROR` (czerwone) w przypadku problemów.
*   Logi zawierają informacje debugowania zdefiniowane w skryptach (np. `ESP_LOGI("salon", "S02A_P SP")`), co pozwala śledzić, czy system poprawnie rozpoznaje wciśnięcia przycisków i które scenariusze są uruchamiane.
