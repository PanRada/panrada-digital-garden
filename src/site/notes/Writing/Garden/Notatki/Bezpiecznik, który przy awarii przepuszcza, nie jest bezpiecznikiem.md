---
{"dg-publish":true,"dg-path":"Notatki/Bezpiecznik, który przy awarii przepuszcza, nie jest bezpiecznikiem.md","permalink":"/notatki/bezpiecznik-ktory-przy-awarii-przepuszcza-nie-jest-bezpiecznikiem/","noteIcon":"","created":"2026-10-31","updated":"2026-10-31","dg-note-properties":{"status":"kiełek","created":"2026-10-31","updated":"2026-10-31","zrodla":["[[Development/Vault/Hooki i deny rules w Claude Code]]","[[Clippings/Hooki Claude Code nie działają 12 przyczyn i poprawek-artykuł]]"],"medium":null}}
---

W Claude Code skrypt, który pilnuje akcji agenta, może zakończyć się błędem na dwa sposoby. Kod wyjścia 2 blokuje akcję. Kod 1 to zwykły błąd i akcja idzie dalej. Strażnik, który się wysypie, otwiera więc drzwi.

Miałem to przed oczami w październiku, kiedy dopisywałem bezpiecznik na destrukcyjne operacje na bazach danych. W trybie automatycznym takie wywołanie nie zatrzymałoby się na prośbie o zgodę.

## Instrukcja to za mało

Zakaz w pliku z instrukcjami wykonuje się, jeśli model o nim pamięta. Hook, czyli skrypt odpalany przez narzędzie przy zdarzeniu, działa poza pętlą modelu i wykonuje się zawsze.

Mój hook zatrzymuje kasowanie tabel, schematów i baz, usuwanie kolumn, `TRUNCATE`, `DELETE` bez `WHERE` oraz reset i usuwanie gałęzi bazy. Przepuszcza usuwanie polityk, funkcji czy indeksów, bo to codzienność migracji. Gdyby je blokował, szybko bym go wyłączył.

![bezpiecznik-ktory-przy-awarii-przepuszcza-diagram.png](/img/user/Writing/Garden/images/bezpiecznik-ktory-przy-awarii-przepuszcza-diagram.png)

*Czerwona ścieżka to pułapka: skrypt się wysypuje, a operacja, którą miał zatrzymać, przechodzi.*

## Trzy zasady

1. **Awaria to blokada.** Skrypt łapie każdy wyjątek i kończy się kodem 2. W konfiguracji nie ma `|| true`. Interpreter ma ścieżkę bezwzględną, bo gdyby powłoka nie znalazła go po nazwie, zwróciłaby kod 127, czyli przepuszczenie.
2. **Zgodę daje człowiek, po blokadzie.** Agent pokazuje mi dokładną komendę, a ja odpisuję hasłem. Liczy się tylko moja wiadomość wysłana po blokadzie. Hasło w tekście modelu, w wyniku narzędzia, we wstawce systemowej albo w poleceniu dla subagenta jest ignorowane, bo model mógł je tam napisać albo przeczytać w danych.
3. **Zgoda obejmuje jedno wywołanie.** Bezpiecznik zapamiętuje skrót nazwy narzędzia i argumentów. Przechodzi to samo wywołanie, raz. Zmiana w zapytaniu to nowa blokada. To zasada z [[Writing/Garden/Notatki/Najpierw podgląd, potem wykonaj\|Najpierw podgląd, potem wykonaj]]: zatwierdzam dokładnie to, co się wykona.

## Bezpiecznik też psuje się po cichu

Strażnik, który nie wystartował, wygląda tak samo jak strażnik, który nie miał czego zatrzymać. Pierwsza tura testów wcześniejszego hooka przeszła na zielono, chociaż skrypt w ogóle się nie uruchomił. Teraz sprawdzam efekt uboczny, a nie sam kod wyjścia.

Z tego samego powodu reguła dopasowania nie jest przypięta do identyfikatora połączenia z bazą. Po ponownym podłączeniu nazwa by się zmieniła i bezpiecznik zamilkłby bez komunikatu. O takich awariach pisałem w [[Writing/Garden/Notatki/Automatyzacja psuje się po cichu\|Automatyzacja psuje się po cichu]].

Ten bezpiecznik przeszedł 17 przypadków zapytań i narzędzi, 9 przypadków ścieżki z hasłem i test na żywo w nowej sesji.

Znam też jego granicę. Pilnuje agenta, nie mnie: w panelu bazy mogę zrobić wszystko. To bezpiecznik na pomyłki, nie zamek.

## Pytanie dla tech leada

Jeśli dajesz agentowi dostęp do bazy, nie pytaj, czy zakaz jest w instrukcji. Zapytaj, co się stanie, gdy strażnik się wysypie, i skąd wie, że zgodę wyraził człowiek.

Instrukcję model może pominąć. Bezpiecznik ma zamykać drzwi także wtedy, gdy sam się psuje.
