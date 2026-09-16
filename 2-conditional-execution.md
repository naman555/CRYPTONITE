# Conditional Execution
>Here we learn about comparison operators and conditional operators in python such as if, else, elif, etc.

## Code

```python
hrs = int(input("Enter Hours:"))
rph = float(input("Enter rate per hour:"))
gpay = 0

if (hrs > 40):
    gpay = (hrs-40)*(1.5*rph)+40*rph
else:
    gpay = hrs*rph

print(gpay)
```

```python
score = float(input("Enter Score: "))

if (score>=0.9):
    grade="A"
elif (score>=0.8):
    grade="B"
elif (score>=0.7):
    grade="C"
elif (score>=0.6):
    grade="D"
elif (score<0.6):
    grade="F"
else:
    print("Value is out of range")

print(grade)
```

## Concepts Learnt
- Conditional operators
- Comparison operators

## References
- [PY4E](https://www.py4e.com/lessons/logic)
