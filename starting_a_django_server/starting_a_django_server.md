# Introduction


# Lets get started
1. Create a folder to host your django application.
2. I recommend setting up a virtual environment for each and every application you build using the django framework.

## Install django framework
Open terminal in your project directory:
Run
```bash
    virtualenv virtual
```
or
```bash
    python3 -m venv virtual
```

This command will create a python virtual environment named "virtual" in your project directory.

Activate your virtual environment:
Run
```bash 
source virtual/bin/activate
```
Then,
Install Django
Run
```bash
(virtual) pip install django
```
or you can use python buit in pip module
Run
```bash
(virtual) python -m pip install django
```
Any of the above commands should install the latest current version of django.

However, it is important to check the django version installed in your virtual environment.

On your terminal, open the python shell
Run
```bash
(virtual) python
```
or
```bash
(virtual) python3
```
This command will issue a prompt in python shell run codes below to check django version installed.
```bash
(virtual)
    >>> import django
    >>> django.get_version()

output:
>>> '4.0.3'
```
I used django version (4.0.3) as it was the current LTS when writing this documentation.

## Start django project

