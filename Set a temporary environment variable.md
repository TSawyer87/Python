- **Step 1** : Use the following command to create a new shell variable. This will only make the variable in your current session:
```bash
MY_SITE='linuxconfig.org'
```

- **Step 2**: Use the `export` command to set the new variable as an environment variable:
```bash
export MY_SITE
```

- **Step 3**: Alternatively, we can set the temporary env variable by using a single command with this syntax:
```bash
export MY_SITE="linuxconfig.org"
```
