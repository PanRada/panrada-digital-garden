---
{"dg-publish":true,"dg-path":"Notatki/Pusto i nie sprawdzono to dwa różne wyniki.md","permalink":"/notatki/pusto-i-nie-sprawdzono-to-dwa-rozne-wyniki/","noteIcon":"","created":"2026-11-07","updated":"2026-11-07","dg-note-properties":{"status":"kiełek","created":"2026-11-07","updated":"2026-11-07","zrodla":null,"medium":null}}
---

Poranny plan dnia składa mi agent. Główny wątek rozdziela pracę na zbieraczy, czyli subagentów, z których każdy czyta jedno źródło: zadania, kalendarz, pocztę, tablicę projektów. Na końcu dostaję plan i jedną linijkę kontrolną: „Braki źródeł: brak”.

Na początku listopada ta linijka skłamała. Jeden zbieracz wystartował bez dostępu do narzędzi, plan został uzupełniony po cichu, a raport i tak mówił, że niczego nie brakuje. Jedno ze źródeł nie zostało sprawdzone wcale.
## Skąd się wziął brak

To nie był błąd modelu, tylko wyścig na starcie sesji. Orkiestrator rejestruje zbieracza z tymi narzędziami, które są dostępne w danej chwili. Połączenia z zewnętrznymi usługami zestawiają się chwilę później. Zbieracz, który ruszy za wcześnie, dostaje komunikat „narzędzie niedostępne” i oddaje to, co ma, czyli nic.

Samo „nic” jest w porządku. Problem w tym, że po drodze zmieniło znaczenie. Dla zbieracza znaczyło „nie mogłem sprawdzić”, a w raporcie stało się „sprawdziłem i jest pusto”.

![pusto-i-nie-sprawdzono-to-dwa-rozne-wyniki-diagram.png](/img/user/Writing/Garden/images/pusto-i-nie-sprawdzono-to-dwa-rozne-wyniki-diagram.png)

*Czerwona ścieżka to pułapka: brak dostępu przechodzi do raportu jako czysty wynik.*

## Trzy zasady

1. **Brak dostępu ponawiam raz, zbiorczo.** Skoro to zwykle wyścig, druga próba po chwili najczęściej przechodzi. Jedno zlecenie na wszystkie brakujące źródła, a nie pętla prób, która maskuje prawdziwą awarię.
2. **Gdy dalej brak, sprawdzam sam.** Główny wątek ma pełny dostęp i może zajrzeć do źródła bezpośrednio. Zbieracz to optymalizacja, a nie jedyna droga do danych.
3. **Raport nazywa każdą lukę.** Albo „źródło X: zbieracz bez dostępu, uzupełnione ręcznie”, albo „źródło X niedostępne”. „Brak braków” wolno napisać tylko wtedy, gdy każde źródło z listy faktycznie zwróciło wynik, także te, które sprawdzam rzadko i najłatwiej o nich zapomnieć.

## Pusta lista to też twierdzenie

„Nie znaleziono” jest twierdzeniem o świecie. „Nie sprawdzono” jest twierdzeniem o procesie. Agent, który ich nie rozróżnia, daje wynik, który wygląda na czysty, a jest dziurą. To ten sam typ awarii, o której pisałem w [[Writing/Garden/Notatki/Automatyzacja psuje się po cichu\|Automatyzacja psuje się po cichu]] i [[Writing/Garden/Notatki/Bezpiecznik, który przy awarii przepuszcza, nie jest bezpiecznikiem\|Bezpiecznik, który przy awarii przepuszcza, nie jest bezpiecznikiem]]: system, który nie wystartował, wygląda tak samo jak system, który nie miał nic do zrobienia.

U ludzi to rozróżnienie jest naturalne. Nikt nie powie „klient nie ma zaległości”, jeśli nie mógł otworzyć systemu. Model powie, bo z jego perspektywy brak danych i brak problemu wyglądają tak samo, a raport bez braków brzmi lepiej.

## Pytanie dla tech leada

Jeśli Twój agent zbiera dane z kilku źródeł, nie pytaj, czy raport jest kompletny. Zapytaj, jak raport wyglądałby, gdyby jedno źródło w ogóle nie odpowiedziało. Jeśli tak samo, to „brak braków” nic Ci nie mówi.
