# MateMatic - Pomoc Prawna PL

*Otwartoźródłowy asystent Claude Code dla polskiej nieodpłatnej pomocy prawnej, klinik prawa, fundacji i NGO.*

> [!IMPORTANT]
> **MateMatic dostarcza narzędzie (oprogramowanie). MateMatic NIE świadczy pomocy prawnej, NIE jest kancelarią, NIE wykonuje zawodu adwokata ani radcy prawnego i NIE udziela porad prawnych.**
> Ten plugin przygotowuje szkielet pracy administracyjnej *wokół* poradnictwa. Merytoryczna porada, weryfikacja cytatów i nadzór są w całości po stronie organizacji używającej i jej uprawnionych prawników. Odpowiedzialność za wynik, zgodność z prawem i nadzór ponosi organizacja, nie MateMatic.

## Dla kogo

- punkty **nieodpłatnej pomocy prawnej** i nieodpłatnego poradnictwa obywatelskiego
- **kliniki prawa** (uniwersyteckie poradnie prawne)
- **fundacje i NGO** prowadzące poradnictwo prawne i obywatelskie

## Co robi

Organizacje pomocy prawnej zwykle obsługują więcej zgłoszeń, niż pozwalają zasoby, a część czasu prawnika pochłaniają czynności administracyjne wokół poradnictwa. Ten plugin skraca czas tego, co jest *wokół* porady - kwalifikacji, wywiadu, pierwszego szkicu, ramy analizy - aby ten sam zespół obsłużył więcej osób, a prawnicy mieli więcej czasu na to, co faktycznie wymaga prawnika.

**Przyspiesza część nie-merytoryczną. Zachowuje poradnictwo.** To zasada projektowa.

Każdy wynik to **szkic do analizy i nadzoru** - oznaczony, zalogowany, przepuszczony przez model nadzoru ustawiony przez organizację.

## Skille

| Skill | Do czego | Czego NIE robi |
|---|---|---|
| **konfiguracja** | Jednorazowa konfiguracja początkowa: profil organizacji, obszary, właściwość, kryteria, model nadzoru, warunki wstępne | Nie zastępuje regulaminu/szkolenia organizacji |
| **kwalifikacja** | Wstępna ocena zgłoszenia według kryteriów z konfiguracji - rekomendacja do przeglądu | Nie decyduje o przyznaniu pomocy |
| **wywiad** | Ustrukturyzowane przyjęcie sprawy: fakty, chronologia, dokumenty, wychwytywanie problemów z innych obszarów | Nie udziela porady, nie liczy terminów |
| **projekt-pisma** | Pierwszy szkic typowego pisma, cytaty oznaczone do weryfikacji | Nie składa pisma, nie podaje wiążących cytatów |
| **memo** | Szkielet analizy IRAC - reguły jako luki badawcze, analiza pusta dla prawnika | Nie pisze analizy ani wniosku za prawnika |

## Kręgosłup nadzoru i weryfikacji

Plugin jest zbudowany wokół nadzoru i weryfikacji, nie wokół automatyzacji.

- **Markery pewności** w treści (`[DO WERYFIKACJI]`, `[NIEPEWNE]`, `[POTRZEBNE BADANIE]`, `[ANALIZA PRAWNIKA]`, `[BRAK FAKTU]`, `[OGRANICZENIE RODO/AI ACT]`). Zasada: ufaj flagom bardziej niż ich brakowi.
- **Trzy modele nadzoru** (do wyboru przy konfiguracji): formalna kolejka / konfigurowalne flagi / lżejszy nadzór.
- **Skille nie zaszywają prawa** - czytają konfigurację organizacji, nie reguły wbudowane w kod. Chroni przed błędem przy zmianie przepisów.
- **Ślad audytowy** zgodny z AI Act art. 12 (record-keeping).

## Start

1. Zainstaluj plugin w Claude Code.
2. Koordynator uruchamia `konfiguracja` (raz) - ustawia profil organizacji i model nadzoru, przechodzi przez warunki wstępne (Część 0).
3. Personel używa `kwalifikacja`, `wywiad`, `projekt-pisma`, `memo`.

Plugin działa bez konektorów (dostęp do plików lokalnych). Podłączenie źródeł orzecznictwa podnosi jakość weryfikacji cytatów, ale nie jest wymagane.

## Warunki wstępne (zanim użyjesz z realnymi sprawami)

Potwierdź z koordynatorem i osobą ds. zgodności: poziom konta Claude i politykę retencji/treningu danych, zgodę i informowanie osób o pracy z AI, obsługę danych poufnych i wrażliwych, obszary o podwyższonej poufności (przemoc domowa, cudzoziemcy), anonimizację danych osobowych. Skill `konfiguracja` zapisuje te decyzje jako pierwszy krok.

## Ramy prawne

- **AI Act** art. 12 (record-keeping)
- **RODO** (przetwarzanie danych osób korzystających z pomocy)
- **Ustawa o nieodpłatnej pomocy prawnej** (nieodpłatna pomoc prawna, nieodpłatne poradnictwo obywatelskie, edukacja prawna - pełny tytuł i nowelizacje do walidacji przed wdrożeniem)
- **KEA / KERP** (etyka adwokata / radcy prawnego)

Plugin nie egzekwuje tych reguł - robi to organizacja. Plugin oznacza, gdzie sprawa może ich dotykać.

## Licencja i atrybucja

**Apache License 2.0.** Wzorzec architektoniczny (struktura wtyczki, schemat SKILL.md, konfiguracja CLAUDE.md, system markerów pewności, modele nadzoru) studiowany z [`anthropics/claude-for-legal`](https://github.com/anthropics/claude-for-legal) (Apache-2.0) i [`lawdroidAI/legal-aid-plugin`](https://github.com/lawdroidAI/legal-aid-plugin) (Apache-2.0, LawDroid Ltd.). Cała treść specyficzna dla polskiej pomocy prawnej - mapowanie reguł amerykańskich na polskie ramy, wszystkie skille i ich logika - jest oryginalna i napisana od zera. Szczegóły w pliku [`NOTICE`](./NOTICE).

Wydane otwarcie, aby każdy punkt npp, klinika prawa, fundacja i NGO mogły wdrożyć je za darmo. Zgłoszenia, PR i forki mile widziane.

---

*MateMatic Solutions - bezpieczna architektura AI. Dostawca technologii, nie usług prawnych.*
