Using pyenv to Install Python

Now that you have pyenv installed, installing [[Python]] is the next step. You have many versions of Python to choose from. If you wanted to see all the available CPython 3.6 through 3.8, you can do this:

$ pyenv install --list | grep " 3\.[678]"
  3.6.0
  3.6-dev
  3.6.1
  3.6.2
  3.6.3
  3.6.4
  3.6.5
  3.6.6
  3.6.7
  3.6.8
  3.7.0
  3.7-dev
  3.7.1
  3.7.2
  3.8-dev

The above shows all the Python versions that pyenv knows about that match the regular expression. In this case, that is all available CPython versions 3.6 through 3.8. Likewise, if you wanted to see all the Jython versions, you could do this:

$ pyenv install --list | grep "jython"
  jython-dev
  jython-2.5.0
  jython-2.5-dev
  jython-2.5.1
  jython-2.5.2
  jython-2.5.3
  jython-2.5.4-rc1
  jython-2.7.0
  jython-2.7.1

Again, you can see all the Jython versions that pyenv has to offer. If you want to see all the versions, you can do the following:

$ pyenv install --list
...
# There are a lot

Once you find the version you want, you can install it with a single command:

$ pyenv install -v 3.7.2
/tmp/python-build.20190208022403.30568 ~
Downloading Python-3.7.2.tar.xz...
-> https://www.python.org/ftp/python/3.7.2/Python-3.7.2.tar.xz
Installing Python-3.7.2...
/tmp/python-build.20190208022403.30568/Python-3.7.2 /tmp/python-build.20190208022403.30568 ~
[...]
Installing collected packages: setuptools, pip
Successfully installed pip-18.1 setuptools-40.6.2
Installed Python-3.7.2 to /home/realpython/.pyenv/versions/3.7.2

Having Problems? The pyenv documentation has great installation notes as well as a useful FAQ along with common build problems.

This will take a while because pyenv is building Python from source, but once it’s done, you’ll have Python 3.7.2 available on your local machine. If you don’t want to see all the output, just remove the -v flag. Even development versions of CPython can be installed:

$ pyenv install 3.8-dev

Pro Tip: If you’ve been using pyenv for a while and don’t see the version you’re looking for, you may need to run pyenv update to update the tool and make sure you have access to the latest versions.

For the rest of the tutorial, the examples assume you’ve installed 3.6.8 and 2.7.15, but you’re free to substitute these values for the Python versions you actually installed. Also note that the system Python version in the examples is 2.7.12.