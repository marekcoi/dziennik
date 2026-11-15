# Dziennik – instalacja na iPhonie (bez kosztów, bez przebudowy)

## Co jest w paczce
| Plik | Rola |
|---|---|
| `index.html` | cała aplikacja |
| `sw.js` | działanie offline |
| `manifest.webmanifest`, `icon-180.png`, `icon-512.png` | ikona i tryb pełnoekranowy |
| `robots.txt` | blokuje indeksowanie przez wyszukiwarki |

W kodzie nie ma żadnych opisowych nazw kategorii – tylko litery R/P/D/E. Twoje własne nazwy, wpisy i notatki istnieją wyłącznie w zaszyfrowanej bazie na telefonie.

## Instalacja (ok. 10 minut, jednorazowo)

1. **GitHub** – załóż konto (github.com), jeśli nie masz. Nazwa konta będzie częścią adresu, więc wybierz neutralną.
2. **Nowe repozytorium** → „New” → nazwa neutralna, np. `notes` → **Public** (darmowe GitHub Pages wymaga publicznego repozytorium; publiczny jest tylko kod, nie dane).
3. **Wgraj pliki** → „Add file” → „Upload files” → wszystkie 6 plików z paczki (rozpakuj ZIP w aplikacji Pliki) → „Commit changes”.
4. **Włącz Pages** → Settings → Pages → Source: *Deploy from a branch* → Branch: `main`, folder `/ (root)` → Save. Po 1–2 min adres: `https://<login>.github.io/notes/`
5. **Na iPhonie w Safari** otwórz ten adres → Udostępnij → **Do ekranu początkowego** → Dodaj.
6. **Uruchamiaj wyłącznie z ikony**, nie z Safari. Aplikacja z ekranu początkowego ma osobny magazyn danych – PIN ustawiasz przy pierwszym uruchomieniu z ikony.

## Ważne
- **Nie zmieniaj nazwy konta ani repozytorium.** Dane są przypisane do adresu – nowy adres = pusta aplikacja (ratunek: eksport → import).
- **Nie usuwaj repozytorium.** Aplikacja działa offline z pamięci podręcznej, ale iOS może ją kiedyś wyczyścić i wtedy pobierze pliki z adresu.
- **Kopia zapasowa:** Ustawienia → Eksportuj. Plik jest zaszyfrowany osobnym hasłem (min. 8 znaków). Zapisz go np. w Plikach / na iCloud Drive – bez hasła jest nieczytelny. Rób eksport np. raz w miesiącu.
- **Usunięcie ikony z ekranu = usunięcie danych.**
- **Aktualizacja aplikacji:** wgraj nowy `index.html` i w `sw.js` zmień `dz-v1` na `dz-v2` itd. Dane zostają.

## Co chroni, a czego nie
| Sytuacja | Ochrona |
|---|---|
| Ktoś bierze odblokowany telefon | PIN aplikacji, blokada po wyjściu (domyślnie 1 min, zalecam „od razu”) |
| Podgląd w przełączniku aplikacji | zasłona przy przejściu w tło (**niepewne:** iOS bywa szybszy i może złapać zrzut przed jej nałożeniem – ustawienie „blokada od razu” zmniejsza ryzyko) |
| Kopia iCloud / komputera | dane są tylko w postaci zaszyfrowanej (AES-256-GCM) |
| Ktoś zgaduje PIN | licznik prób, domyślnie kasowanie po 10 błędnych |
| Analiza kryminalistyczna skopiowanych danych | **słaba przy krótkim PIN-ie** – 6 cyfr to 1 mln kombinacji; PBKDF2 spowalnia, ale nie uniemożliwia łamania offline. 8 cyfr = 100× trudniej |
| Wyciek przez sieć | brak – aplikacja ma zablokowany dostęp do sieci (Content-Security-Policy) |
