# Szablon SKILL.md - matematic-pomoc-prawna-pl

Kanoniczny szkielet skilla pluginu. Godzi house style (5 skilli v0.1.0) z wzorcem
strukturalnym z peer-pluginow (Klotzkette/claude-fuer-deutsches-recht, Apache-2.0 OR MIT)
ORAZ Konstytucja pluginu - w szczegolnosci **Artykul VII: skille nie zaszywaja prawa**.

Roznica od wzorca DE: niemiecki skill wbija paragrafy (§§) i orzeczenia BGH wprost w tresc.
U NAS to zlamanie Art. VII. Sekcja "Rama prawna" wskazuje konfiguracje + grounding,
a przepisy sa placeholderem `[DO WERYFIKACJI]`, nigdy autorytetem zaszytym w modelu.

---

```markdown
---
name: nazwa-skilla
description: Dla [punktow npp / klinik prawa / fundacji / NGO]. [Co robi, w 1-2 zdaniach.] [Z czyjej perspektywy - jesli sprawa ma dwie strony, nazwij obie.] [Czego NIE robi - jedno zdanie granicy.] Trigger - "fraza 1", "fraza 2", "fraza 3".
---

# Nazwa skilla (krotki opis w nawiasie)

[Jedno zdanie: komu pomaga i w czym. Wprost: "Nie decydujesz / nie doradzasz -
to robi uprawniony prawnik."]

## Najpierw przeczytaj konfigurację
Wczytaj `CLAUDE.md`. Uzyj wartosci ZAPISANYCH przez organizacje (obszary, wlasciwosc,
kryteria, model nadzoru). Artykul VII: nie podawaj wlasnych regul prawnych z pamieci modelu.
Pole puste/niejasne -> `[DO WERYFIKACJI: ... - potwierdz z koordynatorem]`, nie zgaduj.

## Wejscia
Ponumerowana lista tego, czego skill potrzebuje na wejsciu (wzor: Eingaben):
1. **Stan faktyczny** - ...
2. **Dokumenty** - ...
3. **Perspektywa** - [strona A / strona B], jesli dotyczy
4. **Cel** - ...
(Brak wymaganego wejscia -> `[BRAK FAKTU: ...]`, bez zgadywania.)

## RODO i poufność
Na wstepie `[OGRANICZENIE RODO/AI ACT: ... - potwierdz zasady poufnosci z konfiguracji]`.
Zalec pseudonimizacje (skill let-it-be) przed wklejeniem wrazliwych danych. Przy obszarach
o podwyzszonej poufnosci sprawdz w konfiguracji, czy plugin jest dopuszczony.

## Rama prawna (NIE zaszywamy prawa - Art. VII)
- Wlasciwe przepisy i orzecznictwo bierze prawnik / konfiguracja organizacji, nie skill.
- Jesli skill przywoluje przepis lub orzeczenie - ZAWSZE z markerem `[DO WERYFIKACJI: art. X / sygn. - sprawdz zrodlo]`.
- Bez konektora orzecznictwa kazdy cytat jest domyslnie `[DO WERYFIKACJI]`.
- (Roznica od wzorca DE, ktory wbija §§/BGH w skill - u nas to byloby zlamanie Art. VII + ryzyko cite-trap.)

## Wynik
Struktura outputu, zawsze zaczynajaca sie etykieta bazowa:
1. `[SZKIC AI - wymaga analizy i nadzoru uprawnionego prawnika]`
2. ... (kolejne sekcje wyniku)
N. **Rekomendacja / szkielet** - jako rekomendacja lub rama, NIGDY jako rozstrzygniecie.

## Czego ten skill NIE robi
- nie decyduje / nie doradza / nie sklada pisma (wlasciwa granica skilla)
- nie podaje wlasnych regul ustawowych - czyta konfiguracje
- (kolejne twarde granice)

## Po [skillu]
Nastepny krok w lancuchu (np. -> `wywiad`). Slad: zaloguj wynik i kto go przeglada (Art. V, AI Act art. 12).
```

---

## Reguly stosowania
- **Markery pewnosci** (Czesc 3 CLAUDE.md): `[SZKIC AI]`, `[DO WERYFIKACJI]`, `[NIEPEWNE]`,
  `[POTRZEBNE BADANIE]`, `[ANALIZA PRAWNIKA]`, `[WNIOSEK PRAWNIKA]`, `[BRAK FAKTU]`, `[OGRANICZENIE RODO/AI ACT]`.
- **"Dla kogo"** na poczatku `description` KAZDEGO skilla (na zyczenie Wieslawa).
- **Pelne polskie diakrytyki** w tresci skilla (tu w szablonie pominiete dla czytelnosci kodu).
- **Trigger** zawsze na koncu `description`, 3-5 fraz w cudzyslowie.
- Sekcje opcjonalne wg typu skilla: "Wejscia" i "Rama prawna" pomijasz w skillu czysto
  konfiguracyjnym (np. `konfiguracja`); zawsze w skillu merytorycznym.
