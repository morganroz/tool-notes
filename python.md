# Python Notes

## Working with Postgres

To connect to a local database in a Python script, use the psycopg2 module:

```shell
pip3 install psycopg2
```

## Cleanup and Optimizations
### Profilers
Python has several profilers. 

##### pyinstrument
pyinstrument provides a nice output.
```shell
pip install pyinstument
pyinstrument -r html <script.py>
```
This will format a nice html output.

##### cProfile
cProfile has some good basic usage.

```shell
pip install cprofile
python -m cProfile -s cumtime <script.py>
```

The basic output is very simple, so KCacheGrind can help with that. We need to create the cProfile output and convert it to KCacheGrind format using pyprof2calltree.

```shell
python -m cProfile -o <script.cprof> <script.py>
pyprof2calltree -k -i <script.cprof>
```


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
