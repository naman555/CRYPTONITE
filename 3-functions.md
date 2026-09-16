# Functions
> In this module, we learn about functions. Functions provide to reuse a piece of code multiple times throughout the program without rewriting it everytime.

## Code
```python
def computepay(hrs,rph):
    if hrs <= 40:
        pay = hrs * rph
    elif hrs > 40:
        pay = 40*rph + (hrs-40)*rph*1.5
    return pay

hrs = int(input("Enter hours: "))
rph = float(input("Enter rate per hour: "))
pay = computepay(hrs,rph)
print("Pay", pay)
```

## Concepts Learnt
- What is a function?
- Creation of functions

## References
- [PY4E](https://www.py4e.com/lessons/functions)
