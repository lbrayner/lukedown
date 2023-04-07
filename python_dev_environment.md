# pyenv

- pyenv similar to nvm, but it builds from source
- install dev libraries (Wiki, troubleshooting)

```python
pyenv install 3.10.6
pyenv global 3.10.6
pyenv install 3.10.0
```

- Create a file `~/.config/pip/pip.conf`:

```conf
[install]
only-binary = yes
```

- cd project
- pyenv local 3.10.0

If you're using zsh, run `rehash` after either `pyenv global` or `pyenv local`.

- pip3 install pipenv
- pipenv -r requirements.txt

A sample `pyrightconfig.json`:

```json
{
    "venvPath": "/home/lbrayner/.local/share/virtualenvs",
    "venv": "src-yHlzwEGQ"
}
```
