#Functions 
- Builtin functions are great, but we can only get so far with them before we need to start defining our own functions. Below is a simple example.

```python
def least_difference(a, b, c):
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    return min(diff1, diff2, diff3)
```
- This creates a function called `least_difference`, which takes three arguments, `a`, `b`, and `c`.

- Functions start with a header introduced by the `def` keyword. The indented block of code following the `:` is run when the function is called.

- `return` is another keyword uniquely associated with functions. When Python encounters a `return` statement, it exits the function immediately, and passes the value on the right hand side to the calling context.

Is it clear what `least_difference()` does from the source code? If we're not sure, we can always try it out on a few examples:
```python
print(
    least_difference(1, 10, 100),
    least_difference(1, 10, 10),
    least_difference(5, 6, 7), # Python allows trailing commas in                                        # argument lists. How nice is that?
)
```
`Out:`
`9 0 1`

Or maybe the `help()` function can tell us something about it.