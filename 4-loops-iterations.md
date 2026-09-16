# Loops and Iterations
>In this module, we learn about iterating structures in python, to be more specific, loops. We learn the two main loops: while and for loops.

## Code
```python
largest = None
smallest = None
while True:
    num = input("Enter a number: ")
    if num == "done":
        break

    try:
        num = int(num)
        if largest is None or num > largest:
            largest = num
        if smallest is None or num < smallest:
            smallest = num
    except:
        print("Invalid input")

print("Maximum is", largest)
print("Minimum is", smallest)
```

## Concepts Learnt
- For loops and while loops
- break/continue statements

## References
- [PY4E](https://www.py4e.com/lessons/loops)
