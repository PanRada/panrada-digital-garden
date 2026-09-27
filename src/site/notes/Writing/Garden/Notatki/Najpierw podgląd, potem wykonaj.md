---
{"dg-publish":true,"dg-path":"Notatki/Najpierw podgląd, potem wykonaj.md","permalink":"/notatki/najpierw-podglad-potem-wykonaj/","noteIcon":"","created":"2026-09-27","updated":"2026-09-27","dg-note-properties":{"status":"kiełek","created":"2026-09-27","updated":"2026-09-27","zrodla":null,"medium":null}}
---

Agent AI, który składa moje wieczorne podsumowania dnia, zapisał kiedyś w notatce błędną liczbę. Poprawić się jej nie dało. Narzędzie, przez które pisał, umiało tylko dopisywać, więc pod błędem pojawiło się sprostowanie, a błędna wersja została na stałe.

## Dwa kroki zamiast jednego

Od tamtej pory agent w ciągu dnia niczego nie zapisuje. Składa szkic lokalnie i pokazuje mi go. Szkic mogę przepisywać do woli, bo poprawki nie zostawiają śladu. Do aplikacji trafia jedna wersja, raz, i dopiero po przeglądzie punkt po punkcie.

Tak samo działa skrypt, który porządkuje moje skrzynki pocztowe. Ma trzy tryby, a domyślny niczego nie zmienia:

- **Podgląd** dzieli wątki na kubełki (do zrobienia, zaległe, do wiedzy, szum) i tylko pokazuje raport.
- **Wykonaj** archiwizuje to, co trafiło do wiedzy i szumu.
- **Wykonaj i odpuść zaległe** to osobna, jawna decyzja. Mieszanie „zrób to” z „czy to jeszcze żyje?” zamienia skrzynkę w cmentarz.

## Podgląd to obietnica

Sam tryb podglądu jeszcze niczego nie gwarantuje. Podgląd jest coś wart tylko wtedy, gdy wykonanie zrobi dokładnie to, co pokazał. Jeśli między „pokaż” a „zrób” model decyduje jeszcze raz, zatwierdzam jedno, a wykonuje się coś innego.

![najpierw-podglad-potem-wykonaj-diagram.png](/img/user/Writing/Garden/images/najpierw-podglad-potem-wykonaj-diagram.png)

*Czerwona ścieżka to pułapka: przy wykonaniu model decyduje od nowa i wykonuje się plan, którego nikt nie zatwierdził.*

Dlatego w moich automatyzacjach obowiązują trzy zasady:

1. **Decyduje kod, nie kolejne wywołanie modelu.** W skrypcie pocztowym kubełki przydziela ta sama deterministyczna funkcja. Tam, gdzie skrypt używa modelu, model tylko przepisuje dane z API i niczego nie ocenia. Gdyby klasyfikował, wynik zmieniałby się między uruchomieniami, czyli właśnie między podglądem a wykonaniem.
2. **Identyfikatory pochodzą ze skryptu, nie z rozmowy.** Przy przeglądzie szkicu decyduję numerami („wywal 7 i 14”), a numery nadaje skrypt. Po każdej zmianie numery się przesuwają, więc lista pokazuje się od nowa. Gdyby punkty numerował model w czacie, po pierwszej poprawce jego numeracja mogłaby już nie pasować do szkicu, a „wywal 7” skasowałoby nie ten punkt.
3. **Po wykonaniu sprawdzam stan, a nie komunikat.** Pierwsza wersja archiwizacji zgłosiła sukces przy zerowej zmianie w skrzynce: serwer przyjął polecenie i nic nie zrobił. Wyszło to tylko dlatego, że ktoś zajrzał do skrzynki po operacji. Teraz skrypt liczy wiadomości przed i po. Więcej o takich awariach pisałem w [[Writing/Garden/Notatki/Automatyzacja psuje się po cichu\|Automatyzacja psuje się po cichu]].

## Właściwe pytanie

Przy automatyzacji z AI, która coś zmienia, pytanie „czy ma podgląd?” to za mało. Właściwe brzmi: czy to, co zobaczę w podglądzie, jest dokładnie tym, co się wykona?

Na tej stronie też to przerabiałem. Publikacja ruszyła, zanim edytor zauważył zmianę pliku, i na stronę poszła starsza wersja. Teraz publikacja czeka kilka sekund, aż edytor zauważy zmianę, a ta notatka czekała jeszcze na moje „publikuj”.

Model może proponować. Zatwierdzam ja, a kod wykonuje dokładnie to, co zatwierdziłem.
