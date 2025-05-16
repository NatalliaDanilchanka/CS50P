# HarvardX CS50P's Introduction to Programming with Python

This repo contains the solution to the problem sets.

- [Week 0: Functions, Variables](#week-0-functions-variables)
- [Week 1: Conditionals](#week-1-conditionals)
- [Week 2: Loops](#week-2-loops)
- [Week 3: Exceptions](#week-3-exceptions)
- [Week 4: Libraries](#week-4-libraries)
...
- Week 9:

### Week 0: Functions, Variables

Link to Problem Set 0: https://cs50.harvard.edu/python/2022/psets/0/

**Indoor Voice**
```python
x = input("Please enter a string:").lower()
print(x)
```

**Playback Speed**
```python
x = input("Please provide the input: ").replace(" ", "...")
print(x)
```

**Making Faces**
```python
def convert(x):
    return x.replace(":)","🙂").replace(":(","🙁")

def main():
    x = input("Please enter the string:")
    print(convert(x))

main()
```

**Einstein**
```python
c = 300000000
m = int(input("Please enter mass in kg: "))

print(c**2*m)
```

**Tip Calculator**
```python
def main():
    dollars = dollars_to_float(input("How much was the meal? "))
    percent = percent_to_float(input("What percentage would you like to tip? "))
    tip = dollars * percent
    print(f"Leave ${tip:.2f}")

def dollars_to_float(d):
    return float(d.replace("$",""))

def percent_to_float(p):
    return float(p.replace("%",""))/100

main()
```

***

### Week 1: Conditionals

Link to Problem Set 1: https://cs50.harvard.edu/python/2022/psets/1/

Deep Thought
```python
x = input("What is the Answer to the Great Question of Life, the Universe, and Everything? ").strip()
if x == "42":
    x = 42
else:
    x = x.lower()

if x == 42 or x == "forty-two" or x == "forty two":
    print("Yes")
else:
    print("No")
```

Home Federal Savings Bank
```python
x = input("Greeting: ").lower().replace(",","").strip()
x = x.split(" ")

if x[0] == "hello":
    print("$0")
elif x[0][0] == "h":
    print("$20")
else:
    print("$100")
```

File Extensions
```python
x = input("File name: ").replace("jpg","jpeg").strip().lower().split(".")
end = x[-1]

match end:
    case "gif" | "jpg" | "jpeg" | "png" :
        print(f"image/{end}")
    case "pdf" | "zip":
        print(f"application/{end}")
    case "txt" :
        print(f"text/{end}")
    case _:
        print("application/octet-stream")
```

Math Interpreter
```python
x, y, z = input("Expression: ").split(" ")
x = float(x)
z = float(z)

if y == "+":
    print(x + z)
elif y == "-":
    print(x - z)
elif y == "*":
    print(x * z)
else:
    print(x / z)
```

Meal Time
```python
def main():
    x = input("What time is it? ")
    time = convert(x)
    if 7 <= time <= 8:
        print("breakfast time")
    elif 12 <= time <= 13:
        print("lunch time")
    elif 18 <= time <= 19:
        print("dinner time")

def convert(time):
    i, d = time.split(":")
    i = int(i)
    d = int(d)

    d = d/60
    return float(i + d)

if __name__ == "__main__":
    main()
```

### Week 2: Loops
camelCase
```python
# Camel case to snake case
name = input("camelCase:")

for ltr in name:
    if ltr.isupper():
        ltr = ltr.lower()
        print(f"_{ltr}", end = "")
    else:
        print(ltr, end="")
```

Coke Machine
```python
due = 50
print(f"Amount Due: {due}")


while due > 0:
    x = int(input("Insert Coin: "))
    if x == 5 or x == 10 or x == 25:
        due -= x
        if due > 0:
            print(f"Amount Due: {due}")
        else:
            print(f"Change Owed: {abs(due)}")
    else:
        print(f"Amount Due: {due}")
```

Just setting up my twttr
```python
x = input("Input: ")

for ltr in x:
    if ltr.lower() not in ("a", "e", "i", "o", "u"):
        print(ltr, end = "")
print()
```

Vanity Plates
```python
def main():
    plate = input("Plate: ")
    if is_valid(plate):
        print("Valid")
    else:
        print("Invalid")

def is_valid(s):
    n = 0
    if 2 <= len(s) <= 6:   ## check lenght
        if s[0:2].isalpha():  ## check first 2 variables are letters
            for i in s:     ## check that numbers only at the end
                if i.isnumeric():
                    n += 1
            if s[0: len(s) - n].isalpha():
                if n != 0 and int(s[len(s) - n]) != 0:
                    return True
                elif n == 0:
                    return True

main()
```

Nutrition Facts
```python
fruits = {
    "apple": 130,
    "avocado": 50,
    "banana": 110,
    "cantaloupe": 50,
    "grapefruit": 60,
    "grapes": 90,
    "honeydew melon": 50,
    "kiwifruit": 90,
    "lemon": 15,
    "lime": 20,
    "nectarine": 60,
    "orange": 80,
    "peach": 60,
    "pear": 100,
    "pineapple": 50,
    "plums": 70,
    "strawberries": 50,
    "sweet cherries": 100,
    "tangerine": 50,
    "watermelon": 80
}
x = input("Item: ").lower()
if x in fruits.keys():
    print("Calories: ", fruits[x])
```


### Week 3: Exceptions

Fuel Gauge
```python
while True:
    try:
        x, y = input("Fraction: ").split("/")
        x = int(x)
        y = int(y)
        if x > y:
            continue
        fuel = x / y
        break
    except ValueError:
        pass
    except ZeroDivisionError:
        pass

if fuel <= 0.01:
    print("E")
elif fuel >= 0.99:
    print("F")
else:
    fuel = round(fuel * 100)
    print(f"{fuel}%")
```

Felipe’s Taqueria
```python
def get_price(dish):
    meny = {
        "Baja Taco": 4.25,
        "Burrito": 7.50,
        "Bowl": 8.50,
        "Nachos": 11.00,
        "Quesadilla": 8.50,
        "Super Burrito": 8.50,
        "Super Quesadilla": 9.50,
        "Taco": 3.00,
        "Tortilla Salad": 8.00
    }
    if dish in meny:
        return meny[dish]
    else:
        return 0

def main():
    n = 0
    while True:
        try:
            item = input("Item: ").strip().title()
            n += float(get_price(item))
            print(f"Total: ${n:.2f}")
        except EOFError:
            break

main()
```

Grocery List
```python
gr_list= {}

while True:
    try:
        x = input().upper()
        if x in gr_list:
            gr_list[x] += 1
        else:
            gr_list.update({ x : 1 } )

    except EOFError:
        break
gr_list = dict(sorted(gr_list.items()))

for i in gr_list:
    print(gr_list[i], i)
```

Outdated
```python
calendar = [
    "January",
    "February",
    "March",
    "April",
    "May",
    "June",
    "July",
    "August",
    "September",
    "October",
    "November",
    "December"
]
while True:
    date = input("Date: ")
    mm, dd, yyyy = date.strip().replace("/", " ").replace(", "," ").split(" ")

    if "/" in date:
        try:
            dd = int(dd)
            mm = int(mm)
        except:
            date = input("Date: ")
            mm, dd, yyyy = date.strip().replace("/", " ").replace(", "," ").split(" ")
    else:
        if "," not in date:
            date = input("Date: ")
            mm, dd, yyyy = date.strip().replace("/", " ").replace(", "," ").split(" ")
        else:
            try:
                mm = int(mm)
            except:
                mm = calendar.index(mm) + 1
            try:
                dd = int(dd)
            except:
                date = input("Date: ")
                mm, dd, yyyy = date.strip().replace("/", " ").replace(", "," ").split(" ")

    if int(mm) > 12 or int(dd) > 31:
        pass
    else:
        break
print(f"{yyyy}-{mm:02}-{int(dd):02}")
```



### Week 4: Libraries

Emojize
```python
import emoji
word = input("Inpit: ")
print("Output: " + emoji.emojize(word, language="alias" ))
```

Frank, Ian and Glen’s Letters
```python
from pyfiglet import Figlet
import sys
import random

textFont = sys.argv[1:]
figlet = Figlet()

if len(textFont) == 0:
    randfont = random.choice(figlet.getFonts())
    figlet.setFont(font = randfont)
    text = input()
    print(figlet.renderText(text))

elif len(textFont) == 2:
    #slised without file name
    if textFont[0] == "-f" or textFont[0] == "--font" and textFont[1] in figlet.getFonts():
        text = input()
        figlet.setFont(font = textFont[1])
        print(figlet.renderText(text))

    else:
        sys.exit("Invalid usage")
else:
    sys.exit("Invalid usage")
```

Adieu, Adieu
```python
names = []
intro = "Adieu, adieu, to "
while True:
    try:
        names.append(input())
    except EOFError:
        break

if len(names) == 1:
    print(intro + names[0])
elif len(names) == 2:
    print(intro + names[0] + " and " + names[1])
else:
    n = 0
    print(intro, end = "")
    while n < len(names) - 1:
        print( names[n], end = ", ")
        n += 1
    print("and " + names[-1])
```

Guessing Game
```python
from random import randrange

level = 0
while level <= 0:
    level = input("Level: ")
    try:
        level = int(level)
    except ValueError:
        level = int(input("Level: "))

n = randrange(1, level)
try:
    guess = int(input("Guess: "))
except ValueError:
    guess = int(input("Guess: "))

while n != guess:
    if n < guess:
        print("Too large!")

    else:
        print("Too small!")
    try:
        guess = int(input("Guess: "))
    except:
        pass

print("Just right!")
```

Little Professor
```python
import random
from numpy import nan

def main():
    level = get_level()
    generate_integer(level)

def get_level():
    n = nan
    while True:
        n = input("Level: ")
        if n.isdigit():
            if int(n) == 1 or int(n) == 2 or int(n) == 3:
                return int(n)
            else:
                n = input("Level: ")
        else:
            n = input("Level: ")

def generate_integer(level):
    score = 0
    for i in range(10):
        if level == 1:
            x = random.randint(0, 9)
            y = random.randint(0, 9)
        elif level == 2:
           x = random.randint(10, 99)
           y = random.randint(10, 99)
        else:
            x = random.randint(100, 999)
            y = random.randint(100, 999)

        answr = input(f"{x} + {y} = ")

        cntr = 0
        if int(answr) == x + y :
            score += 1
        else:
            while int(answr) != (x + y) and cntr < 2:
                print("EEE")
                answr = input(f"{x} + {y} = ")
                cntr += 1
                if cntr == 2:
                    m = x + y
                    print(f"{x} + {y} = {m}")
                    break
    print(score)

if __name__ == "__main__":
    main()
```

Bitcoin Price Index
```python
import json
import requests
import sys


try:
    n = sys.argv[1]
    n = float(n)
except ValueError:
    sys.exit("Command-line argument is not a number")
except requests.RequestException:
    sys.exit("Missing command-line argument")


response = requests.get("https://api.coindesk.com/v1/bpi/currentprice.json")
o = response.json()
conversion = float((o["bpi"]["USD"]["rate"]).replace(",", ""))
usdVal = n * conversion
print( "$" + '{:,.4f}'.format(usdVal) )


#{"time":{"updated":"Jul 17, 2024 13:18:44 UTC",
#         "updatedISO":"2024-07-17T13:18:44+00:00",
#         "updateduk":"Jul 17, 2024 at 14:18 BST"},
#"disclaimer":"This data was produced from the CoinDesk Bitcoin Price Index (USD). Non-USD currency data converted using hourly conversion rate from openexchangerates.org",
#"chartName":"Bitcoin",
#"bpi":{"USD":{"code":"USD","symbol":"&#36;","rate":"64,773.009","description":"United States Dollar","rate_float":64773.0085},
#       "GBP":{"code":"GBP","symbol":"&pound;","rate":"49,701.69","description":"British Pound Sterling","rate_float":49701.6897},
#       "EUR":{"code":"EUR","symbol":"&euro;","rate":"59,194.045","description":"Euro","rate_float":59194.0445}}}
```
