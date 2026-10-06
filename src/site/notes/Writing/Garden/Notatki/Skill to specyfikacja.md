---
{"dg-publish":true,"dg-path":"Notatki/Skill to specyfikacja.md","permalink":"/notatki/skill-to-specyfikacja/","noteIcon":"","created":"2026-10-06","updated":"2026-10-06","dg-note-properties":{"status":"kiełek","created":"2026-10-06","updated":"2026-10-06","zrodla":null,"medium":null}}
---

W skanerze, który co miesiąc przegląda moje notatki, jest linijka wyglądająca na zbędną. Zanim tekst trafi do normalizacji Unicode, zamienia „ł” na „l”. Po co, skoro normalizacja i tak rozkłada polskie znaki na literę i ogonek?

Bo nie rozkłada wszystkich. „Ą”, „ć” czy „ż” mają rozkład, a „ł” jest osobną literą z kreską i normalizacja zostawia ją bez zmian. Bez tej linijki skaner przepuszczał najczęstszą literówkę w polskich nazwach plików. Z kodu tego nie wyczytasz. Mówi o tym specyfikacja.

## Kanon i instalacja

Tak samo traktuję skille, czyli zapisane instrukcje, które agent AI ładuje przy konkretnym zadaniu. Każdy skill ma u mnie dwie warstwy:

- **Kanon** leży w notatkach, obok reszty mojej wiedzy. Zapisuję w nim zakres, konwencje, pułapki, uzasadnienia decyzji i precedensy z datami.
- **Instalacja** to plik, który agent faktycznie odpala. Jest wykonywalną formą kanonu i niczym więcej.

Między nimi obowiązują trzy zasady:

1. **Przy rozbieżności wygrywa kanon.** Jeśli skill robi co innego, niż mówi kanon, poprawiam skill.
2. **Zmiana idzie najpierw do kanonu.** Poprawka wprowadzona tylko w instalacji jest szybsza, ale zostawia nieaktualny dokument, który ma rozstrzygać spory.
3. **Odbudowuję ze specyfikacji, nie z kopii.** Gdy instalacja zginie, czytam kanon i buduję skill od nowa.

![skill-to-specyfikacja-diagram.png](/img/user/Writing/Garden/images/skill-to-specyfikacja-diagram.png)

*Czerwona ścieżka to skrót, który kusi: poprawka trafia tylko do instalacji, a kanon, który rozstrzyga spory, zostaje w tyle.*

Kanon synchronizuje się razem z notatkami, a instalacje leżą w katalogu domowym. Mam jeszcze skille bez kanonu. Jeśli stracę ten katalog, przepadną razem z powodami, dla których działały tak, a nie inaczej.

## Opis, który miał rację

Najlepiej widać to wtedy, gdy opis i kod się rozjadą. Skrypt, który rozkłada moje szybkie wpisy na zadania, pomysły i materiały do przeczytania, miał w opisie dwa tryby: podgląd, który niczego nie zmienia, i wykonanie. Napisałem go od nowa na drugim komputerze, a stara wersja żyła dalej na pierwszym. Synchronizacja nadpisała nową wersję starą. Przez co najmniej sześć tygodni opis mówił o podglądzie, a kod bez pytania zapisywał pliki.

Kiedy to wyszło, trzeba było ustalić, co jest prawdą. Przywróciłem kod do opisu, bo to w opisie siedziały decyzje, na przykład ta, że żaden wpis nie zostaje w skrzynce bez przydziału. Dlaczego podgląd ma sens tylko wtedy, gdy wykonanie robi dokładnie to samo, pisałem w [[Writing/Garden/Notatki/Najpierw podgląd, potem wykonaj\|Najpierw podgląd, potem wykonaj]].

## Co wpisuję do kanonu

Instrukcja krok po kroku jest w kanonie najmniej trwała. Najcenniejsze są rzeczy, których z kodu nie odczytasz:

- **decyzje z datą i powodem**, żeby nikt ich później nie „uprościł”;
- **pułapki z precedensem.** Diagramy na tej stronie gubiły ostatnią literę etykiet, dopóki skrypt nie przełączył się z etykiet HTML na SVG. Bez tego wpisu powrót do ustawień domyślnych wyglądałby na porządki;
- **granice zakresu:** czego skill nie robi i dlaczego.

## Pytanie dla tech leada

Jeśli wprowadzasz agentów AI do zespołu, prompt w repozytorium to dopiero instalacja. Zapytaj, gdzie jest specyfikacja: gdzie żyje, kto ją czyta i co wygrywa, kiedy rozjedzie się z tym, co agent robi.

Ze specyfikacji odtworzę instalację. Z instalacji nie odtworzę powodów.
