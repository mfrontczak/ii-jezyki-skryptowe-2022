# Lab 4
## Wyrażenia listowe i generatorowe
### Generator
Generator pozwala nam na użycie wyrażeń ktore zachowują się jak 📖 [iterator](https://pl.wikipedia.org/wiki/Iterator). Funkcja generatora pamięta swój stan jaki posiadała w poprzednim wywołaniu. Generatory są często wykorzystywane w momencie kiedy przetwarzamy sekwencje które są bardzo długie, a w danym momencie nie interesuje nas jako całość, a jedynie jej elementy. Do obsługi generatorów używamy funkcji wbudowanej `next`.

:book: Proszę przeczytać https://docs.python.org/3.9/library/functions.html#next, aby dowiedzieć się więcej.

Przykład 1:
```python
import random
genr = ( (i, random.randint(1, 100)) for i in range(100) )
type(genr)

print(next(genr))
print(next(genr))
print(next(genr))
```

Przykład 2:
```python
import random
genr = ( (i, random.randint(1, 100)) for i in range(100) )
type(genr)

for (i, r) in genr:
    print(f"{i}-te wywołanie generatora, zwróciło losową wartość {r}")
    
```

✏️ Stwórz generator który będzie zwracał kolejne litery alfabetu.

✏️ Zapoznaj się z modułem [random](https://docs.python.org/3.9/library/random.html), Korzystając z funkcji `random.choice`, napisz generator który będzie zwracał losowe alfa-numeryczne znaki.

✏️ Spytaj użytkownika o to jak długie powinno być wygenerowane hasło, a następnie wykorzystaj wcześniej utworzony generator do wygenerowania losowego hasła dla użytkownika. 


#### Generator listy

Przykład:
```python
arr = []
for x in range(10):
    arr.append(x % 3)
print(arr)
```
Powyższy kod, można zastąpić przez generator wyrażenia listowego:
```python
arr = [x % 3 for x in range(10)]
print(arr)
```

### Filtrowanie

Funkcja wbudowana `filter(func, iter)` zwraca iterator elementów dla których `func` zwróci `True`. 

Przykład z wykorzystaniem funkcji `filter`:
```python
def only_even(value):
    return value % 2 == 0
    
arr = [1, 5, 3, 4, 2, 7, 8, 9, 10, 12, 11, 16, 14]

print(f"Nasza lista przed zastosowaniem filtra: {arr}")

filtered_arr = list( filter(only_even, arr) )

print(f"Nasza lista po zastosowaniu filtra:{filtered_arr}")
```

Przykład filtrowania danych z wykorzystaniem pętli for:
```python
arr = [1, 5, 3, 4, 2, 7, 8, 9, 10, 12, 11, 16, 14]

print(f"Nasza lista przed zastosowaniem filtra: {arr}")

filtered_arr = []
for value in arr:
    if value % 2 == 0:  # if only_even(value):
        filtered_arr.append(value)
        
print(f"Nasza lista po zastosowaniu filtra:{filtered_arr}") 
```

Bardziej eleganckim i zgodnym z Pythonem sposobem filtrowanie listy, jest wykorzystanie generatora wyrażeń listowych.

Przykład:
```python
arr = [1, 5, 3, 4, 2, 7, 8, 9, 10, 12, 11, 16, 14]

print(f"Nasza lista przed zastosowaniem filtra: {arr}")

filtered_arr = [value for value in arr if value % 2 == 0]

print(f"Nasza lista po zastosowaniu filtra:{filtered_arr}")
```

<!-- 
### Transformacja danych

```python
arr = [1, 5, 3, 4, 2, 7, 8, 9, 10, 12, 11, 16, 14]

powered_arr = [x**2 for x in arr] 
-->

### Funkcje anonimowe (lambda)
Przy pomocy słowa kluczowego `lambda` definiujemy jedno-wierszową funkcję z kodem. 
Funkcje anonimowe mają zastosowanie w momencie kiedy chcemy przekazać proste wyrażenie jako parametr do innej funkcji np. `sorted`.

Przykład 1:
```python
# takiej funkcji nie da się wywołać poprzez nazwę
lambda x: x**2
# Sposób jednorazowego wywołania
(lambda x: x**2)(10)
```
Przykład 2:
```python
# niby-anonimowa, bo nazwana
pow = lambda x: x**2
print(pow(2))
```

Przykład 3:
```python
d = {
    'klucz1': 2,
    'klucz2': 4,
    'klucz3': 3,
    'klucz4': 1
}
print(sorted(d))
print(sorted(d.items()))

print(sorted(d.items(), key=lambda item: item[0]))
```

### Sortowanie danych

Przykład 1:
```python
arr = [1, 4, 5, 6, 1, 3, 4, 7, 8]
print(sorted(arr))
print(sorted(arr, reverse=True))
```

Przykład 2:
```python
words = ["ala", "ma", "kota", "i", "psa"]
print(sorted(words))
print(sorted(words, reverse=True))
```

:book: Proszę przeczytać https://docs.python.org/3.9/library/functions.html#sorted, aby dowiedzieć się więcej.
