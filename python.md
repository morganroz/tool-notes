# Python Notes

## Virtual Environments

### virtualenv
Installing:

```sh
pip install virtualenv
virtualenv --version
```

Create a virtual env:
```sh
virtualenv my_name
```
This command creates a directory named my_name that contains everything the virtual environment needs. This is where you install any Python packages you need.

Specify a particular Python version to use (replace 3 with 2.7 if needed):
```sh
virtualenv -p /usr/bin/python3 env_name
```

Activate the virtual environemnt after creating it.
```sh
source virtualenv/bin/activate
```
Now you can install any dependencies you need with regular pip commands!

Once done working, you can deactivate the virtual env with:
```sh
deactivate
```

### virtualenvwrapper

virtualenvwrapper provides a nice way to keep all envs in one place and manage them.

I had to add this to my .bash_profile:

```sh
#virtualenvwrapper
export WORKON_HOME=$HOME/.virtualenvs
export VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python3
export VIRTUALENVWRAPPER_VIRTUALENV=/usr/local/bin/virtualenv
source /usr/local/bin/virtualenvwrapper.sh
```

##### Commands
- Create an environment: ```mkvirtualenv createdenv```
- If in a project folder: ```mkvirtualenv [-a project_path] [-i package] [-r requirements_file] [virtualenv options] [ENVNAME]```  
	- This will create the environment connected to the project folder and will automatically navigate to this folder when you activate the environment.
	- For example, ```mkvirtualenv -a $(pwd) createdenv```
- If you created a virtualenv before the project folder: ```setvirtualenvproject [~/.virtualenvs/your-virtual-env/] [~/path/to/your/project]```
- Deactivate environment: ```deactivate```
- List virtual environments: ```workon```
- Activate a virtual environment: ```workon myenv```
- Delete a virtual environment (must be deactivated): ```rmvirtualenv createdenv```
- Copy an existing env: ```cpvirtualenv createdenv copiedenv```

## Working with Postgres

To connect to a local database in a Python script, use the psycopg2 module:

```sh
pip3 install psycopg2
```

## Testing

##### unittest

```python3 -m unittest discover ./tests```

##### ddt

##### coverage

```pip3 install coverage```
```coverage run --source="SOURCE_DIR" -m unittest discover ./tests```
```coverage report -m```

## Cleanup and Optimizations
### Profilers
Python has several profilers. 

##### pyinstrument
pyinstrument provides a nice output.
```sh
pip install pyinstument
pyinstrument -r html <script.py>
```
This will format a nice html output.

##### cProfile
cProfile has some good basic usage.

```sh
pip install cprofile
python -m cProfile -s cumtime <script.py>
```

The basic output is very simple, so KCacheGrind can help with that. We need to create the cProfile output and convert it to KCacheGrind format using pyprof2calltree.

```sh
python -m cProfile -o <script.cprof> <script.py>
pyprof2calltree -k -i <script.cprof>
```

### Linting
Black is a nice tool to lint your code.


```sh
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
