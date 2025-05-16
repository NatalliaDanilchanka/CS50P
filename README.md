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

```

Felipe’s Taqueria
```python

```

Grocery List
```python

```

Outdated
```python

```



### Week 4: Libraries

Emojize
```python

```

Frank, Ian and Glen’s Letters
```python

```

Adieu, Adieu
```python

```

Guessing Game
```python

```

Little Professor
```python

```

Bitcoin Price Index
```python

```
