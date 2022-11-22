# Lab 5 - cd.
## Funkcje anonimowe (lambda)
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

## Sortowanie danych

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
