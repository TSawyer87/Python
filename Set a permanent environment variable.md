#Environment_variables

In order to configure a new environment variable to be persistent, we’ll need to edit the Bash configuration files. This can be done through three different files, depending on exactly how you plan to access the environment variable.

- `~/.bashrc` - Variables stored here will reside in the user's home directory and are only accessible by that user.  The variables get loaded any time a new shell is opened.
- `/etc/profile` - Variables stored here will be accessible by all users and are loaded whenever a new shell is opened.
- `/etc/environment` - Variables stored here are accessible system-wide.


	Add a new variable to the `~/.bashrc` or `/etc/profile` configuration files by appending a line to the end of it with this syntax. Notice we precede each new variable with `export`.
```bash
export MY_SITE='linuxconfig.org'
```
- Afterwards, you can load the new environment variables into the current session with the following command.
```bash
source ~/.bashrc
OR
source /etc/profile
```


If adding an environment variable to the `/etc/environment` file, you don't need to precede the line with "export".
```bash
MY_SITE='linuxconfig.org'
```