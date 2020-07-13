# Python Notes

## Working with Postgres

To connect to a local database in a Python script, use the psycopg2 module:

```shell
pip3 install psycopg2
```

### Profilers
Python has several profilers. pyinstrument provides a nice output.
```shell
pip install pyinstument
pyinstrument -r html <script.py>
```
This will format a nice html output.

### Linting
Black is a nice tool to lint your code.

```shell
black -l 120 <script.py>
```
This will lint the code with a max of 120 chars on each line.

# Python Course Notes

### Named tuple

This is a good [explanation](https://stackoverflow.com/questions/2970608/what-are-named-tuples-in-python).

Immutable, ordered.

##### Use Case:
```python3
from collections import namedtuple
```
