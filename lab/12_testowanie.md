# Lab 12

## Materiały pomocnicze
1. testująca koza - https://www.obeythetestinggoat.com/
2. https://pl.wikipedia.org/wiki/Test-driven_development

## Podział
* **testy jednostkowe** (unit tests) — testujemy pojedynczą jednostkową część taką jak funkcje, metody czy klasy
* **testy integracyjne** (integration tests) — testujemy wiele komponentów systemu za jednym razem
* **testy regresyjne** (regression tests) — wszystkie testy w domenie biznesowej mające na celu sprawdzenie czy zmiana nie spowodowała błędu w innej części systemu
* **testy akceptacyjne** (acceptance tests) — testy weryfikujące czy aplikacja spełnia wymagania biznesowe

## Testowanie skryptów 
Popularną techniką stosowaną w Pythonie do testowania skryptów jest technika TDD (Test Driven Development). Kluczowym aspektem techniki TDD
jest rozpoczęcie pracy nad testami przed dodaniem funkcjonalności.

* funkcjonalności muszą być odizolowane od siebie tak żeby była możliwość ich testowania
* testy jednostkowe są dokumentacją programisty i upewnieniem się, że kod spełnia wszystkie wymagania klienta
* Keep It Simple Stupid czyli nie implementujemy nic na zaś, tylko to co jest aktualnie potrzebne

Cykl pisania:

* Piszemy test który nie przechodzi (zgodnie z wymaganiami aplikacji)
* Piszemy minimalny wymagany fragment kodu aby nasz test przeszedł.
* refaktorujemy kod celem optymalizacji i poprawy jakości.
