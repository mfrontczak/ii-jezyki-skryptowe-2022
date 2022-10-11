# Języki Skryptowe - Lab 1

**Legenda**

📖 - proszę przeczytać

📝 - warte zapamiętania / zanotowania

⚠️ - zwróć uwagę

✏️ - zadanie do wykonania

🔍 - poszukaj w internecie

## Wprowadzenie
**Python** - Język skryptowy (język programowania wysokiego poziomu) ogólnego przeznaczenia. Do jego głównych cech zalicza się wysoką czytelność kodu źródłowego. Wspiera [programowanie wielo-paradygmatowe](https://pl.wikipedia.org/wiki/Paradygmat_programowania).

---

W przykładach będzie użyty :book: [f-string](https://docs.python.org/3/library/stdtypes.html#printf-style-string-formatting) służący do formatowania tekstu.

Wszystkie udostępnione fragmentu kodu można skopiować i uruchomić w konsoli python'a.

### Przykłady kodu w C i Pythonie

Przykład 1 - wyświetlenie tekstu na ekranie:

**Kod w C**
```C
#include <stdio.h>

int main() {
  printf("Hello World from C\n");
  return 0;
}
```

**Kod w Pythonie**
```python
print("Hello World from Python")
```

Przykład 2 - obsługa pętli:

**Kod w C**
```C
#include <stdio.h>

int main() {
  int array[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
  for(int i = 0; i < 10; i++) {
    printf("%d\n", array[i]);
  }
  return 0;
}
```

**Kod w Pythonie**
```python
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
for i in arr:
    print(i)
```

przykład 3 - definicja funkcji:

**Kod w C**
```C
#include <stdio.h>

int oblicz_delte(short a, short b, short c) {
  return b*b - 4*a*c;
}

int main() {
  printf("delta dla a=1, b=2, c=1 wynosi: %d\n", delta(1, 2, 1));
  return 0;
}
```

**Kod w Pythonie**
```python
def oblicz_delte(a, b, c):
    return b*b - 4*a*c


print("delta dla a=1, b=2, c=1 wynosi: {}".format(oblicz_delte(1,2,1)))
```

### Zarządzanie modułami w Pythonie
W Pythonie modułem nazywamy plik które udostępnia nam zbiór funkcji i/lub klas. 
Moduł importujemy przy użyciu słowa kluczowego `import`, na przykład:
```python
import os
import sys
import pdb
```

Python domyślnie udostępnia standardowa biblioteka modułów pozwalająca nam od razu rozpocząć programowanie.

W przypadku kiedy chcemy wykorzystać moduł który nie znajduje się w standardowej bibliotece, możemy skorzystać z narzędzia `pip` do zarządzania modułami.

Więcej o projekcie i dostępnych modułach można znaleźć na https://pypi.org/.

#### :memo: Lista przydatnych komend

lista zainstalowanych modułów:
```bash
pip list
```
lista zainstalowanych modułów w składni dla komendy `pip install -r`.
```bash
pip freeze > requirements.txt  # zapisujemy informację zainstalowanych modułach do pliku requirements.txt
```

instalacja nowego modułu:
```bash
pip install [--user] [-U] nazwa_pakietu[==konkretna wersja]
pip install -r requirements.txt   # instalujemy listę pakietów które znajdują się w pliku requirements.txt
```

Usunięcie modułu z środowiska:
```bash
pip uninstall nazwa_pakietu
pip uninstall -r requirements.txt  # usunie listę pakietów które znajdują się w pliku requirements.txt
```

**Zadanie**
1. ✏️ Zainstaluj środowisko Anaconda/Python 3.8.
2. ✏️ Zainstaluj moduł `ipython`. :mag:
3. ✏️ Zapoznaj się z dokumentacją opisującą moduł `timeit` (https://docs.python.org/3/library/timeit.html).
4. ✏️ Uruchom `ipython` i wykonaj następujący kod: 
```python
import this
```

### Zmienna

Nazwa zmiennej jest obarczona pewnymi ograniczeniami - nie może zaczynać się od cyfry ani zawierać znaków specjalnych. Zalecane jest nazewnictwo zgodne z przeznaczeniem lub informacją którą ma przechowywać dana zmienna. 

:warning: W Pythonie typ zmiennej jest określany w trakcie przypisania wartości i może się zmienić (jest dynamiczny:dash:). 

```python
zmienna1 = 'Dawid Rybka'    # jest to teraz zmienna typu str (String - Łańcuch znakowy)
print(f'zmienna1={zmienna1}, typ={type(zmienna1)}')
zmienna1 = 12345      # teraz typ zostanie określony na int (Integer - liczba całkowita)
print(f'zmienna1={zmienna1}, typ={type(zmienna1)}')
zmienna1 = 0.4533113  # nowy typ na podstawie przypisania wartości do zmiennej będzie: float (liczba zmienno przecinkowa)
print(f'zmienna1={zmienna1}, typ={type(zmienna1)}')
```

### Standardowe typy danych

#### Proste 
```python
# łancuchy znakowe
str   # string - łańcuch znakowy

# numeryczne
int      # integer - liczba całkowita
float    # floating point number - liczba zmienno przecinkowa
complex  # complex - liczb zespolona
```

przykład:
```python
imie = 'Michał'             # zmienna przechowująca łańcuch znakowy Michał (typ str)
liczba_calkowita = 5        # zmienna przechowująca wartość liczbową 5 (typ int)
liczba_rzeczywista = 3.44   # zmienna przechowująca liczbę rzeczywistą 3.44 (typ float)
prawda = True               # zmienna przechowująca wartość logiczną (typ bool)
c = 1 + 3j                  # zmienna przechowująca liczbę zespoloną (typ complex) 
```

#### Struktury danych
Prócz prostych typów danych, można jeszcze wyróżnić:
```python
list      # tablica gdzie kluczem jest indeks (wartość całkowita) 
dict      # słownik gdzie kluczem może być dowolna wartość - niemodyfikowalna - czyli taka z której można wygenerować unikalny hash
set       # zbiór unikalnych wartości, kluczem jest indeks
tuple     # krotka niemodyfikowalna tablica (lista)
frozenset # zbiór, niemodyfikowalny
```

przykład:
```python
l = [1, 2, 3, 4]  # lista
print(l[3])
l.append(6)
print(l)

d = {     # słownik (mapa klucz-wartość)
  'klucz1': 'ala ma kota',
  'klucz2': 'płotek',
  'moja_lista': l,
  5: 'pięć'
}

d['klucz1']
print(d[5])
# mała modyfikacja
d[5] = 'sześć'
print(d[5])

s = set([1, 3, 5, 3, 2, 1, 1, 1])  # zbiór unikalnych wartości
print(s)
s.add(10)
print(s)

t = (1, 4, 5, 3, 2, 1)  # tuple - krotka
print(t)
print(t[1])

fs = frozenset([1, 3, 4, 3, 3, 2, 1])  # niemodyfikowany zbiór
print(fs)
```

Przykład 2:
```python
l = [1, 2, 3, 4]
l[0] = '2'
print(l)
```
Przykład 3 (powinniśmy otrzymać błąd):
```python
t = (1, 4, 5, 3, 2, 1)
t[1] = 10
print(t)
```

Przykład 4 (też nie działa):
```python
s = {1, 4, 5, 3, 2, 1}  # alternatywna składnia do (nie mylić z słownikiem): set([1, 4, 5, 3, 2, 1])
s[1] = 10
print(s)
```

**Problem**

✏️ Jak zmodyfikować krotkę / zbiór? 

🔍 Poszukaj rozwiązania w sieci.


**Problem**

✏️ zapisz elementy krotki/listy/zbioru do osobnych zmiennych. 

🔍 Poszukaj o rozpakowywaniu sekwencji (unpacking).

```python
t = (5, 'kot', '12,333', 11223)
l = ['2021-10-02', '2021-10-09', '2021-10-16', '2021-10-23', '2021-10-30', '2021-11-06', '2021-11-13', '2021-11-20']
s = {5, 6, 7, 9, 10, 10, 11}

person_info = ['Imię', 'Nazwisko', (2001, 9, 11)]
```

**Zadanie** 

✏️ Sprawdź wydajność poszczególnych struktur danych dla różnych typów danych. (wykorzystaj do tego moduł `timeit`)

**Zadanie** 

✏️ Stwórz listę w której będą wyniki dużego lotka.

**Zadanie** 

✏️ Stwórz słownik (`dict`) w którym będziesz przechowywał informację o ilości schronisk w danym mieście dla miast (kluczy): Kraków, Warszawa, Poznań.

**Zadanie** 

✏️ W Poznaniu i Krakowie wybudowano nowe schronisko, w Warszawie wybudowano aż trzy. 
W poprzednio utworzonym słowniku (`dict`) zaktualizuj informację o liczbie schronisk.

**Zadanie** 

✏️ Do naszego słownika z informacją o schroniskach dodaj nowe miasto Rzeszów z liczbą schronisk 3.


**Zadanie** 

✏️ Stwórz słownik w którym kluczami będą daty w formacie 'YYYY-MM-DD', a wartościami wyniki dużego lotka. 
Wykonaj zadanie dla ostatnich 3 losowań (albo wprowadź własne liczby).

**Zadanie** 

✏️ Korzystając z funkcji `input()` poproś użytkownika o miasto (klucz) dla którego chce wyświetlić informacje o liczbie schronisk.


---
📖 Proszę przeczytać https://docs.python.org/3/library/stdtypes.html, aby dowiedzieć się więcej.


### Sterowanie przebiegiem programu

Instrukcja warunkowa `if`:

przykład 1:
```python
x = 11
if x > 10:
    print("x jest większe niż 10")
elif x == 10:
    print("x jest równe 10")
else:
    print("x jest mniejsze niż 10")
```

przykład 2:
```python
x = 255
arr = [11, 255, 555, 100, 421]
if x in arr:
  pos = arr.index(x)
  print(f"x znajduje sie na pozycji {pos} w liście arr")
else:
  print(f"wartość {x} nie została znaleziona w liście")
```

**Problem**

✏️ W Pythonie nie istnieje instrukcja `switch`. Spróbuj ją zasymulować.

Pętla `while`:
```python
i = 0
while i < 10:
    print(f"i = {i}")
    i += 1
```

Pętla `for`:

Przykład 1:
```python
for i in range(10):
    print(f"i = {i}")
```

Przykład 2:
```python
for slowo in ['ala', 'ma', 'kota']:
    print(f"{slowo}", end=" ")
```

Przykład 3:
```python
for conv in (int, float, str):
    print(f"{conv.__name__}(5.59) = {conv(5.59)}")
```

---
:book: Proszę przeczytać https://docs.python.org/3/tutorial/controlflow.html, aby dowiedzieć się więcej.


### Funkcje

#### Wbudowane funkcje

:memo: Wybrane wbudowanych funkcje które warto znać:
* [print](https://docs.python.org/3/library/functions.html#print)
* [input](https://docs.python.org/3/library/functions.html#input)
* [range](https://docs.python.org/3/library/functions.html#func-range)
* [len](https://docs.python.org/3/library/functions.html#len)
* [help](https://docs.python.org/3/library/functions.html#help)
* [type](https://docs.python.org/3/library/functions.html#type)
* [dir](https://docs.python.org/3/library/functions.html#dir)
* [globals](https://docs.python.org/3/library/functions.html#globals)
* [locals](https://docs.python.org/3/library/functions.html#locals)
* [id](https://docs.python.org/3/library/functions.html#id)
* [hash](https://docs.python.org/3/library/functions.html#hash)
* [hasattr](https://docs.python.org/3/library/functions.html#hasattr)
* [getattr](https://docs.python.org/3/library/functions.html#getattr)
* [isinstance](https://docs.python.org/3/library/functions.html#isinstance)

Przykład 1:
```python
name = input("Jak masz na imię? ")
name_len = len(name)
print(f"{name} to wspaniałe imie! Twoje imie ma {name_len} znaków.")
```

Przykład 2:
```python
age = int(input("Ile masz lat? "))
age_cpy = age

print(f"id({age}) = {id(age)}")
print(f"id({age_cpy}) = {id(age_cpy)}")
```

Przykład 3 (z błędem - bez rzutowania na int):
```python
age = input("Ile masz lat? ")
age_in_10_years = age + 10
print(f"dziś mam {age} a za 10 lat będę miał {age_in_10_years}")
```

---
:book: Proszę przeczytać https://docs.python.org/3/library/functions.html, aby dowiedzieć się więcej.

#### definiowanie własnych funkcji
W pythonie funkcje definiujemy przy użyciu słowa kluczowego `def` i nazwy.

Przykład 1:
```python
def say_hello():
    pass
    
say_hello()  # wywołanie funkcji bez argumentów
```

Przykład 2:
```python  
# przykład funkcji z jednym argumentem
def say_hello_to(name):
    print(f"Hello {name}")


say_hello_to('Johnny')  # wywołanie funkcji z jednym argumentem
```

#### Funkcje z wieloma argumentami
Kolejne argumenty umieszczamy po przecinku (argumenty pozycyjne). Jeżeli chcemy by nasza funkcja przyjmowała dowolną ilość argumentów (pozycyjnych) możemy użyć  `*args`.

Przykład 1:
```python
def sum_numbers(a, b, c, d, e):
    return a + b + c + d + e
```

Przykład 2:
```python
def sum_numbers(*args):
    result = 0
    for number in args:
        result += number
    return result
```
Istnieje również możliwość obsługi dowolnej ilości nazwanych argumentów, z wykorzystaniem `**kwargs`.

Przykład:
```python
d = {}
def add_marks(student, **kwargs):
    d[student] = kwargs


add_marks('Kowalski', JezykiSkryptowe=3, JezykiProgramowania=4, WF=5)
add_marks('Nowak', JezykiSkryptowe=2, JezykiProgramowania=3, WF=4)

print(d)
```
#### Funkcje z domyślną wartością dla argumentów
Kiedy chcemy zdefiniować domyślną wartość argumentu, należy w trakcie definicji funkcji przypisać wartość domyślną dla danego argumentu.

⚠️ Argumenty z domyślną wartością muszą znajdować się na końcu.

Przykład 1:
```python
def foo(a, b, c=0):
    res = 1
    if a > 1:
        res *= a
    if b > 1:
        res *= b
    if c > 1:
        res *= c
    else:
        res *= -1
    return res



bar = foo(3,2,5)  
print(bar)

bar = foo(5,3)  
print(bar)
```

Przykład 2:
```python
def multiple_x_by(x, multiplier=1):
  return x * multiplier


print(multiple_x_by(5))  # domyślną wartością dla multiplier będzie 1
print(multiple_x_by(6, 10)) # w tym przypadku wartość argumentu multiplier wynosi 10
print(multiple_x_by(7))  # domyślną wartością dla multiplier będzie 1
```


**Zadanie** 

✏️ Napisz funkcję która poprosi użytkownika o jego dane osobowe jak imię, nazwisko, wiek. Zaproponuj którą z struktur danych do tego użyć.

✏️ Napisz funkcję która przyjmie dwie wartości liczbowe i zwróci większą z nich (użyj funkcji wbudowanej `max`).

✏️ Napisz funkcję która przyjmie listę liczb jako argument i zwróci sumę liczb znajdujących się w liście.

✏️ Napisz funkcję która przyjmie dowolnie długą listę liczb (użyj `*args`) i zwróci wartość najmniejszą (użyj funkcji wbudowanej `min`).

✏️ Napisz funkcję która przyjmie od użytkownika dane: imie (`str`), nazwisko (`str`), grupa (`str`), obecny (`bool`) i zapisze je do globalnej listy studentów.

---
:book: Proszę przeczytać https://docs.python.org/3/tutorial/controlflow.html#defining-functions, aby dowiedzieć się więcej.
