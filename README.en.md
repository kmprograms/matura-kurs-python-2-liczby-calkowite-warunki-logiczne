[Polski](README.md) · **English**

---

# Matura in Computer Science, extended level - Python course, part 2. "Integers and logical conditions"

> ### 🎬 Video walkthrough
> A full step-by-step walkthrough of this material is available on my YouTube channel:
> **[Link to the YouTube video](https://youtu.be/r9y-FW2l82M)**
>
> In the video I show the three kinds of division in Python, checking parity and divisibility with the modulo operator, relational operators, the logical operators `and` and `or`, extracting the digits of a number, and converting seconds into hours, minutes and seconds.

---

## Description

Code for the second video in a series where I cover what a student taking the computer science Matura exam at the extended level should know about Python. In the previous video I went through the script `app-1-pierwszy-program-zmienne.py`, and in this one I move on to `app-2-liczby-calkowite.py`.

The main topic is integers, the data type used most often in the Matura exam. I cover arithmetic operations, including three kinds of division, and then show what information you can get from the remainder of a division. Along the way I introduce the first logical conditions: relational operators and the logical operators `and` and `or`. We will use them with conditional statements and loops in the next parts of the series.

Finally, I show how to extract the digits of a number using integer division and modulo. This topic comes up very often in the Matura exam. The video ends with a short example of converting seconds into hours, minutes and seconds.

## Requirements

- Python 3.8 or newer. The script `app-1-pierwszy-program-zmienne.py` uses the `f"{a = }"` f-string syntax, which is available since that version
- No external dependencies. The scripts do not import any modules

## Running

```bash
git clone https://github.com/kmprograms/matura-kurs-python-2-liczby-calkowite-warunki-logiczne
cd matura-kurs-python-2-liczby-calkowite-warunki-logiczne
```

The script covered in this video:

```bash
python app-2-liczby-calkowite.py
```

The script from the previous video:

```bash
python app-1-pierwszy-program-zmienne.py
```

The programs do not read any input. All values are hard-coded, and the results are printed to the terminal.

## Project structure

| File | Description |
| --- | --- |
| `app-1-pierwszy-program-zmienne.py` | Script from the previous video. First program, variables and their types, f-string formatting, arithmetic operators, swapping variable values, the `end` and `sep` parameters of `print`, type conversion, and the `+=`, `-=` and `*=` operators |
| `app-2-liczby-calkowite.py` | Script covered in this video. Operations on integers, three kinds of division, parity and divisibility, relational operators, the logical operators `and` and `or`, digits of a number, and converting seconds into hours, minutes and seconds |

## Topics covered

### Operations on integers

First I create the variables `a = 29` and `b = 3` and perform basic operations on them. Exponentiation is written with two asterisks `**`.

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

Python has three kinds of division:

| Operator | Kind of division | Example | Result |
| --- | --- | --- | --- |
| `/` | true division | `29 / 2` | `14.5` |
| `//` | integer division (floor division) | `29 // 2` | `14` |
| `%` | remainder of division (modulo) | `29 % 2` | `1` |

True division returns a floating-point number. Integer division cuts off the fractional part of the result. The result `14.5` is not rounded to 15. Even if the fractional part were `.8`, it would simply be cut off. The modulo operator returns the remainder of the division. 29 divided by 2 is 14 whole parts, which gives 28, with a remainder of 1.

### Parity and divisibility

The remainder of a division tells you a lot. The simplest example is checking parity and divisibility:

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

For even numbers `liczba % 2` gives 0, and for odd numbers it gives 1. Checking parity is in fact checking divisibility by 2, and the same rule works for any other divisor. If a number is divisible by 5, `liczba % 5` gives 0. If it is divisible by 8, `liczba % 8` gives 0. In all other cases you get a non-zero remainder.

The result of `% 5` always falls in the range from 0 to 4, that is, from 0 to the divisor minus 1. For consecutive numbers 20, 21, 22 and so on, the remainders repeat in a cycle: 0, 1, 2, 3, 4, 0, 1, 2, 3, 4. When dividing by 7, the values would cycle from 0 to 6.

### The == operator and the first logical conditions

To check whether a number is divisible by 5, you take it modulo 5 and check whether the result is 0. You cannot use a single `=` sign for this, because it is reserved for assigning a value to a variable. Comparison is done with the `==` operator, which checks whether the left-hand side is equal to the right-hand side.

```python
# Operator == i pierwsze warunki logiczne
x = 21
# Chcesz sprawdzić, czy wartość w zmiennej x dzieli się przez 5
print(f"Czy {x} jest podzielne przez 5: {x % 5 == 0}")
y = 25
print(f"Czy {y} jest podzielne przez 5: {y % 5 == 0}")
```

The result of a comparison is a boolean value, either `True` or `False`. For `x = 21` the remainder of division by 5 is 1, and 1 is not equal to 0, so the result is `False`. For `y = 25` the remainder is 0, so the result is `True`. We will use conditions like these once we learn conditional statements.

### The != operator and the other relational operators

The `!=` operator works the opposite way to `==`. It gives `True` if and only if the left-hand side is not equal to the right-hand side. So the expression `y % 5 != 0` checks whether a number is not divisible by 5. For `y = 25` the result is `False`, because 25 is divisible by 5.

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

Summary of the relational operators:

| Operator | Meaning | Expression for `y = 25` | Result |
| --- | --- | --- | --- |
| `==` | equal to | `y % 5 == 0` | `True` |
| `!=` | not equal to | `y % 5 != 0` | `False` |
| `>` | greater than | `y > 10` | `True` |
| `>=` | greater than or equal to | `y >= 10` | `True` |
| `<` | less than | `y < 10` | `False` |
| `<=` | less than or equal to | `y <= 10` | `False` |

### The logical operators and and or

The `and` operator gives `True` only when both conditions hold at the same time. The `or` operator requires at least one of the conditions to be true. If both conditions are false, the whole `or` expression is false as well.

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

The cases from the video:

| `y` | Expression | First condition | Second condition | Result |
| --- | --- | --- | --- | --- |
| 25 | `y % 5 == 0 and y > 10` | `True` | `True` | `True` |
| 5 | `y % 5 == 0 and y > 10` | `True` | `False` | `False` |
| 14 | `y % 7 == 0 or y > 20` | `True` | `False` | `True` |
| 14 | `y % 5 == 0 or y > 20` | `False` | `False` | `False` |
| 14 | `y % 5 == 0 or y > 10` | `False` | `True` | `True` |

### Digits of a number

Extracting and analysing the digits of a number, whatever numeral system it is written in, is one of the topics that come up very often in the Matura exam. For now we work with the digits of a number in the decimal system.

```python
# Cyfry liczby
n = 47218
print(f"Cyfra jedności:   {n % 10}")
print(f"Cyfra dziesiątek: {(n // 10) % 10}")
print(f"Cyfra setek:      {(n // 100) % 10}")
```

The mechanism works like this:

1. The remainder of dividing any number by 10 is its last digit, that is, the units digit
2. Integer division by 10 cuts off the units digit. `47218` becomes `4721`, and the last position now holds the tens digit, which `% 10` extracts
3. Integer division by 100 cuts off the last two digits. What remains is `472`, and `% 10` gives the hundreds digit

| Digit | Expression | Calculation | Result |
| --- | --- | --- | --- |
| units | `n % 10` | `47218 % 10` | 8 |
| tens | `(n // 10) % 10` | `4721 % 10` | 1 |
| hundreds | `(n // 100) % 10` | `472 % 10` | 2 |

The same approach gives you the thousands digit, the ten-thousands digit and so on. Going through the digits of a number in a `while` loop is a topic I cover when teaching algorithms.

### Converting seconds into hours, minutes and seconds

A mini example that combines integer division and modulo:

```python
# Zamiana sekund na godziny, minuty i sekundy
sekundy = 7384
godziny = sekundy // 3600
reszta = sekundy % 3600
minuty = reszta // 60
pozostale_sekundy = reszta % 60
print(f"{sekundy} s = {godziny} h {minuty} min {pozostale_sekundy} s")
```

The steps:

1. An hour has 3600 seconds, so `sekundy // 3600` gives the number of full hours, which is `7384 // 3600 = 2`
2. `sekundy % 3600` is the remainder left for minutes and seconds, which is `184`
3. `reszta // 60` is the number of full minutes, which is `3`
4. `reszta % 60` is the remaining seconds, which is `4`

## Results

After running `app-2-liczby-calkowite.py`, the terminal shows:

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

The values discussed in the video match this output. Dividing 29 by 2 gives `14.5`, `14` and `1` respectively, and 7384 seconds is 2 hours, 3 minutes and 4 seconds.

## Implementation notes

In the first block of `app-2-liczby-calkowite.py`, the labels in the strings read `a ** b`, `a / b`, `a // b` and `a % b`, but the expressions inside the curly braces are `a ** 2`, `a / 2`, `a // 2` and `a % 2`. This matches the explanation in the video, where I square 29 and divide 29 by 2. The variable `b` is used only in addition, subtraction and multiplication.

The results of the operations and logical conditions are evaluated directly inside the curly braces of the f-strings. This lets you print a result straight away without creating an extra variable.

Python prints boolean values as `True` and `False`, with a capital letter.

In the seconds example, the final result is stored in the variable `pozostale_sekundy`, not in `sekundy`. This way `sekundy` keeps its initial value, which is needed later in the message printed by `print`.