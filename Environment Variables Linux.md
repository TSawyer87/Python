**List environment variables**
```bash
printenv
```

**To list a specific variable, just pass the name of it to the command.**
```bash
printenv SHELL
```
`Out:`
`/usr/bin/zsh`

**Check multiple variables at once**:
```bash
printenv HOME SHELL
```
`Out:`
`/home/jr`
`/usr/bin/zsh`


**To interact with the environment variables in your terminal or when writing a script, you will need to precede them with a dollar sign `$`**
```bash
echo "I am logged in as $USER with the $SHELL shell and my home directory is $HOME"
```
`Out:`
`I am logged in as jr with the /usr/bin/zsh shell and my home directory is /home/jr`

- A popular environment variable to edit is the `$PATH` variable, which lets you specify the directories Bash should search for programs when you enter a command.
```bash
printenv PATH
```
`Out:`
`/home/jr/zig-linux-x86_64-0.12.0:/home/jr/anaconda3/condabin:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/home/jr/.local/bin:/home/jr/bin:/home/jr/.cargo/bin`

