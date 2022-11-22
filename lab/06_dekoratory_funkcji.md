# Lab 6

## Zakresy zmiennych
Widoczność zmiennej (funkcji lub klasy) zależy od miejsca w którym jest zdeklarowana. 

Aby zmienna była widoczna funkcji należy użyć słowa kluczowego `global` a następnie podać nazwę zmiennej do której chcemy mieć dostęp w obrębie naszej funkcji.

Przykład:
```python
zmienna_globalna = 10


def funkcja():
    global zmienna_globalna
    print(f"Zmienna globalna w funkcji: {zmienna_globalna}")
    zmienna_globalna = 20
    print(f"Zmienna globalna w funkcji po przypisaniu nowej wartości: {zmienna_globalna}")


print(f"Zmienna globalna PRZED wywołaniem funkcji: {zmienna_globalna}")
print("-" * 50)
funkcja()
print("-" * 50)
print(f"Zmienna globalna PO wywołaniem funkcji: {zmienna_globalna}")  
```


## Dekorator funkcji
Dekoratorem funkcji nazywamy funkcję która jako parametr przyjmuje referencje innej funkcji w celu rozszerzenia jej funkcjonalności.

Przykład:

```python
# funkcja power_of_2 przyjmie jako parametr inną funkcję
# a następnie wykorzysta ją wewnątrz funkcji _wrapper
# która wywoła przekazaną funkcję i zmodyfikuje jej wartość
def power_of_2(func):
    def _wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
        return result**2
    return _wrapper


def just_a_number_plus_one(a):
    return a + 1

print(just_a_number_plus_one.__name__)

# tutaj dokonujemy "podmiany"
just_a_number_plus_one = power_of_2(just_a_number_plus_one)

print(just_a_number_plus_one.__name__)

print(just_a_number_plus_one(2))
```

Aby użyć funkcji jako dekorator należy użyć konstrukcji `@` + nazwa funkcji.

Przykład:
```python
def power_of_2(func):
    def _wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
        return result**2
    return _wrapper

@power_of_2
def just_a_number_plus_one(a):
    return a + 1

print(just_a_number_plus_one.__name__)

print(just_a_number_plus_one(2))
```

Dektorator może również działać jak funkcja i przyjmować parametry.

Przykład:
```python
def multiply(by):
    def _wrapper(func):
        def _inner(*args, **kwargs):
            return func(*args, **kwargs) * by
        return _inner
    return _wrapper


@multiply(2)
def add_two_numbers(a, b):
    return a + b
    
    
@multiply(3)
def add_three_numbers(a, b, c):
    return a + b

print(add_two_numbers(3, 2)) 
print(add_three_numbers(1, 2, 3))
```

✏️ Napisz funkcję która przyjmuje jako parametr funkcję. Następnie niech funkcja wywoła przekazaną funkcję w argumencie i zwróci wynik jej działania. 

✏️ Zapoznaj się z https://docs.python.org/3/library/functools.html#functools.wraps, jakie są plusy wykorzystania tego dekoratora?

✏️ Stwórz dekorator dla funkcji (zwracającej liczbę) który będzie sprawdzał czy liczba jest większa od 0, jeżeli tak to ma zwrócić jej pierwiastek (użyj moduł `math` funkcję `sqrt`).

✏️ Stwórz dekorator który dla dowolnej funkcji będzie wyświetlał przed jej wywołaniem wartości argumentów jakie zostały do niej przekazane.

✏️ Napisz dekorator który zrzutuje argumenty funkcji na wskazane typy.

✏️ Napisz dekorator `register` który zapisze udekorowaną funkcję do listy, oraz zwróci tą funkcję spowrotem.

✏️ Napisz dekorator który będzie wyświetlał informację o tym jak długo zajeło wywołanie danej funkcji. Utwórzy kilka różnych funkcji (możesz użyć funkcji `sleep` z modułu `time`).

