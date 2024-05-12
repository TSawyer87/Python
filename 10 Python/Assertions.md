#Debugging 
An _assertion_ is a sanity check to make sure your code isn’t doing something obviously wrong. These sanity checks are performed by assert statements. If the sanity check fails, then an AssertionError exception is raised. In code, an assert statement consists of the following:

- The assert keyword
- A condition (that is, an expression that evaluates to True or False)
- A comma
- A string to display when the condition is False

In plain English, an assert statement says, “I assert that the condition holds true, and if not, there is a bug somewhere, so immediately stop the program.” For example, enter the following into the interactive shell:
```python
>>> ages = [26, 57, 92, 54, 22, 15, 17, 80, 47, 73]  
>>> ages.sort()  
>>> ages  
[15, 17, 22, 26, 47, 54, 57, 73, 80, 92]  
>>> assert  
ages[0] <= ages[-1] # Assert that the first age is <= the last age.
```
The assert statement here asserts that the first item in ages should be less than or equal to the last one. This is a sanity check; if the code in sort() is bug-free and did its job, then the assertion would be true.

Because the ages[0] <= ages[-1] expression evaluates to True, the assert statement does nothing.

However, let’s pretend we had a bug in our code. Say we accidentally called the reverse() list method instead of the sort() list method. When we enter the following in the interactive shell, the assert statement raises an AssertionError:
```python
>>> ages = [26, 57, 92, 54, 22, 15, 17, 80, 47, 73]  
>>> ages.reverse()  
>>> ages  
[73, 47, 80, 17, 15, 22, 54, 92, 57, 26]  
>>> assert ages[0] <= ages[-1] # Assert that the first age is <= the last age.  
Traceback (most recent call last):  
  File "<stdin>", line 1, in <module>  
AssertionError
```
- Unlike exceptions, your code should _not_ handle assert statements with try and except; 
- if an assert fails, your program _should_ crash. By “failing fast” like this, you shorten the time between the original cause of the bug and when you first notice the bug. This will reduce the amount of code you will have to check before finding the bug’s cause.

Assertions are for programmer errors, not user errors. Assertions should only fail while the program is under development; a user should never see an assertion error in a finished program. For errors that your program can run into as a normal part of its operation (such as a file not being found or the user entering invalid data), raise an exception instead of detecting it with an assert statement. You shouldn’t use assert statements in place of raising exceptions, because users can choose to turn off assertions. If you run a Python script with `python -O myscript.py` instead of `python myscript.py`, Python will skip assert statements. Users might disable assertions when they’re developing a program and need to run it in a production setting that requires peak performance. (Though, in many cases, they’ll leave assertions enabled even then.)

Assertions also aren’t a replacement for comprehensive testing. For instance, if the previous ages example was set to `[10, 3, 2, 1, 20]`, then the assert `ages[0] <= ages[-1] `assertion wouldn’t notice that the list was unsorted, because it just happened to have a first age that was less than or equal to the last age, which is the only thing the assertion checked for.