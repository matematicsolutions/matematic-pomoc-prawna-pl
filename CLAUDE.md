# Pomoc Prawna PL - konfiguracja organizacji

> **DISCLAIMER.** MateMatic dostarcza narzędzie (oprogramowanie). MateMatic NIE świadczy pomocy prawnej, NIE jest kancelarią, NIE wykonuje zawodu adwokata ani radcy prawnego i NIE udziela porad prawnych. Ten plugin przygotowuje szkielet pracy administracyjnej wokół poradnictwa. Merytoryczna porada, weryfikacja cytatów i nadzór są w całości po stronie organizacji używającej i jej uprawnionych prawników. Odpowiedzialność za wynik, zgodność z prawem i nadzór ponosi organizacja, nie MateMatic.

Ten plik trzyma konfigurację organizacji. Wypełnia go skill `konfiguracja` (uruchamiany raz na początku). Skille czytają ten plik zamiast zaszywać reguły prawne (Artykuł VII konstytucji), dzięki czemu plugin działa według realiów organizacji i aktualnych przepisów.

---

## Część 0 - Warunki wstępne: etyka i poufność (wypełnij PRZED użyciem z realnymi sprawami)

- [ ] **Poziom konta Claude i polityka retencji/treningu danych** - potwierdź, co obowiązuje organizację i czy spełnia wymogi RODO oraz wewnętrzne zasady poufności.
- [ ] **Zgoda i informowanie klienta o pracy wspomaganej AI** - ustal, czy i jak organizacja informuje osoby korzystające z pomocy; udokumentuj.
- [ ] **Obsługa danych poufnych i wrażliwych** - co trafia do sesji, gdzie przechowywane są wyniki, kto ma dostęp, jak długo, jak rotacja personelu wpływa na dostęp.
- [ ] **Obszary o podwyższonej poufności** (np. przemoc domowa, sprawy cudzoziemców, niektóre sprawy rodzinne) - zdecyduj, czy plugin jest w ogóle odpowiedni dla tych spraw.
- [ ] **Anonimizacja danych osobowych** - rekomendacja: pseudonimizacja danych przed wklejeniem do sesji (zob. skill let-it-be).

Nie pomijaj tej części. Skill `konfiguracja` zapisuje te decyzje jako pierwszy krok.

---

## Część 1 - Profil organizacji (wypełnia `konfiguracja`)

- **Typ organizacji:** [punkt npp / klinika prawa / fundacja / NGO]
- **Obszary poradnictwa:** [np. mieszkaniowe, rodzinne, konsumenckie, cudzoziemcy, świadczenia, długi]
- **Właściwość / jurysdykcja:** [województwo, właściwe sądy]
- **Kryteria kwalifikacji:** [reguły, według których organizacja kwalifikuje - np. oświadczenie, grupa uprawnionych; wpisz aktualne według przepisów i regulaminu organizacji]
- **Proces sprawdzenia konfliktu:** [jak organizacja sprawdza konflikt interesów]
- **Źródła finansowania / ograniczenia:** [jeśli dotyczy - ograniczenia narzucone przez grantodawcę]

---

## Część 2 - Model nadzoru (wybierz jeden, wypełnia `konfiguracja`)

Plugin dostosowuje się do tego, jak organizacja realnie nadzoruje, nie odwrotnie.

1. **Formalna kolejka przeglądu** - wynik kierowany do klienta/sądu trafia do kolejki, koordynator zatwierdza, wszystko logowane.
2. **Konfigurowalne flagi, przegląd nieformalny** - określone wyzwalacze oznaczają wynik etykietą `SPRAWDŹ Z KOORDYNATOREM`, bez mechanizmu kolejki.
3. **Lżejszy nadzór** - standardowe etykiety szkicu na wszystkim, koordynator nadzoruje przez istniejącą strukturę organizacji (narady, przegląd akt).

**Wybrany model:** [ustawia `konfiguracja`]

---

## Część 3 - Kręgosłup nadzoru i weryfikacji (stały, NIE edytuj)

### Markery pewności (każdy skill stosuje w treści)

Ufaj flagom bardziej niż ich brakowi. Brak flagi NIE oznacza, że prawnik pomija weryfikację.

- `[SZKIC AI - wymaga analizy i nadzoru uprawnionego prawnika]` - etykieta bazowa na każdym wyniku. To etykieta przeglądu, nie treść dla klienta; usuń przed wysłaniem czegokolwiek.
- `[NIEPEWNE: powód]` - skill jest realnie niepewny w tym miejscu.
- `[DO WERYFIKACJI: twierdzenie - sprawdź źródło]` - twierdzenie prawdopodobne, ale niezweryfikowane. Prawnik potwierdza przed oparciem się na nim.
- `[POTRZEBNE BADANIE: ...]` - luka badawcza w szkielecie memo, nie wniosek.
- `[ANALIZA PRAWNIKA: ...]` - miejsce na analizę celowo puste.
- `[WNIOSEK PRAWNIKA: ...]` - miejsce na wniosek celowo puste.
- `[BRAK FAKTU: ...]` - wymagany fakt nieobecny w aktach. Prawnik uzupełnia; bez zgadywania.
- `[OGRANICZENIE RODO/AI ACT: ...]` - flaga, gdy planowane działanie może dotykać ograniczeń RODO lub AI Act; osoba ds. zgodności w organizacji waży.
- `SPRAWDŹ Z KOORDYNATOREM PRZED WYSŁANIEM` / `PRZED ZŁOŻENIEM` - etykieta nadzoru w trybie "konfigurowalne flagi".

### Zasady stałe

- Każdy wynik to szkic (Artykuł I). Nic nie wychodzi bez modelu nadzoru.
- Żaden cytat prawny nie jest pewnikiem (Artykuł III) - tag `[DO WERYFIKACJI]`.
- Bez konektora orzecznictwa każdy cytat jest domyślnie `[DO WERYFIKACJI]`.
- Skille nie zaszywają prawa (Artykuł VII) - czytają konfigurację wyżej.
- Ślad audytowy: każdy istotny wynik logowany (model, data, źródła, kto) - Artykuł V, AI Act art. 12.

---

## Część 4 - Jak plugin się uczy

Ten profil nie jest statyczny - dostrajaj go w miarę użycia. Skille sygnalizują, kiedy wynik użył wartości domyślnej, którą warto doprecyzować w tym pliku.
