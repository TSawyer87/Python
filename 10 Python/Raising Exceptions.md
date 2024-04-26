#Debugging
Python raises an exception whenever it tries to execute invalid code.

Exceptions are raised with a raise statement. In code, a raise statement consists of the following:

- The raise keyword
- A call to the Exception() function
- A string with a helpful error message passed to the Exception() function

For example, enter the following into the interactive shell:

>>> raise Exception('This is the error message.')  
Traceback (most recent call last):  
  File "<pyshell#191>", line 1, in <module>  
    raise Exception('This is the error message.')  
Exception: This is the error message.
If there are no try and except statements covering the raise statement that raised the exception, the program simply crashes and displays the exception’s error message.
