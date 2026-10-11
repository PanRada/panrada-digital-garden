---
{"dg-publish":true,"dg-path":"Notatki/Zaległość mówi więcej niż proces.md","permalink":"/notatki/zaleglosc-mowi-wiecej-niz-proces/","noteIcon":"","created":"2026-10-11","updated":"2026-10-11","dg-note-properties":{"status":"kiełek","created":"2026-10-11","updated":"2026-10-11","zrodla":null,"medium":null}}
---

Przez jedenaście dni nie działało mi przetwarzanie notatek głosowych i nic tego nie zdradzało.

Mechanizm jest prosty. Nagrywam myśl w aplikacji do dyktowania, a skrypt w tle co 30 sekund sprawdza katalog nagrań i wrzuca transkrypcje do mojej skrzynki. Skrypt startuje tylko przy logowaniu do systemu. W połowie września proces został zatrzymany w trakcie sesji i nikt go już nie podniósł. Do skrzynki nic nie trafiało, a cisza wyglądała dokładnie tak samo jak dzień bez nowych myśli.

## Złe pytanie: czy proces żyje?

Pierwszy odruch to sprawdzać, czy proces działa. To łatwe i wystarcza do chwili, gdy proces żyje, ale nie robi swojej roboty. Na przykład patrzy w zły katalog, bo aplikacja do dyktowania potrafi przenieść folder z nagraniami. Wtedy lista procesów jest w porządku, a nagrania i tak leżą.

Lepsze pytanie brzmi: czy coś czeka dłużej, niż powinno? Nagranie, które od dwóch godzin leży nieprzetworzone, oznacza awarię niezależnie od tego, co pokazuje lista procesów.

![zaleglosc-mowi-wiecej-niz-proces-diagram.png](/img/user/Writing/Garden/images/zaleglosc-mowi-wiecej-niz-proces-diagram.png)

*Czerwona ścieżka to przypadek, którego samo sprawdzanie procesu nie złapie: proces działa, a nagrania i tak czekają.*

## Jak to teraz działa

Poranny brief, który i tak czytam codziennie, dostał jedną dodatkową linię. Pojawia się tylko przy awarii:

- **Dwa niezależne testy.** Pierwszy sprawdza, czy proces żyje. Drugi sprawdza, czy w katalogu leżą nagrania starsze niż dwie godziny, których nie ma na liście przetworzonych. Ostrzeżenie pokazuje się, gdy którykolwiek z nich zawiedzie.
- **Próg z zapasem.** Przerwane nagranie skrypt odpuszcza dopiero po godzinie, więc próg dwóch godzin nie zgłasza zwykłego opóźnienia.
- **Konkret zamiast „coś nie działa”.** Linia mówi, ile nagrań czeka i ile z nich miało trafić do moich notatek.
- **Cisza tam, gdzie usługa nie ma działać.** Na drugim komputerze skrypt z założenia nie chodzi, więc ostrzeżenie tam milczy, zamiast codziennie fałszywie alarmować.
- **Liczy kod, nie model.** Brief pisze AI, ale tę linię dokleja skrypt, który sam sprawdza proces i katalog.

## Odpowiedź na stare pytanie

W [[Writing/Garden/Notatki/Automatyzacja psuje się po cichu\|Automatyzacja psuje się po cichu]] pytałem, skąd się dowiem, że automatyzacja przestała działać. Dla tego skryptu odpowiedź brzmi: z porannego briefu, i tylko wtedy, gdy coś naprawdę czeka. Kiedy wszystko działa, ostrzeżenia nie ma, więc każde, które się pojawi, coś znaczy.

Żywy proces niczego nie dowodzi. Nagranie, które czeka ponad dwie godziny, mówi wszystko.
