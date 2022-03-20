---
title: How to install pyenv and python on ubuntu
tags: [pyenv, python, ubuntu]
---

## My work environment
- ubuntu

## Prerequisites
- git

## Steps

[pyenv github page](https://github.com/pyenv/pyenv#basic-github-checkout)

1. Install dependencies
```sh
sudo apt-get update; sudo apt-get install make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

2. Install pyenv from git repository
```sh
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
cd ~/.pyenv && src/configure && make -C src
```

3. Setup .bashrc file
```sh
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init --path)"' >>~/.bashrc
```

4. Apply modified .bashrc or re-open terminal
```sh
source ~/.bashrc
```

5. Install python by specifying version
```sh
pyenv install 3.9.11
```

6. Use installed python version globally
```sh
pyenv global 3.9.11
```

7. Check if installed succesfully
```sh
pyenv --version
python --version
```
