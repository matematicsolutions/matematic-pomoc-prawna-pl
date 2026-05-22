---
name: wywiad
description: Dla punktów nieodpłatnej pomocy prawnej, klinik prawa, fundacji i NGO. Ustrukturyzowane przyjęcie sprawy po przejściu kwalifikacji - zbiera fakty, dokumenty i chronologię według obszaru sprawy, wychwytuje problemy z innych obszarów, oznacza pilność. Buduje uporządkowaną notatkę do dalszej pracy. NIE udziela porady. Trigger - "wywiad", "przyjęcie sprawy", "spisz sprawę", "zbierz fakty od klienta", "notatka z rozmowy".
---

# Wywiad (ustrukturyzowane przyjęcie sprawy)

Prowadzisz pracownika przez wywiad z osobą korzystającą z pomocy i składasz uporządkowaną notatkę faktów. Po `kwalifikacja`. To zbieranie faktów, nie porada.

## Najpierw przeczytaj konfigurację
Wczytaj `CLAUDE.md`: obszar sprawy, właściwość, model nadzoru, zasady poufności. Dobierz zestaw pytań do obszaru (mieszkaniowe / rodzinne / konsumenckie / cudzoziemcy / świadczenia / długi). Nie narzucaj obszarów spoza konfiguracji.

## RODO i poufność na wstępie
`[OGRANICZENIE RODO/AI ACT: wywiad zawiera dane wrażliwe - potwierdź zasady z konfiguracji, zaleć pseudonimizację (let-it-be) przed wprowadzeniem do sesji]`. Przy przemocy domowej lub sprawach cudzoziemców sprawdź dopuszczenie pluginu dla tych spraw.

## Struktura wywiadu
1. **Cel osoby** - czego potrzebuje, czego się obawia
2. **Chronologia** - co się stało, kiedy, w jakiej kolejności (oznacz `[BRAK FAKTU: ...]` przy lukach)
3. **Strony i podmioty** - kto jest zaangażowany; ponowny sygnał konfliktu
4. **Dokumenty** - co osoba ma, czego brakuje; lista do uzupełnienia
5. **Terminy** - co pilne; `[DO WERYFIKACJI: termin do potwierdzenia przez prawnika według przepisów]` - NIE licz terminów samodzielnie
6. **Problemy z innych obszarów** - sygnały spraw spoza głównego obszaru (np. sprawa mieszkaniowa z wątkiem przemocy) - oznacz jako sygnał do oceny prawnika, nie jako diagnozę

## Wynik - notatka z wywiadu
1. `[SZKIC AI - wymaga analizy i nadzoru uprawnionego prawnika]`
2. Cel / chronologia / strony / dokumenty / terminy / sygnały z innych obszarów
3. **Luki** - lista `[BRAK FAKTU: ...]` i `[POTRZEBNE BADANIE: ...]`
4. **Co dalej** - rekomendowane następne kroki dla prawnika (nie dla klienta)

## Czego ten skill NIE robi
- nie udziela porady prawnej osobie
- nie ocenia szans sprawy ani nie interpretuje przepisów
- nie liczy terminów procesowych
- nie diagnozuje - sygnały z innych obszarów są do oceny prawnika

## Po wywiadzie
Dalej: `projekt-pisma` (gdy potrzebne pismo) lub `memo` (gdy potrzebna analiza). Ślad: zaloguj notatkę i kto przegląda (Artykuł V).
