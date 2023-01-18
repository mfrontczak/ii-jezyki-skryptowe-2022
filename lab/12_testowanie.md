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

**Cykl pisania:**

* Piszemy test który nie przechodzi (zgodnie z wymaganiami aplikacji)
* Piszemy minimalny wymagany fragment kodu aby nasz test przeszedł.
* refaktorujemy kod celem optymalizacji i poprawy jakości.

## Przykłady
Podstawowe testowanie kodu przy pomocy wyrażenia `assert`. 

Przykład 1
```python
def foo():
    return 4
    
def test_foo():
    assert 4 == foo()

if __name__ == "__main__":
    test_foo()
```
Skrypt wykona się bez zgłaszania żadnych problemów jeżeli wyrażenie `4 == foo()` zwróci wartość `True`.
W innym wypadku zostanie zgłoszony wyjątek `AssertionError`.

Więcej na ten temat proszę przeczytać na https://realpython.com/python-assert-statement/.

Przykład 2
``` python
def capital_case(x):
    return x.capitalize()

def test_capital_case():
    assert capital_case('camouflage') == 'Camouflage'

def test_raises_exceptions():
    with pytest.raises(TypeError):
        capital_case2(9)

def capital_case2(input):
    if not isinstance(input, str):
        raise TypeError('Input value must be string type')
      return input.capitalize()
```
Przykład 3 - *fixture* 
```python
import pytest

class Fruit:
    def __init__(self, name):
        self.name = name

    def __eq__(self, other):
        return self.name == other.name

@pytest.fixture
def my_fruit():
    return Fruit("apple")

@pytest.fixture
def fruit_basket(my_fruit):
    return [Fruit("banana"), my_fruit]

def test_my_fruit_in_basket(my_fruit, fruit_basket):
    assert my_fruit in fruit_basket
```
Przykład 4 - *parametrize*
```python
@pytest.mark.parametrize("test_input,expected", [("3+5", 8), ("2+4", 6), ("6*9", 54)])
def test_eval(test_input, expected):
    assert eval(test_input) == expected
```

## Zadania
1. Napisz funkcję która będzie sprawdzać przy pomocy `assert` czy przekazana wartość jest poprawnym rokiem. A następnie zwróci czy rok jest przestępny.
```python 
def is_leap_year(year): 
   pass
   
print( is_leap_year(2023) ) # poprawna wartość brak wyjątku

print( is_leap_year(-1232) ) # nie poprawna wartość, zostanie zgłoszony wyjątek
```
2. Przygotuj testy funkcji sprawdzającej czy osoba o przekazanym wieku jest pełnoletnia dla wieku 4, 18, 24, 38  
```python
def is_adult(age)
```
3. Przygotuj testy funkcji zwracającej pole koła dla trzech różnych wartości, dodatkowo rozważ warunek w którym promień zostanie podany jako typ różny od *int* lub *float*  
```python
def calculate_circle_area(r)
```
4. Przygotuj test sprawdzający działanie funkcji sortującej (własnej implementacji) wywołanej na liście zawierającej listę miast, adresów mailowych, numerów telefonów oraz wartości logicznych. Do przekazywania różnych danych wykorzystaj konstrukcję ```parametrize```
5. Przygotuj klasę *Kalkulator* posiadającą funkcje *dodawanie, mnożenie i potęgowanie*. Zaproponuj testy jednostkowe weryfikujące działanie kalkulatora.
