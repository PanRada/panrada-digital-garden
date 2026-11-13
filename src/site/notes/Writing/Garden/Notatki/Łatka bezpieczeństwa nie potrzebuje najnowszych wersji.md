---
{"dg-publish":true,"dg-path":"Notatki/Łatka bezpieczeństwa nie potrzebuje najnowszych wersji.md","permalink":"/notatki/latka-bezpieczenstwa-nie-potrzebuje-najnowszych-wersji/","noteIcon":"","created":"2026-11-14","updated":"2026-11-14","dg-note-properties":{"status":"kiełek","created":"2026-11-14","updated":"2026-11-14","zrodla":null,"medium":null}}
---

W połowie listopada Next.js dostał poprawki krytycznych podatności, między innymi zdalnego wykonania kodu przez optymalizację obrazków i odmowy usługi przez Server Actions. Ten framework siedzi w kilku moich projektach, więc tego samego dnia każdy z nich dostał łatkę.

Przy takiej łatce odruch jest jeden: zaktualizować wszystko, co się da, i mieć spokój. `npm audit fix --force`, świeży lockfile, zielony audyt. Właśnie tego odruchu pilnowałem najbardziej.

## Pośpiech to też wektor ataku

Groźne ataki na ekosystem npm często nie wchodzą przez starą dziurę, tylko przez nową wersję. Ktoś przejmuje konto opiekuna paczki, publikuje wydanie ze złośliwym kodem i czeka, aż projekty pobiorą je przy najbliższej aktualizacji. Takie wydania zwykle znikają z rejestru po kilku dniach. Kto w dniu alarmu aktualizuje wszystko, sam się zgłasza na ochotnika.

Dlatego łatka ma u mnie jedną regułę: do lockfile nie wchodzi nic młodszego niż 7 dni. Świadomy wyjątek to sama poprawka frameworka, bo ona z definicji jest świeża.

## Jak to wygląda w praktyce

1. **Framework podbijam dokładnie do wersji z poprawką.** Wersja jest przypięta, bez daszka. Jeśli linia, na której jestem, nie ma wydania z pełną poprawką, skaczę dalej, ale świadomie, a nie jako skutek uboczny.
2. **Lockfile przebudowuję z datą graniczną.** npm ma do tego flagę `--before`: bierze tylko wersje opublikowane przed podaną datą. Ustawiam ją na tydzień wstecz i dopiero wtedy uruchamiam `npm audit fix`, bez `--force`.
3. **Sprawdzam, czy starsze wydania zamykają te same podatności.** W tej rundzie zamykały wszędzie. Po przebudowie audyt pokazywał zero krytycznych, choć część paczek została kilka wersji za najnowszą.
4. **To, czego reguła nie domyka, idzie do osobnego zadania.** Zostało kilka podatności o wysokiej wadze, bo ich poprawka wymagała zmiany wersji głównej. Wolę je nazwać i zaplanować, niż przemycić migrację w pilnej łatce.

![latka-bezpieczenstwa-nie-potrzebuje-najnowszych-wersji-diagram.png](/img/user/Writing/Garden/images/latka-bezpieczenstwa-nie-potrzebuje-najnowszych-wersji-diagram.png)

*Czerwona ścieżka to odruch: „zaktualizuj wszystko” wpuszcza do projektu paczki, których nikt jeszcze nie zdążył sprawdzić.*

## Najnowsza wersja to więcej zmian, nie więcej bezpieczeństwa

Reguła dała mi jeszcze jedną korzyść, o której nie myślałem na starcie. W jednym projekcie najnowsza wersja biblioteki do routingu wielojęzycznego zmieniała sposób dopasowania ścieżek. Wersja nieco starsza zamykała tę samą podatność i niczego w aplikacji nie ruszała. Najnowsze wydanie niesie więc nie tylko ryzyko złośliwego kodu, ale też zmiany, których łatka bezpieczeństwa w ogóle nie potrzebuje.

To ta sama myśl, co w [[Writing/Garden/Notatki/Najpierw podgląd, potem wykonaj\|Najpierw podgląd, potem wykonaj]]: pilność nie zwalnia z patrzenia, co dokładnie wchodzi.

## Pytanie dla tech leada

Gdy pojawia się krytyczna podatność, zespół zwykle pyta, jak szybko zaktualizujemy. Dokładam drugie pytanie: co jeszcze wpuścimy razem z tą aktualizacją. Jeśli odpowiedź brzmi „wszystko, co wyszło w tym tygodniu”, łatka zamyka jedną dziurę i otwiera okno na następną.
