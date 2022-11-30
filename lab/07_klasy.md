# Lab 7

## klasy
Klasa to zdefiniowany zbiór atrybutów i metod . Nowy obiekt stworzony z danej klasy nazywamy **instancją**. Interakcja z pozostałymi obiektami odbywa się przez wcześniej zdefiniowane metody.

### minimalna definicja klasy
Aby zdefiniować klasę należy użyć słowa kluczowego `class`, dowolną nazwę (najlepiej zaczynającą się z dużej litery) oraz dwukropek.
```python
class NazwaKlasy:
    pass
```

Słowo kluczowe `pass` odgrywa tutaj kluczową rolę, w Pythonie nie ma możliwości pozostawienia pustej definicji klasy/funkcji oraz bloku instrukcji.

### Tworzenie instacji z klasy

Przykład:
```python
# Definicja klasy
class Backpack:
    pass
    
arnolds_backpack = Backpack()  # nowa instancja przypisana do zmiennej arnolds_backpack
jimmys_backpack = Backpack()  # kolejna instancja tym razem przypisana do zmiennej jimmys_backpack
```

#### Atrybuty
Atrybutami nazywamy zmienne zdefiniowane w klasie.

Przykład 1:
```python
class Backpack:
    color = None

arnolds_backpack = Backpack()
arnolds_backpack.color = 'Blue'

jimmys_backpack = Backpack()
jimmys_backpack.color = 'Orange'

print(f"Kolor plecaka Jimmiego to {jimmys_backpack.color}")
print(f"Kolor plecaka Arnolda to {arnolds_backpack.color}")
```

Przykład 2:
```python
class Notebook:
    paper_size = 'b4'  # atrybut dostępny dla wszystkich instancji klasy Notebook z domyślną wartością. 
    
    def __init__(self, subject):
        self.subject = subject

arnolds_notebook = Notebook('Matematyka')
jimmys_notebook = Notebook('Fizyka')

print(f"Zeszyt Arnolda formatu {arnolds_notebook.paper_size} służy mu do przedmiotu {arnolds_notebook.subject}")
print(f"Zeszyt Jimmiego formatu {jimmys_notebook.paper_size} służy mu do przedmiotu {jimmys_notebook.subject}")
```

Przykład 3:

Modyfikacja atrybutu `paper_size` ma wpływ tylko na konkretną instancję.
```python
class Notebook:
    paper_size = 'B4'  # atrybut dostępny dla wszystkich instancji klasy Notebook z domyślną wartością. 
    
    def __init__(self, subject):
        self.subject = subject

arnolds_notebook = Notebook('Matematyka')
arnolds_notebook.paper_size = 'A5'

jimmys_notebook = Notebook('Fizyka')

print(f"Zeszyt Arnolda formatu {arnolds_notebook.paper_size} służy mu do przedmiotu {arnolds_notebook.subject}")
print(f"Zeszyt Jimmiego formatu {jimmys_notebook.paper_size} służy mu do przedmiotu {jimmys_notebook.subject}")
```


## Zadania

### Zadanie 1

Zaimplementuj klasę `Pet`:

* Klasa powinna posiadać atrybut `name` do przechowywania jego imienia.
* Klasa powinna posiadać atrybut `age` do przechowywania jego wieku.

### Zadanie 2

Zaimplementuj klasę `Rocket`:

* Rakieta powinna posiadać zmienną `mass`.
* Rakieta powinna posiadać zmienną `fuel`.
* Rakieta powinna definiować funkcję która policzy ile paliwa zostanie zużyte aby wzbić się na wysokość `h`.

### Zadanie 3

Zaimplementuj klasę `Box`:

* Pudełko powinno posiadać zmienną `size` do przechowywania jego rozmiaru (w formie krotki: LENGTH, WIDTH, HEIGHT).
* Ilość obiektów przechowywana przez pudełko, powinna być ograniczona przez jego rozmiar (zmienna `size`). 
* Dodaj metodę `put_in` z parametrem `other_box`, metoda `put_in` powinna sprawdzać czy rozmiar pudełka które chcemy umieścić wewnątrz jest mniejszy od wolnej przestrzeni.


### Zadanie 4

Utwórz klasę `CrazyStrings` która będzie udostęniać następujące metody:
* `__init__` z parametrem `text`.
* `leet` która wyświetli tekst w stylu Leet. (https://pl.wikipedia.org/wiki/Leet_speak).
* `poke` który wyświetli tekst naprzemiennie zmieniając litery na małe i duże. 
* `random` która wyświetli tekst w losowym stylu (dwóch powyższych).

## Metoda statyczna
`@staticmethod` jest wbudowanym dekoratem. 
Metoda statyczna jest powiązana z klasą w której się znajduje i **nie posiada** dostępu do atrybutów klasy. 
Nie jest wymagane podawanie żadnych parametrów. 

```python
from datetime import datetime

class Data:
    def __init__(self, rok, miesiac, dzien):
        self.rok = rok
        self.miesiac = miesiac
        self.dzien = dzien
    
    @staticmethod
    def czy_dzisiejsza(rok, miesiac, dzien):
        dzis = datetime.now()
        return rok == dzis.year and miesiac == dzis.month and dzien == dzis.day


print(Data.czy_dzisiejsza(1997, 7, 18))  # sprawdzi czy podana data jest dzisiejsza.
```

## Metoda klasowa
`@classmethod` jest wbudowanym dekoratem.
Metoda klasowa jest powiązana z klasą w której się znajduje i **posiada** dostęp do jej atrybutów.
Pierwszym parametrem w metodzie klasowej jest (musi być) `cls`, który odnosi się do klasy a nie instancji konkretnego obiektu. 

```python
from datetime import datetime

class Data:
    def __init__(self, rok, miesiac, dzien):
        self.rok = rok
        self.miesiac = miesiac
        self.dzien = dzien
    
    @classmethod
    def dzisiaj(cls):
        dzis = datetime.now()
        return cls(dzis.year, dzis.month, dzis.day)

d = Data.dzisiaj()  # Utworzy nową instancję obiektu z klasy Data z dzisiejszą datą.
```

✏️ Napisz metodę klasy dla klasy `Data` zwracającą nowy obiekt z datą wczorajszą.

✏️ Napisz metodę statyczną dla klasy `Data` zmieniającą datę zapisaną w stringu w formacie USA "MM/DD/YYYY" na format europejski "DD/MM/YYYY". 
