# Málaga, pięć dni

Informator wyprawowy na wyjazd 17–21 września 2026.

**Strona:** https://jakubglowacz.github.io/malaga-2026/
**PDF:** https://jakubglowacz.github.io/malaga-2026/informator-malaga-2026.pdf

## Co tu leży

| Plik | |
|---|---|
| `index.html` | Cała strona — jeden plik, bez zależności poza fontami Google |
| `informator-malaga-2026.pdf` | Wersja do druku, 23 strony A4 |
| `.nojekyll` | Wyłącza przetwarzanie Jekyllem, Pages serwuje pliki wprost |

## To repozytorium jest budowane, nie edytowane ręcznie

Plik `index.html` powstaje automatycznie i **każda ręczna zmiana tutaj zostanie
nadpisana** przy następnej publikacji.

Źródło leży poza repozytorium, w iCloud:

```
Wyjazdy za granicę/09.2026 - Malaga/Informator/
  informator-malaga-2026.html   ← źródło, pełna wersja
  build.py                      ← wycina dane rezerwacji, składa dokument, renderuje PDF
  publish.sh                    ← build + commit + push
```

Wersja źródłowa zawiera numer rezerwacji, PIN Booking.com i telefon do obiektu.
`build.py` usuwa je przed publikacją i **przerywa pracę**, jeśli którykolwiek
z tych ciągów przetrwa redakcję — zarówno w HTML, jak i w wydobytym tekście PDF-a.
Dlatego pełna wersja nigdy nie trafiła do historii gita.

## Aktualizacja

```bash
cd "$HOME/Library/Mobile Documents/com~apple~CloudDocs/Wyjazdy za granicę/09.2026 - Malaga/Informator"
./publish.sh "co się zmieniło"
```

Strona odświeża się w około 40 sekund. Adres nigdy się nie zmienia.

## Wymagania

- Brave (renderowanie PDF) — dowolna przeglądarka Chromium zadziała po zmianie ścieżki w `build.py`
- `pdftotext` z pakietu poppler (`brew install poppler`) — kontrola PDF; bez niego build działa, tylko pomija ten krok
