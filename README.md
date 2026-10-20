**Polski** · [English](README.en.md)

---

# Matura z informatyki, poziom rozszerzony - kurs Pythona, część 2. "Liczby całkowite i warunki logiczne"

> ### 🎬 Wideo z omówieniem
> Pełne omówienie tego materiału krok po kroku znajdziesz na moim kanale YouTube:
> **[Link do filmu na YouTube](https://youtu.be/r9y-FW2l82M)**
>
> Na filmie pokazuję trzy rodzaje dzielenia w Pythonie, sprawdzanie parzystości i podzielności za pomocą operatora modulo, operatory relacji, spójniki logiczne `and` i `or`, wyznaczanie cyfr liczby oraz zamianę sekund na godziny, minuty i sekundy.

---

## Opis

Kod do drugiego nagrania z serii, w której omawiam to, co maturzysta zdający informatykę na poziomie rozszerzonym powinien wiedzieć o języku Python. W poprzednim nagraniu omawiałem skrypt `app-1-pierwszy-program-zmienne.py`, a w tym przechodzę do skryptu `app-2-liczby-calkowite.py`.

Głównym tematem są liczby całkowite, czyli najczęściej używany typ danych na maturze. Omawiam działania arytmetyczne, w tym trzy rodzaje dzielenia, a potem pokazuję, jakie informacje można wyciągnąć z reszty z dzielenia. Przy okazji wprowadzam pierwsze warunki logiczne: operatory relacji oraz spójniki `and` i `or`. Będziemy z nich korzystać przy instrukcjach warunkowych i pętlach w kolejnych częściach serii.

Na koniec pokazuję, jak wyznaczać cyfry liczby za pomocą dzielenia całkowitego i modulo. To zagadnienie bardzo często pojawia się na maturze. Całość zamyka krótki przykład zamiany sekund na godziny, minuty i sekundy.

## Wymagania

- Python 3.8 lub nowszy. Skrypt `app-1-pierwszy-program-zmienne.py` korzysta z zapisu `f"{a = }"` w f-stringach, który jest dostępny od tej wersji
- Brak zewnętrznych zależności. Skrypty nie importują żadnych modułów

## Uruchomienie

```bash
git clone https://github.com/kmprograms/matura-kurs-python-2-liczby-calkowite-warunki-logiczne
cd matura-kurs-python-2-liczby-calkowite-warunki-logiczne
```

Skrypt omawiany w tym nagraniu:

```bash
python app-2-liczby-calkowite.py
```

Skrypt z poprzedniego nagrania:

```bash
python app-1-pierwszy-program-zmienne.py
```

Programy nie wczytują żadnych danych. Wszystkie wartości są zapisane w kodzie, a wyniki trafiają do terminala.

## Struktura projektu

| Plik | Opis |
| --- | --- |
| `app-1-pierwszy-program-zmienne.py` | Skrypt z poprzedniego nagrania. Pierwszy program, zmienne i ich typy, formatowanie w f-stringach, operatory arytmetyczne, zamiana wartości zmiennych, parametry `end` i `sep` funkcji `print`, zamiana typów oraz operatory `+=`, `-=` i `*=` |
| `app-2-liczby-calkowite.py` | Skrypt omawiany w tym nagraniu. Działania na liczbach całkowitych, trzy rodzaje dzielenia, parzystość i podzielność, operatory relacji, spójniki `and` i `or`, cyfry liczby oraz zamiana sekund na godziny, minuty i sekundy |

## Omawiane zagadnienia

### Działania na liczbach całkowitych

Na początek tworzę zmienne `a = 29` i `b = 3` i wykonuję na nich podstawowe działania. Potęgowanie zapisuje się za pomocą dwóch gwiazdek `**`.

```python
a = 29
b = 3

print(f"a + b = {a + b}")
print(f"a - b = {a - b}")
print(f"a * b = {a * b}")
print(f"a ** b = {a ** 2}")
print(f"a / b = {a / 2}")
print(f"a // b = {a // 2}")
print(f"a % b = {a % 2}")
```

W Pythonie są trzy rodzaje dzielenia:

| Operator | Rodzaj dzielenia | Przykład | Wynik |
| --- | --- | --- | --- |
| `/` | dzielenie rzeczywiste | `29 / 2` | `14.5` |
| `//` | dzielenie całkowite (całkowitoliczbowe) | `29 // 2` | `14` |
| `%` | reszta z dzielenia (modulo) | `29 % 2` | `1` |

Dzielenie rzeczywiste zwraca liczbę zmiennoprzecinkową. Dzielenie całkowite obcina część ułamkową wyniku. Wynik `14.5` nie jest zaokrąglany do 15. Nawet gdyby część ułamkowa wynosiła `.8`, zostałaby po prostu obcięta. Operator modulo zwraca resztę z dzielenia. 29 podzielone przez 2 to 14 całych, czyli 28, i 1 reszty.

### Parzystość i podzielność

Na podstawie reszty z dzielenia można wyciągnąć wiele informacji. Najprostszy przykład to sprawdzanie parzystości i podzielności:

```python
print("Parzystość liczby")
print(f"23 % 2 = {23 % 2}")
print(f"24 % 2 = {24 % 2}")
print(f"25 % 2 = {25 % 2}")
print(f"26 % 2 = {26 % 2}")

print("Podzielność")
print(f"20 % 5 = {20 % 5}")
print(f"21 % 5 = {21 % 5}")
print(f"22 % 5 = {22 % 5}")
print(f"23 % 5 = {23 % 5}")
print(f"24 % 5 = {24 % 5}")
print(f"25 % 5 = {25 % 5}")
```

Dla liczb parzystych `liczba % 2` daje 0, a dla nieparzystych 1. Sprawdzanie parzystości to w praktyce sprawdzanie podzielności przez 2, a ta sama zasada działa dla każdego innego dzielnika. Jeżeli liczba dzieli się przez 5, to `liczba % 5` daje 0. Jeżeli dzieli się przez 8, to `liczba % 8` daje 0. W pozostałych przypadkach dostajesz niezerową resztę.

Wynik operacji `% 5` zawsze mieści się w przedziale od 0 do 4, czyli od 0 do dzielnika pomniejszonego o 1. Dla kolejnych liczb 20, 21, 22 i tak dalej reszty powtarzają się cyklicznie: 0, 1, 2, 3, 4, 0, 1, 2, 3, 4. Przy dzieleniu przez 7 byłyby to cyklicznie wartości od 0 do 6.

### Operator == i pierwsze warunki logiczne

Aby sprawdzić, czy liczba dzieli się przez 5, trzeba wykonać operację modulo 5 i sprawdzić, czy wynik wynosi 0. Nie można do tego użyć pojedynczego znaku `=`, ponieważ jest on zarezerwowany dla przypisania wartości do zmiennej. Do porównania służy operator `==`, który sprawdza, czy lewa strona jest równa prawej.

```python
# Operator == i pierwsze warunki logiczne
x = 21
# Chcesz sprawdzić, czy wartość w zmiennej x dzieli się przez 5
print(f"Czy {x} jest podzielne przez 5: {x % 5 == 0}")
y = 25
print(f"Czy {y} jest podzielne przez 5: {y % 5 == 0}")
```

Wynikiem porównania jest wartość logiczna `True` albo `False`. Dla `x = 21` reszta z dzielenia przez 5 wynosi 1, a 1 nie jest równe 0, więc wynik to `False`. Dla `y = 25` reszta wynosi 0, więc wynik to `True`. Takie warunki wykorzystamy, gdy poznamy instrukcje warunkowe.

### Operator != i pozostałe operatory relacji

Operator `!=` działa odwrotnie niż `==`. Daje `True` wtedy i tylko wtedy, gdy lewa strona nie jest równa prawej. Wyrażenie `y % 5 != 0` sprawdza więc, czy liczba nie jest podzielna przez 5. Dla `y = 25` wynik to `False`, bo 25 dzieli się przez 5.

```python
# Czy lewa strona NIE jest równa prawej stronie?
# Czy wartość w zmiennej y NIE jest podzielna przez 5
print(f"Czy {y} NIE jest podzielne przez 5: {y % 5 != 0}")

# Pozostałe operatory relacji
print(f"Czy {y} jest większa od 10: {y > 10}")
print(f"Czy {y} jest większa lub równa 10: {y >= 10}")
print(f"Czy {y} jest mniejsza od 10: {y < 10}")
print(f"Czy {y} jest mniejsza lub równa 10: {y <= 10}")
```

Zestawienie operatorów relacji:

| Operator | Znaczenie | Wyrażenie dla `y = 25` | Wynik |
| --- | --- | --- | --- |
| `==` | równe | `y % 5 == 0` | `True` |
| `!=` | różne od | `y % 5 != 0` | `False` |
| `>` | większe od | `y > 10` | `True` |
| `>=` | większe lub równe | `y >= 10` | `True` |
| `<` | mniejsze od | `y < 10` | `False` |
| `<=` | mniejsze lub równe | `y <= 10` | `False` |

### Spójniki logiczne and i or

Spójnik `and` daje `True` tylko wtedy, gdy oba warunki są spełnione jednocześnie. Spójnik `or` wymaga, aby co najmniej jeden z warunków był prawdziwy. Jeżeli oba warunki są fałszywe, całe wyrażenie z `or` też jest fałszywe.

```python
# Spójniki logiczne
print(f"Czy {y} jest podzielna przez 5 i większa od 10: {y % 5 == 0 and y > 10}")
y = 5
print(f"Czy {y} jest podzielna przez 5 i większa od 10: {y % 5 == 0 and y > 10}")
y = 14
print(f"Czy {y} jest podzielna przez 7 lub większa od 20: {y % 7 == 0 or y > 20}")
print(f"Czy {y} jest podzielna przez 5 lub większa od 20: {y % 5 == 0 or y > 20}")
print(f"Czy {y} jest podzielna przez 5 lub większa od 10: {y % 5 == 0 or y > 10}")
```

Przypadki z nagrania:

| `y` | Wyrażenie | Pierwszy warunek | Drugi warunek | Wynik |
| --- | --- | --- | --- | --- |
| 25 | `y % 5 == 0 and y > 10` | `True` | `True` | `True` |
| 5 | `y % 5 == 0 and y > 10` | `True` | `False` | `False` |
| 14 | `y % 7 == 0 or y > 20` | `True` | `False` | `True` |
| 14 | `y % 5 == 0 or y > 20` | `False` | `False` | `False` |
| 14 | `y % 5 == 0 or y > 10` | `False` | `True` | `True` |

### Cyfry liczby

Wyznaczanie i analiza cyfr liczby, niezależnie od systemu liczbowego, w którym jest zapisana, to jedno z zagadnień, które bardzo często pojawiają się na maturze. Na razie zajmujemy się cyframi liczby w systemie dziesiętnym.

```python
# Cyfry liczby
n = 47218
print(f"Cyfra jedności:   {n % 10}")
print(f"Cyfra dziesiątek: {(n // 10) % 10}")
print(f"Cyfra setek:      {(n // 100) % 10}")
```

Mechanizm wygląda tak:

1. Reszta z dzielenia dowolnej liczby przez 10 to jej ostatnia cyfra, czyli cyfra jedności
2. Dzielenie całkowite przez 10 obcina cyfrę jedności. Z `47218` zostaje `4721`, a na ostatniej pozycji jest teraz cyfra dziesiątek, którą wyłuskuje `% 10`
3. Dzielenie całkowite przez 100 obcina dwie ostatnie cyfry. Zostaje `472`, a `% 10` daje cyfrę setek

| Cyfra | Wyrażenie | Obliczenia | Wynik |
| --- | --- | --- | --- |
| jedności | `n % 10` | `47218 % 10` | 8 |
| dziesiątek | `(n // 10) % 10` | `4721 % 10` | 1 |
| setek | `(n // 100) % 10` | `472 % 10` | 2 |

Na tej samej zasadzie wyznaczysz cyfrę tysięcy, dziesiątek tysięcy i tak dalej. Przeglądanie cyfr liczby w pętli `while` to temat, który omawiam podczas nauki algorytmów.

### Zamiana sekund na godziny, minuty i sekundy

Miniprzykład, który łączy dzielenie całkowite i modulo:

```python
# Zamiana sekund na godziny, minuty i sekundy
sekundy = 7384
godziny = sekundy // 3600
reszta = sekundy % 3600
minuty = reszta // 60
pozostale_sekundy = reszta % 60
print(f"{sekundy} s = {godziny} h {minuty} min {pozostale_sekundy} s")
```

Kolejne kroki:

1. Godzina ma 3600 sekund, więc `sekundy // 3600` daje liczbę pełnych godzin, czyli `7384 // 3600 = 2`
2. `sekundy % 3600` to reszta, która przypada na minuty i sekundy, czyli `184`
3. `reszta // 60` to liczba pełnych minut, czyli `3`
4. `reszta % 60` to pozostałe sekundy, czyli `4`

## Wyniki

Po uruchomieniu `app-2-liczby-calkowite.py` w terminalu pojawia się:

```
a + b = 32
a - b = 26
a * b = 87
a ** b = 841
a / b = 14.5
a // b = 14
a % b = 1
Parzystość liczby
23 % 2 = 1
24 % 2 = 0
25 % 2 = 1
26 % 2 = 0
Podzielność
20 % 5 = 0
21 % 5 = 1
22 % 5 = 2
23 % 5 = 3
24 % 5 = 4
25 % 5 = 0
Czy 21 jest podzielne przez 5: False
Czy 25 jest podzielne przez 5: True
Czy 25 NIE jest podzielne przez 5: False
Czy 25 jest większa od 10: True
Czy 25 jest większa lub równa 10: True
Czy 25 jest mniejsza od 10: False
Czy 25 jest mniejsza lub równa 10: False
Czy 25 jest podzielna przez 5 i większa od 10: True
Czy 5 jest podzielna przez 5 i większa od 10: False
Czy 14 jest podzielna przez 7 lub większa od 20: True
Czy 14 jest podzielna przez 5 lub większa od 20: False
Czy 14 jest podzielna przez 5 lub większa od 10: True
Cyfra jedności:   8
Cyfra dziesiątek: 1
Cyfra setek:      2
7384 s = 2 h 3 min 4 s
```

Wartości omawiane na nagraniu zgadzają się z tym wydrukiem. Dzielenie 29 przez 2 daje kolejno `14.5`, `14` i `1`, a 7384 sekundy to 2 godziny, 3 minuty i 4 sekundy.

## Uwagi implementacyjne

W pierwszym bloku skryptu `app-2-liczby-calkowite.py` etykiety w napisach mają postać `a ** b`, `a / b`, `a // b` i `a % b`, ale w nawiasach klamrowych obliczane są wyrażenia `a ** 2`, `a / 2`, `a // 2` i `a % 2`. Zgadza się to z omówieniem na nagraniu, gdzie podnoszę 29 do kwadratu i dzielę 29 przez 2. Zmienna `b` bierze udział tylko w dodawaniu, odejmowaniu i mnożeniu.

Wyniki działań i warunków logicznych są obliczane bezpośrednio w nawiasach klamrowych f-stringów. Dzięki temu można od razu wypisać wynik bez tworzenia dodatkowej zmiennej.

Wartości logiczne Python wypisuje jako `True` i `False`, z wielkiej litery.

W przykładzie z sekundami wynik końcowy trafia do zmiennej `pozostale_sekundy`, a nie do `sekundy`. Dzięki temu zmienna `sekundy` zachowuje wartość początkową, która jest potem potrzebna w komunikacie wypisywanym przez `print`.