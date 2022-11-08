# Lab 4
## Obsługa plików
Do obsługi plików otwarcia(r)/zapisu(w)/nadpisania(a) służy funkcja `open`. Funkcja `open` działa również z wyrażeniem `with`. 

Przykład:
```python
f = open('plik.txt')
# data = f.read()
# lines = f.readline()
for line in f:
  print(line)
f.close()
```

Przykład z `with`:

```python
with open('plik.txt') as f:
    # data = f.read()
    # lines = f.readline()
    for line in f:
      print(line)
```

✏️ Utwórz plik tekstowy a następnie wczytaj go do swojego programu przy użyciu różnych metod.

:book: Proszę przeczytać https://docs.python.org/3.9/library/functions.html#open, aby dowiedzieć się więcej.

### Serializacja obiektów
Serializacja to proces polegający na przekształceniu obiektów na format danych pozwalających nam na zapisanie i późniejsze odtworzenie danych z pliku, bazy danych lub pamięci komputera.

⚠️ Pliki do przykładów znajdują się w katalogu [materiały/lab04](materiały/lab04).

#### JSON
Wczytywanie danych z pliku o formacie JSON.

przykład:
```python
import json

# Wczytywanie pliku w formacie JSON do pythona
f = open('uczelnie.json', encoding='utf-8')
content = f.read()
uczelnie = json.loads(content)
# Otrzymujemy strukturę danych zgodną z python'em
print(uczelnie)
f.close()
```

Zapisywanie danych do pliku o formacie JSON.

przykład:
```python
import json

data = {
  'name': 'Guido van Rossum',
  'age': 65,
  'faviourite_movies': [
    'Żywot Briana',
    'Monty Python i Święty Graal',
    'Monty Python: Prawie prawda'
  ]
}

jsonized = json.dumps(data)

f = open('guido_data.json', mode='w', encoding='utf-8')
f.write(jsonized)
f.close()
```

✏️ Stwórz bibliotekę filmów. Napisz skrypt w którym użytkownik będzie mógł dodawać filmy do pliku w formacie json. Użytkownik powinien móc wprowadzać nazwy filmów wraz z ich średnią oceną (z dowolnego serwisu) i rokiem wydawania, aż do momentu nie wprowadzenia tytułu filmu przez użytkownika.

:book: Proszę przeczytać https://docs.python.org/3/library/json.html, aby dowiedzieć się więcej.

#### CSV

Wczytywanie danych z pliku CSV.

Przykład:
```python
import csv

# Wczytywanie danych z pliku CSV
f = open('ciasta.csv', encoding='utf-8')
reader = csv.reader(f, delimiter=';')
for row in reader:
    name, prep_time = row
    print(f"Ciasto *{name}* przygotowuje się *{prep_time}* minut.")
f.close()
```

Zapisywanie danych do pliku CSV.
```python
import csv

# Zapisywanie danych do pliku CSV
f = open('miasta.csv', mode='w', encoding='utf-8')
writer = csv.writer(f, delimiter=';')
writer.writerow(['Kraków', 766000])
writer.writerow(['Wrocław', 638000])
writer.writerow(['Warszawa', 1765000])
f.close()
```
✏️ Napisz skrypt w którym użytkownik będzie mógł dodawać studentów do pliku w formacie csv. Skrypt powinien spytać użytkownika ilu studentów chce dodać a następnie w petli poprosić użytkownika o numer albumu i ocene końcową.

:book: Proszę przeczytać https://docs.python.org/3/library/csv.html, aby dowiedzieć się więcej.

## Wyjątki
Wyjątkiem nazywamy często zdarzenie w wyniku którego nasz skrypt lub program nie działa prawidłowo. Kiedy skrypt zgłosi wyjątek interpreter przerwie jego wykonanie i poinformuje o błędzie użytkownika. Na szczęście w języku Python jak i wielu innych językach programowania istnieje mechanizm służący przechwytywaniu wyjątku przez programistę i obsługi tego zdarzenia.

W celu przechwycenia wyjątku w naszym skrypcie używamy konstrukcji `try` `except`.

Przykład 1: zwracający wyjątek:
```python
f = open('nie_istniejacy.txt')
```

Przykład 2: zwracający wyjątek:
```python
i = int('pietnaście')
```

Przykład 1: obsługujący wyjątek:
```python
try:
    f = open('nie_istniejacy.txt')
except:   # przechwytujemy wszystkie wyjątki.
    print("Podany plik nie istnieje lub nie masz uprawnień do odczytu.")
```

Przykład 2: obsługujący wyjątek:
```python
try:
    i = int('pietnaście')
except ValueError as err:
    print(err)
```

Oczywiście użycie konstrukcji `except` bez podania typu wyjątku który chcemy obsłużyć, będzie przechwytywać wszystkie możliwe wyjątki. W wypadku kiedy chcemy przechwycić konkretny wyjątek należy po `except` podać jego nazwę (jak w przykładzie 2). 

Konstrukcja `except ... as e` pozwala nam na uzyskanie dostępu do informacji o wyjątku zwróconym przez interpreter.

### Przechwytywanie wielu wyjątków
Python umożliwia nam zdefiniowanie w jednym wierszu `except` wielu wyjątków jakie chcemy obsłużyć.

Przykład:
```python
try:
    import foobar
    foobar.value
except (ModuleNotFoundError, ImportError) as e:
    # jakaś obsługa błędu ModuleNotFoundError lub ImportError
except (FileNotFoundError, IOError, OSError) as e:
    # jakaś obsługa błędu FileNotFoundError lub IOError lub OSError
```

📖 Proszę przeczytać https://docs.python.org/3.9/library/exceptions.html, aby dowiedzieć się więcej.

📖 Proszę przeczytać https://docs.python.org/3.9/library/exceptions.html#exception-hierarchy, aby dowiedzieć się więcej.

📖 Proszę przeczytać https://docs.python.org/3.9/tutorial/errors.html, aby dowiedzieć się więcej.

✏️ Z listy dostępnych wyjątków wybierz jeden a następnie użyj go wraz z składnią `raise` do wywołania wyjątku. Napisz skrypt który obsłuży wyjątek - w dowolny sposób.

✏️ Napisz skrypt który będzie odpytywał użytkownika o jego wiek, aż do momentu kiedy wprowadzi poprawne dane. (użyj pętli `while True`)
