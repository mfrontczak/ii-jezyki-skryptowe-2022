# Lab 11

## Tworzenie modułów
W Pythonie istnieje wiele standardowych gotowych do użycia modułów. Listę wszystkich modułów można znaleźć [tutaj](https://docs.python.org/3.9/py-modindex.html).

Modułem nazywamy plik python'a (z rozszerzeniem `.py`) który zawiera definicję funkcji, klas lub zmiennych. Najczęściej w module przechowuje się funkcjonalność zgodną z jego przeznaczeniem, na przykład wbudowany moduł `random` przechowuje funkcje związane z losowaniem.

Aby skorzystać udostęnionego kodu przez moduł wykorzystujemy słowo kluczowe `import`, przykład:

Zawartość pliku `my_physics.py`:
```python
def force(mass, acceleration):
    return mass * acceleration


def acceleration(force, mass):
    return force / mass


def mass(force, acceleration):
    return force / acceleration

```

zawartość pliku `calculate_force.py`:
```python
import my_physics  # tutaj informujemy interpreter python'a że chcemy uzyskać dostęp do zawartości pliku my_physics.py (modułu).


if __name__ == "__main__":
    mass = float(input('Podaj masę obiektu: '))
    acce = float(input('Podaj przyśpieszenie: '))
    f = my_physics.force(mass, acce)  # tutaj wywołujemy funkcję force znajdującą się w module my_physics.
    print(f"{mass:.2f} * {acce:.2f} = {f:.2f}")

```

Istnieje również inny sposób na zaimportowanie określonych zmiennych, funkcji lub klas z modułu. W tym celu należy użyć konstrukcji `from ... import ...`, na przykład `from sys import path`.

Przykład 1:

Alternatywna zawartość pliku `calculate_force.py`:
```python
from my_physics import force  # tutaj informujemy interpreter python'a że chcemy uzyskać dostęp do określonej zawartości pliku my_physics.py (modułu).


if __name__ == "__main__":
    mass = float(input('Podaj masę obiektu: '))
    acce = float(input('Podaj przyśpieszenie: '))
    f = force(mass, acce)  # tutaj wywołujemy funkcję force
    print(f"{mass:.2f} * {acce:.2f} = {f:.2f}")
```

Przykład 2:

Alternatywna zawartość pliku `calculate_force.py`:
```python
from my_physics import force, mass


if __name__ == "__main__":
    mass = float(input('Podaj masę obiektu: '))
    acce = float(input('Podaj przyśpieszenie: '))
    f = force(mass, acce)  # tutaj wywołujemy funkcję force
    print(f"{mass:.2f} * {acce:.2f} = {f:.2f}")
    
    # UPS! tutaj dostaniemy błąd, funkcja mass z modułu my_physics zostanie
    # przysłonięta przez zmienną mass (konflikt nazw).
    m = mass(f, acce)  
    print(f"{m:.2f} * {acce:.2f} = {f:.2f}")
```

📖 Proszę przeczytać https://docs.python.org/3.9/reference/import.html, aby dowiedzieć się więcej.


✏️ Stwórz moduł który udostępni funkcje liczącą średnią artmetyczną i średnią geometryczną.

✏️ Stwórz kolejny moduł w którym znajdą się funkcję do liczenia odchylenia standardowego. 

✏️ Napisz skrypt który wykorzysta funkcje z poprzednio utworzonych modułów. Użytkownik powinien móc wprowadzić dane z klawiatury.

## Paczka

Zbiór modułów(i nie tylko) które chcemy udostępnić w ramach naszej paczki.

### Tworzenie paczki

* Stwórz folder o dowolnej nazwie: np. `up_krakow`.
* Utwórz pusty plik `__init__.py`
* Utwórz moduły które chcesz udostępnić np. `lab01.py`

### Importowanie
Następnie aby z importować utworzoną paczkę znajdującą się w tym samym folderze głównym:

```python
from .up_krakow.lab01 import zad1  # import relatywny

zad1()
```

📖 Proszę przeczytać https://www.geeksforgeeks.org/python-packages/, aby dowiedzieć się więcej.

## Publikacja paczki w publicznym repozytorium

https://pypi.org/account/register/


## Środowiska wirtualne
Środowiskiem wirtualnym w pythonie nazywamy odseparowane od siebie instancje pythona - okrojone kopie środowiska bazowego. 
Pozwala nam to na równocześną współpracę nad różnymi pod względem modułów i wersji projektami. 

Dzięki zastosowaniu wirtualnych środowisk jesteśmy w stanie ograniczyć problem z zależnościami bibliotek które mogą uniemożliwić nam uruchomienie naszego skryptu bądź programu. Problem ten uzyskał nawet własną nazwę ["Piekło zależności"](https://pl.wikipedia.org/wiki/Piek%C5%82o_zale%C5%BCno%C5%9Bci).

Do zarządzania pakietami wykorzystujemy narzędzie `pip`, które jest dostarczane wraz z instalacją python'a.

### :memo: Lista przydatnych komend

lista zainstalowanych modułów:
```bash
pip list
```
lista zainstalowanych modułów w składni dla komendy `pip install -r`.
```bash
pip freeze > requirements.txt  # zapisujemy informację zainstalowanych modułach do pliku requirements.txt
```

instalacja nowego modułu:
```bash
pip install [--user] [-U] nazwa_pakietu[==konkretna wersja]
pip install -r requirements.txt   # instalujemy listę pakietów które znajdują się w pliku requirements.txt
```

Usunięcie modułu z środowiska:
```bash
pip uninstall nazwa_pakietu
pip uninstall -r requirements.txt  # usunie listę pakietów które znajdują się w pliku requirements.txt
```

## Tworzenie przy pomocy modułu venv
Aby utworzyć nowe środowisko należy użyć modułu `venv`, który jest integralną częścią pythona 3.X.

### Tworzenie nowego środowiska
Do stworzenia nowego środowiska wykorzystujemy następującą komendę:
```cmd
python -m venv venv
```
### Aktywacja środowiska
W systemie linux/macos:
```cmd
venv/bin/activate
```

W systemie Windows:
```cmd
venv/Scripts/activate
```

## Zarządzanie paczkami
Istnieją również inne narzędzia do zarządzania wirtualnymi środowiskami takie jak `pipenv`, `virtualenv`, `conda`.

📖 Proszę przeczytać https://github.com/pypa/pipenv.

📖 Proszę przeczytać https://virtualenv.pypa.io/en/latest/.

📖 Proszę przeczytać https://docs.python.org/3.9/tutorial/venv.html.

📖 Proszę przeczytać https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html

## Zadania

✏️ Znajdź na internecie (na githubie) dowolne repozytorium kodu w Pythonie i spróbuj stworzyć środowisko potrzebne do jego developmentu.

✏️ Utwórz nowe środowisko w którym zainstalujesz biblioteki: 
 * `ipython`
 * `pandas`
 * `numpy`
 * `matplotlib`
 * `plotly`
 * `streamlit`
 * `opencv-python`
 * `tensorflow`

Użyj w tym celu narzędzia `pip`.

✏️ Wyekportuj zainstalowane biblioteki w nowo utworzonym środwisku do pliku `requirements.txt`.

✏️ Utwórz kolejne środowisko tym razem z wykorzystaniem pliku `requirements.txt`.

✏️ Utwórz nowe środowisko w którym zainstalujesz https://github.com/jazzband/pip-tools. Użyj narzędzi `pip-compile` i `pip-sync` (🔍 sprawdź dokumentacje na stronie) do zbudowania środowiska na potrzeby NLP (Natural Language Processing) zawierającego następujące biblioteki:

* `ipython`
* `jupyter`
* `scikit-learn`
* `matplotlib`

✏️ Jaka jest różnica między narzędziami `pip` a `pip-tools`? Który Twoim zdaniem jest lepszy?
