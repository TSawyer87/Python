#Environment_variables 

Variables have the following format:
```bash
KEY=value
KEY="Some other value"
KEY=value1:value2
```
- The names of variables are case-sensitive and by convention, environment variables should have UPPER CASE names.
- When assigning multiple values to the variable they must be separated by a colon `:` character.

Variables can be classified into two main categories, environment variables, and shell variables.
1. **Environment variables** are variables that are available system-wide and are inherited by all spawned child processes and shells.
2. **Shell variables** are variables that apply only to the current shell instance.
	- Each shell such as `zsh` has its own set of internal shell variables.

There are several commands available that allow you to list and set environment variables in Linux:

- `env` – The command allows you to run another program in a custom environment without modifying the current one. When used without an argument it will print a list of the current environment variables.
- `printenv` – The command prints all or the specified environment variables.
- `set` – The command sets or unsets shell variables. When used without an argument it will print a list of all variables including environment and shell variables, and shell functions.
- `unset` – The command deletes shell and environment variables.
- `export` – The command sets environment variables.