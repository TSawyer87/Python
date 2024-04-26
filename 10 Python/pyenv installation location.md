### Installation Location[](https://realpython.com/intro-to-pyenv/#installation-location "Permanent link")
[[pyenv]]
As mentioned before, `pyenv` works by building Python from source. Each version that you have installed is located nicely in your `pyenv` root directory:

`$ ls ~/.pyenv/versions/ 2.7.15  3.6.8  3.8-dev`

All of your versions will be located here. This is handy because removing these versions is trivial:

`$ rm -rf ~/.pyenv/versions/2.7.15`

Of course `pyenv` also provides a command to uninstall a particular Python version:

`$ pyenv uninstall 2.7.15`