
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
