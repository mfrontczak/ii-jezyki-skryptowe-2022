# Lab 9
## Generatory
Funkcja generatora pamięta swój stan jaki posiadała w poprzednim wywołaniu. Generatory są często wykorzystywane w momencie kiedy przetwarzamy sekwencje które są bardzo długie, a w danym momencie nie interesuje nas jako całość, a jedynie jej elementy.

Do budowy generatora używamy w funkcji słowa kluczowego `yield` zamiast `return`.

Przykład 1:
```python
# przykład bez generatora
def power(arr, n):
  arr2 = []
  for v in arr:
    arr2.append(v ** n)
  return arr2

arr = [1, 2, 3, 4, 5, 6]
arr = power(arr, 2)
print(arr)
```
W powyższym przykładzie fragment `return arr2` zwraca nową listę z elementami podniesionymi do potęgi `n`. W trakcie wywołania `power(arr, 2)` zostaje wywołana funkcja w której iterujemy po wszystkich elementach a na stępnie zwracamy nową listę z wynikiem.

```python
# przykład z generatorem
def power(arr, n):
  for v in arr:
    yield v ** n

arr = [1, 2, 3, 4, 5, 6]
arr = power(arr, 2)
print(arr)
print(list(arr))  # obsługa generatora poprzez zrzutowanie go na listę.
```

W tym przykładzie wywołanie `power(arr, 2)` zwraca generator. To znaczy, że do momentu wykonania na nim iteracji, nie nastąpi zwrócenia żadnej wartości.

Wykorzystanie `yield` w przeciwieństwie do wyrażen listowych, pozwala nam na utworzenie nieskończonego generatora. 

## Zadania

💡 w zadanich wykorzystaj moduł https://docs.python.org/3/library/string.html.

✏️ Utwórz iterator z dowolnego łańcucha znakowego, a następnie przeiteruj po wszystkich jego elementach.

✏️ Stwórz generator który będzie zwracał losowe znaki.

✏️ Stwórz generator który zwróci 3 dowolne wartości, spróbuj wywołać go przy pomocy `next` 4 razy.

✏️ Stwórz generator który będzie przyjmował listę imion, a następnie zwróci każdę pisane dużymi literami. Utwórz generator i wywołaj na listcie (`list`) i na zbiorze (`set`). 

✏️ Zbuduj klasę `SeqSentence`, która przyjmie jako argument zdanie. Następnie zaimplementuj odpowiednie metody specjalne aby można było użyć `in` i `for` na obiekcie klasy - iteracja w pętli for powinna zwracać kolejna słowa z zdania.

✏️ Zbuduj klasę `SeqSentence2`, która przyjmie jako argument zdanie. Następnie zaimplementuj odpowiednie metody specjalne aby można było użyć `for` na obiekcie klasy (wykorzystaj `yield` aby zbudować generator) - iteracja w pętli for powinna zwracać kolejna słowa z zdania.
