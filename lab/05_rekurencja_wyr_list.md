# Lab 5
## Rekurencja
Funkcja która wywołuję samą siebie nazywamy funkcją rekurencyjną. Do prawidłowego działania potrzebny jest warunek stopu który pozwoli nam opuścić rekurencję. 

Przykład:
```python
def r_sum(arr):
  if len(arr) > 1:
    return arr[0] + r_sum(arr[1:])
  else:
  return arr[0]


print(r_sum([1,2,3,4,5,6]))
```

✏️ Napisz skrypt który policzy potęgę używając rekurencji dla liczby 2 podniesionej do potęgi 8 i dla liczby 1 podniesionej do potęgi 1001.

## wyrażenia listowe

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

### Transformacja danych
```python
arr = [1, 5, 3, 4, 2, 7, 8, 9, 10, 12, 11, 16, 14]

powered_arr = [x**2 for x in arr] 
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

✏️ Napisz skrypt w którym utworzyć dwie listy przy pomocy wyrażeń listowych.

✏️ Napisz skrypt w którym zbudujesz macierz 4x4 korzystając z wyrażeń listowych.

✏️ Napisz skrypt w którym podniesiesz do potęgi wartości w poprzedniej macierzy.

✏️ Napisz skrypt w którym wygenerujesz listę 100 liczb, nie będącymi liczbami pierwszymi. 

✏️ Napisz skrypt w którym użytkownik poda listę imion a następnie listę liter które posłużą jako filtr. Wszystkie podane litery powinny znajdować się w imieniu. 
