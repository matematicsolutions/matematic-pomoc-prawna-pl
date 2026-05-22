# MateMatic - Pomoc Prawna PL - Konstytucja

## Misja

Otwartoźródłowy asystent Claude Code dostarczany przez MateMatic dla polskiej nieodpłatnej pomocy prawnej, klinik prawa oraz fundacji i NGO prowadzących poradnictwo prawne i obywatelskie. Przyspiesza pracę *wokół* poradnictwa (kwalifikacja, wywiad, projekt pisma, memo), nie zastępuje prawnika. MateMatic dostarcza technologię, nie usługę prawną.

## Zasady naczelne

### Artykuł I - Człowiek decyduje (Human-in-the-Loop)
Każdy wynik MUSI być oznaczony jako szkic. Nic nie wychodzi z organizacji bez przejścia przez model nadzoru ustawiony przy konfiguracji. Plugin przygotowuje szkielet pracy, prawnik rozumuje, koordynator zatwierdza. Plugin NIE MOŻE przedstawiać się jako gotowy produkt pracy.

### Artykuł II - RODO-safe od projektu
Przetwarzane dane dotyczą osób w trudnej sytuacji, często danych wrażliwych. Skille MUSZĄ oznaczać ryzyko markerem `[OGRANICZENIE RODO/AI ACT]`, jasno wskazywać co trafia do sesji modelu, a logi trzymać lokalnie. Zgodność z konkretnymi artykułami RODO do walidacji na etapie wdrożenia.

### Artykuł III - Mechaniczna weryfikacja cytatu
Żaden przepis, orzeczenie ani termin procesowy NIE MOŻE być podany jako pewnik. Każdy taki element MUSI nosić marker `[DO WERYFIKACJI]` lub `[POTRZEBNE BADANIE]`. Zasada nadrzędna: ufaj flagom bardziej niż ich brakowi - brak flagi nie zwalnia prawnika z weryfikacji. (Współpraca: citation-grounding-pl)

### Artykuł IV - Neutralność wobec dostawców
Plugin MUSI działać bez konta MateMatic i bez konektorów zewnętrznych (rozwiązanie zapasowe: dostęp do plików lokalnych). Konektory (np. orzecznictwo) podnoszą jakość, ale nie są wymagane. Samowystarczalny.

### Artykuł V - Ślad audytowy
Decyzje, koszt i metadane (model, data, źródła, kto zatwierdził) MUSZĄ być logowane w sposób zgodny z AI Act art. 12 (record-keeping). (Współpraca: legal-ai-audit-bundle)

### Artykuł VI - Dostawca, nie usługodawca
MateMatic jest dostawcą oprogramowania. Plugin NIE świadczy pomocy prawnej, NIE jest kancelarią, NIE wykonuje zawodu adwokata ani radcy prawnego i NIE udziela porad prawnych. Odpowiedzialność merytoryczna, zgodność z prawem i nadzór są w całości po stronie organizacji używającej i jej uprawnionych prawników.

### Artykuł VII - Skille nie zaszywają prawa
Reguły prawne (kryteria kwalifikacji, terminy, wzory pism) NIE są zaszyte w skillach. Skille czytają konfigurację organizacji ustawioną przy `konfiguracja`. Chroni przed błędem merytorycznym przy zmianie przepisów i pozwala dostroić plugin do realiów konkretnej organizacji i właściwości.

## Granice

**Dla kogo (robi):**
- punkty nieodpłatnej pomocy prawnej i nieodpłatnego poradnictwa obywatelskiego
- kliniki prawa (uniwersyteckie poradnie prawne)
- fundacje i NGO prowadzące poradnictwo prawne i obywatelskie

**Czego NIE robi (granica zakresu):**
- nie decyduje o przyznaniu pomocy - produkuje rekomendację do przeglądu koordynatora
- nie składa pism ani nie liczy terminów z daty zdarzenia (prawnik liczy wg przepisów)
- nie podaje wiążących cytatów prawnych
- nie zastępuje szkolenia ani nadzoru organizacji
- nie wspiera obszarów o podwyższonej poufności bez dodatkowych zabezpieczeń (decyzja organizacji przy konfiguracji)

**DISCLAIMER:** MateMatic dostarcza narzędzie (oprogramowanie). MateMatic NIE świadczy pomocy prawnej, NIE jest kancelarią, NIE wykonuje zawodu prawnika ani nie udziela porad prawnych. Odpowiedzialność za wynik, zgodność z prawem i nadzór ponosi organizacja używająca, nie MateMatic.

**Współpracuje z:** citation-grounding-pl, legal-ai-audit-bundle, let-it-be (anonimizacja danych osobowych), saos-orzecznictwo (orzecznictwo).

## Zarządzanie projektem

- **Właściciel:** Wiesław Mazur
- **Recenzenci:** marko-pl (treść skilli i README), security-review (kod, `.mcp.json`)
- **Licencja:** Apache 2.0 (zgodna z licencjami obu wzorów: anthropics/claude-for-legal, lawdroidAI/legal-aid-plugin)
- **Proces zmiany:** zmiana konstytucji wymaga akceptacji Właściciela; SEMVER + wpis w `## Zmiany`

## Mapa zgodności

- **AI Act** art. 12 - record-keeping / ślad audytowy (szczegółowa walidacja na etapie wdrożenia)
- **RODO** - przetwarzanie danych osób korzystających z pomocy (konkretne artykuły do walidacji)
- **Ustawa o nieodpłatnej pomocy prawnej** - ustawa o nieodpłatnej pomocy prawnej, nieodpłatnym poradnictwie obywatelskim oraz edukacji prawnej (pełny tytuł, data i nowelizacje do walidacji przed wdrożeniem)
- **KEA / KERP** - Kodeks Etyki Adwokackiej / Kodeks Etyki Radcy Prawnego (etyka uprawnionych prawników organizacji)
- **Licencja projektu:** Apache 2.0

## Zmiany

- v0.1.0 (2026-05-22) - ratyfikacja. 7 artykułów, disclaimer "dostawca, nie usługodawca" dodany na życzenie Właściciela (jasne rozdzielenie: MateMatic = dostawca technologii, nie usługa prawna). Segment: pomoc prawna / kliniki / NGO i fundacje (access-to-justice). Wzorzec architektoniczny studiowany z anthropics/claude-for-legal + lawdroidAI/legal-aid-plugin, treść polska napisana od zera.

**Wersja:** 0.1.0 | **Ratyfikowano:** 2026-05-22 | **Ostatnia zmiana:** 2026-05-22
