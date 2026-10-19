---
{"dg-publish":true,"dg-path":"Notatki/Pytaj model o pewność, nie o odpowiedź.md","permalink":"/notatki/pytaj-model-o-pewnosc-nie-o-odpowiedz/","noteIcon":"","created":"2026-10-19","updated":"2026-10-19","dg-note-properties":{"status":"kiełek","created":"2026-10-19","updated":"2026-10-19","zrodla":["[[Clippings/What Is Jev The AI Model That Doesn't Generate Text-video]]"],"medium":null}}
---

W notatkach zbieram artykuły i filmy, które czekają na jedną decyzję: zarchiwizować, wyciągnąć z nich wnioski czy zostawić na później. Duży model językowy poradzi sobie z każdą z nich, ale przy każdej odpowie równie pewnie. Nie powie, przy których się waha.

W październiku przeniosłem takie decyzje do modelu, który nie pisze tekstu. To Jev: dostaje element i listę moich opcji, a zwraca jedną z nich i pewność. Kategorii, której mu nie dałem, nie wymyśli.

## Pewność to liczba, nie ton

Modele językowe uczy się na preferencjach ludzi, a ludzie wolą odpowiedzi, które brzmią pewnie. Dlatego pytanie „na ile jesteś pewny?” daje ton, a nie prawdopodobieństwo. Model decyzyjny trenowany na kalibracji obiecuje co innego: 80% pewności ma znaczyć trafność w mniej więcej ośmiu przypadkach na dziesięć.

Z taką liczbą granicę między „zrób” a „pokaż mi” ustawia kod, nie model:

- **0,8 i więcej:** element trafia do paczki do wykonania.
- **Od 0,6 do 0,8:** drugi model przegląda go osobno i zostawia jedno zdanie uzasadnienia.
- **Poniżej 0,6:** decyzja wraca do mnie.

![pytaj-model-o-pewnosc-nie-o-odpowiedz-diagram.png](/img/user/Writing/Garden/images/pytaj-model-o-pewnosc-nie-o-odpowiedz-diagram.png)

*Czerwona ścieżka to pułapka: model sam pisze, że jest pewny, a wykonanie rusza bez progu w kodzie.*

Nawet paczka pewnych czeka na moją zgodę. Treść elementu to dane, a tekst podrzucony w treści potrafi przesunąć model na złą opcję z wysoką pewnością. Dlatego najpierw widzę tabelę, a potem wybieram: wykonaj pewne, przejdźmy po kolei albo tylko raport. Dlaczego podgląd musi pokazywać dokładnie to, co się wykona, pisałem w [[Writing/Garden/Notatki/Najpierw podgląd, potem wykonaj\|Najpierw podgląd, potem wykonaj]].

## Co ustawiłem przy wdrożeniu

1. **Model może faworyzować pierwszą opcję.** Każde pytanie z wyborem zadaję więc dwa razy w jednym zapytaniu, raz z odwróconą kolejnością opcji. Koszt prawie nie rośnie, a gdy odpowiedzi się różnią, element trafia do mnie.
2. **Liczy kod, nie model.** Model decyzyjny słabo liczy i porównuje daty. Wiek pliku nie idzie do niego jako data, tylko jako gotowa etykieta, np. „ten tydzień” albo „ponad pół roku”.
3. **Element jest tak pewny jak jego najsłabsze pytanie.** Gdy pytam o dwie rzeczy naraz, np. dokąd przenieść plik i czy jest jeszcze potrzebny, jedno niepewne pytanie wysyła do mnie cały element.

## Gdzie tego nie używam

Model decyzyjny opłaca się przy dziesiątkach elementów i stałym zestawie opcji. Przy jednym wyborze z trzech opcji nie jest lepszy od rozmowy z mocnym modelem. Plan dnia też zostaje przy najmocniejszym modelu, bo to decyzja, po której coś zostaje. Pisałem o tym w [[Writing/Garden/Notatki/Model według rodzaju pracy\|Model według rodzaju pracy]].

Druga granica to dane. Wszystko, co trafia do modelu, wychodzi do kolejnego dostawcy, więc dokumenty finansowe i sprawy służbowe zostają poza nim. Przy takich elementach model dostaje samą nazwę albo decyzję podejmuje model, któremu te dane już powierzyłem.

## Pytanie dla tech leada

Jeśli w twoim produkcie model klasyfikuje zgłoszenia, sprawdź, kto ustawia próg. Jeśli odpowiedź brzmi „model, bo napisał, że jest pewny”, to progu nie ma.

Pewny ton to jeszcze nie pewność. Liczbę da się wpiąć w kod, tonu nie.
