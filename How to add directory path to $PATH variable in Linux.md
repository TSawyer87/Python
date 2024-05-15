#Environment_variables 

- When you type a command into a Linux terminal, what's really happening is that a program is being executed.
- Normally, to execute a custom program or script, we need to use its full path, such as `/path/to/script.sh` or just `./script.sh` if we're already in its residing directory.
- Alternatively, we can execute a lot of commands without specifying paths, like `uptime` or `date`, etc.

The reason we don't need to specify paths for some commands is because of the `SPATH` variable.
	This is a variable that can be configured to tell our Linux system where to look for certain programs.
	That way, when typing `date` into the terminal, Linux checks the $PATH variable to see a list of directories to look for the program.

**View currently configured directories in $PATH**

Seeing all the directories that are currently configured in your system's $PATH variable is easy:
```bash
echo $PATH
```
`Out:`
```
/home/jr/zig-linux-x86_64-0.12.0:/home/jr/anaconda3/condabin:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/home/jr/.local/bin:/home/jr/bin:/home/jr/.cargo/bin
```

- As you can see, there are a few different directories already stored in $PATH.
- This is what allows us to run so many commands by default, without specifying their full location in the terminal.

To see what directory a command belongs to, you can use the `which` command:
```bash
which date
```
`Out:`
`/usr/bin/date`

**Temporarily add a directory to $PATH**

To add a directory to $PATH for the current session, use the following command syntax.  In this example, we're adding the `/bin/myscripts` directory:
```bash
export PATH="/bin/myscripts:$PATH"
```

You can verify afterwards that the directory has been added.
```bash
echo $PATH
```
`Out:`
`/bin/myscripts [...]`

- Now, files we have stored in the `/bin/myscripts` directory can be executed anywhere, without specifying their full path.

**Permanently add a directory to $PATH**

To add a directory to $PATH permanently, we'll have to edit the `.bashrc` file of the user you want to change.
```bash
nvim ~/.bashrc
```

At the end of this file, put your new directory you wish to permanently add to $PATH.
```nvim
export PATH="/bin/myscripts:$PATH"
```

Save the changes and exit the file.  Afterwards the following command makes the changes take effect in your current session. Alternatively, you can log out and reboot the system.
```bash
source ~/.bashrc
```
That's it! You can check $PATH once more to verify the change.
```bash
echo $PATH
```