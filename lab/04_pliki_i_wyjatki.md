# Lab 4
### Obsługa plików
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

⚠️ Pliki do przykładów znajdują się w katalogu [materiały/lab2](materiały/lab2).

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
