# Lab 11

## Tworzenie modułów

## Tworzenie paczek


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
