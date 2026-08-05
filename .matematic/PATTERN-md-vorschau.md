# Pattern: MD-Vorschau (podglad .md dla plikow binarnych)

Wzorzec z peer-pluginu Klotzkette/claude-fuer-deutsches-recht (Apache-2.0 OR MIT).
Cel: do kazdego binarnego pliku w repo (DOCX, XLSX, PDF) dolaczamy rownolegly podglad `.md`,
zeby przy przegladaniu na GitHubie widac bylo TRESC, nie "binary blob".

## Po co (dla nas)
- **Dyskoverability + GEO**: GitHub i crawlery AI indeksuja Markdown, nie binaria. Wzorow umow/pism
  w .docx nikt (ani crawler) nie przeczyta na GitHubie - .md tak.
- **Review bez pobierania**: koordynator/prawnik czyta wzor w przegladarce, bez sciagania pliku.
- **Slad i audyt**: diff na .md pokazuje zmiany merytoryczne miedzy wersjami wzoru (binarny diff = nieczytelny).
- **Spojne z naszym standardem 10/10** i z reguła "repo czytelne".

## Konwencja nazewnictwa
```
wzory/pozew-o-zaplate.docx
wzory/pozew-o-zaplate.docx.md        <- podglad (suffix .md na pelnej nazwie)
```
Albo katalog `_podglad/` lustrzany do struktury binariow - do wyboru, byle KONSEKWENTNIE.

## Co zawiera podglad .md
- naglowek: nazwa pliku, typ, wersja, data, "PODGLAD - zrodlo prawdy to plik binarny"
- tresc tekstowa wyekstrahowana z dokumentu (markitdown / opendataloader-pdf / pdftotext wg drabinki PDF z CLAUDE.md)
- przy wzorach pism: pola do uzupelnienia oznaczone, marker `[SZKIC AI]` jesli generowane

## Generowanie (drabinka z globalnego CLAUDE.md)
1. Prosty tekst -> `pdftotext` / bezposrednia ekstrakcja
2. Pisma/umowy z naglowkami -> skill `markitdown` (zachowuje strukture)
3. Tabele/kolumny (KRS, finansowe) -> skill `opendataloader-pdf`
4. Skany -> Chandra OCR

## Idempotentny skrypt wsadowy (szkielet, do dopracowania)
Dla kazdego DOCX/XLSX/PDF bez aktualnego `.md` -> wygeneruj podglad. Uruchamiany w pre-commit
lub recznie. RODO: NIE generuj podgladow dla plikow z realnymi danymi osobowymi (tylko wzory/szablony).

## Zakres wdrozenia
- TEN repo: gdy dojda wzory pism/umow w binariach.
- **Wszystkie repo MateMatic z deliverable'ami binarnymi** (kandydat na regule w AGENTS.md kanonie).
- NIE dla repo z danymi wrazliwymi (najpierw let-it-be / pseudonimizacja).

## Atrybucja
Pattern zaobserwowany w Klotzkette/claude-fuer-deutsches-recht. Wlasna implementacja, tresc od zera.
Patrz rejestr ocen wpis #64, [[project_nowe_skille_legaltech_2026-05-22]].
