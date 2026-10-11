---
{"dg-publish":true,"dg-path":"Notatki/Model według rodzaju pracy.md","permalink":"/notatki/model-wedlug-rodzaju-pracy/","noteIcon":"","created":"2026-10-11","updated":"2026-10-11","dg-note-properties":{"status":"kiełek","created":"2026-10-11","updated":"2026-10-11","zrodla":null,"medium":null}}
---

Do niedawna każde wywołanie AI w moich automatyzacjach szło do tego samego modelu: najmocniejszego, w wersji z najdłuższym kontekstem. Nie dlatego, że tak postanowiłem. Po prostu nikt nie postanowił inaczej, a wywołanie bez wskazanego modelu dostaje domyślny.

Ten sam model sortował wpisy ze skrzynki, streszczał artykuły, pisał poranny brief i układał priorytety tygodnia. Robił cztery bardzo różne rzeczy za tę samą cenę.

## Trzy rodzaje pracy

Teraz każde zadanie ma model przypisany do rodzaju pracy, a nie do miejsca, w którym się odbywa:

- **Najtańszy model czyta i przenosi.** Zbiera dane, klasyfikuje według reguł, liczy i formatuje.
- **Średni pisze i łączy.** Przygotowuje poranny brief, streszczenia, notatki ze spotkań, szkice i kod według gotowego planu.
- **Najmocniejszy decyduje.** Ustala priorytety dnia, zobowiązania wobec zespołu i architekturę, a także ocenia, czy tekst może wyjść publicznie.

W skryptach, które codziennie mi pomagają, jest jedenaście wywołań AI. Cztery trafiły do najtańszego modelu, a sześć do średniego. Najmocniejszemu zostało jedno: to, które składa moje zobowiązania na tydzień wobec zespołu.

## Tani zbiera, mocny decyduje

Najwięcej zmienił podział pracy w obrębie jednego zadania. Skille, które układają mi plan dnia i prowadzą wieczorny przegląd, zostały na najmocniejszym modelu. Dane do nich, czyli kalendarz, pocztę, zadania i notatki, zbiera jednak agent na najtańszym modelu. Dostaje polecenie tylko do odczytu, niezależne źródła sprawdza równolegle i oddaje zwięzły raport.

Model, który decyduje, nie wciąga surowych wyników do kontekstu. Dostaje raport, waży źródła i rozmawia ze mną. Jego uwaga idzie na decyzję, a nie na przewijanie danych.

## Zasady, które przy tym wyszły

1. **Model ustawiam w jednym miejscu.** W skryptach jest jedna mapa zadań. Nowe wywołanie bez wpisu w mapie kończy się błędem, więc nie da się znowu po cichu wrócić do domyślnego modelu.
2. **Każdy poziom ma model zapasowy.** Gdy wybrany model jest przeciążony, tani przechodzi na średni, średni na najmocniejszy, a najmocniejszy na średni.
3. **Zmiana stanu dostaje mocniejszy model niż odczyt.** W skrypcie pocztowym przegląd skrzynki robi najtańszy model, a archiwizację, która coś zmienia, średni.

## Pytanie, które zadaję teraz

Przy nowym zadaniu dla AI nie pytam już, który model jest najlepszy. Pytam, jaką pracę to zadanie wykonuje i co się stanie, jeśli model się pomyli. Najmocniejszy model dostał zadania, po których coś zostaje: plan, obietnica wobec ludzi, tekst na stronie. Resztę może zrobić tańszy, bo jego wynik i tak trafia do kogoś, kto decyduje.
