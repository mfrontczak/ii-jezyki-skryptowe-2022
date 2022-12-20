# Lab 10
## Wyrażenia regularne 
Wyrażenia regularne są mini językiem programowania który pozwala nam na tworzenie wzorców dopasowania. 
Modułem odpowiedzialny za udostęnienie funkcjonalności dla wyrażeń regularnych jest `re`.

📖 Proszę przeczytać https://docs.python.org/3/library/re.html.

📖 Proszę przeczytać https://pl.wikipedia.org/wiki/Wyrażenie_regularne.

### meta-znaki 
Meta-znaki posiadają specjalne przeznaczenie w wyrażeniach regularnych. 

| token/meta-znak  | Przeznaczenie | Przykład |
| ------------- | ------------- | ------------- |
| $  | kończy się ...  |  "python$" |
| ^  | zaczyna się od ...   | "^Programowanie" |
| .  | dowolny znak | ".ot" |
| \*  | dopasowanie zachłanne | "\*" |
| + | wyrażenie występuje 1 lub więcej razy | "\[a-z\]+" |
| ? | wyrażenie występuje 0 lub 1 raz | "kot?" |
| {m} | wyrażenie musi być dokładnie `m` razy dopasowane | "\[abc\]{5}" |
| {n,m} | wyrażenie musi być dopasowane od `n` do `m` razy | "\a{3,5}" |
| {n,} | wyrażenie musi być dopasowane `n` lub więcej razy | "\a{3,}" |
| \d | dopasowuje liczby | "\d?" |
| \D | dopasowuje wszystko prócz liczb | "\D+" |
| \s | dopasowuje białe znaki | "\s+" |
| \S | dopasowuje nie-białe znaki | "\S+ \S+" |
| \w | dopasowuje dowolne słowo | "\w" |
| \W | dopasowuje wszystko prócz słów | "\W+" |
| [] | któryś z znaków opisanych w nawiasach kwadratowych | "\[abc\]" |
| \[a-z\] | zakres znaków od a-z | "\[a-z\]+" |
| (...) | przechwyć wszystko co jest zawarte w nawiasach | "(\d)+" |
| a\|b  | dopasowuje `a` lub `b` | "(kot\|pies)" |

### Flagi
| Flaga         | Opis
| ------------- | ------------------------- |
| re.IGNORECASE | ignoruje wielkość znaków. |
| re.MULTILINE | Wyszukanie w wielu liniach. |
| re.ASCII | Tylko znaki ASCII, znaki UNICODE są ignorowane. |
| re.DOTALL | Dopasowuje dowolny znak, nawet jeżeli jest to znak nowej linii. |

📖 Proszę przeczytać https://pl.wikipedia.org/wiki/Wyra%C5%BCenie_regularne#Wyra%C5%BCenia_zach%C5%82anne.

### Funkcja search
Funkcja `re.search(pattern, string, flags=0)` zwraca pierwszy zgodny z wzorcem łańcuch znakowy. 
Funkcja zwraca obiekt `re.Match` lub `None`.

Przykład 1:
```python
import re
p = '[a-z\.]+'
s = '-!!michal.frontczak(at)up.krakow.pl% %lub% %michal.frontczak@up.krakow.pl!!-'
r = re.search(p, s)
print(result.group()) # michal.frontczak
```

Przykład 2:
```python
import re
p = '.ome.'
s = 'domek'
r = re.search(p, s)
print(r.group())


s = 'Tomek'
r = re.search(p, s)
print(r.group())

s = 'Kometa'
r = re.search(p, s)
print(r.group())
```

Przykład 3:
```python
import re
p = 'kot? kot'
s = 'kotek kot'
r = re.search(p, s)
if r:
    print(r.group())
else:
    print("brak wyników")
```

Przykład 4:
```python
import re
p = '(\S+) (\S+)'
s = 'Peter Snake'
r = re.search(p, s)
print(r.groups()) # zwróć uwagę na groups
```

### Funkcja findall
Funkcja `re.findall(pattern, string, flags=0)` zwraca listę dopasowań.

Przykład 1:
```python
import re
p = '[abc]{3}'
s = 'abc a-a-a ccc bb5b ddd aaa'
print(re.findall(p, s))
```
Przykład 2:
```python
import re
p = 'a{3,5}'
s = 'a aa aaa aaaa aaaaa aaaaaa aaaaaaa'
print(re.findall(p, s))
```

Przykład 3:
```python
import re
p = '(kot.|pies)'
s = 'kot pies tok siep kotopies'
print(re.findall(p, s))
```

### Kompilowanie wzorca
Kiedy pracujemy na bardzo dużej ilości danych warto skorzystać z `re.compile(pattern, flags=0)`. 

Przykład 1:

```python
import re

p = re.compile('kot*')

print(p.match("kotek"))
print(p.match("piesek"))
print(p.match("kot"))

r = p.match("koteczek")

print(r.group())
```

Przykład 2:
```python
import re
p = re.compile(r'\d+')
r = p.findall("Dopasuj cyfry 12, 13, 14 z tekstu")
if m:
    print('Znalezione: ', r)
else:
    print('Brak')
```

📖 Proszę przeczytać https://docs.python.org/3.9/howto/regex.html aby dowiedzieć się więcej.

### Zadania

✏️ Napisz regułę pozwalającą na dopasowanie adresu e-mail.

✏️ Napisz regułę pozwalającą na dopasowanie numeru telefonu.

✏️ Napisz skrypt który z wykorzystaniem wyrażeń regularnych znajdzie wszystkie funkcje i klasy w pliku `.py`.

✏️ Napisz regułę pozwalającą na dopasowanie wydobycie protokołu, domeny, i adresu z linku do strony www. np. https://ii.up.krakow.pl/aktualnosci/ -> ('https', 'ii.up.krakow.pl' , '/aktualnosci/')

✏️ Napisz regulę pozwalającą na wyciągnięcie wszystkich odmian Polska z 
`'Witaj Polsko, Polska to piękny kraj. W Polsce żyje bardzo dużo ludzi. "Hello" oznacza "Cześć" po polsku.'`.

✏️ Wczytaj plik `maile.html` z [materiały/lab10](materiały/lab10). Przygotuj regułę dopasowania pozwalającą na znalezienie wszystkich adresów email w pliku HTML.
