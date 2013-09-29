shepherdpy
==========

A companion library for mincemeatpy that will manage MapReduce clients.

You can get mincemeatpy here:

https://github.com/michaelfairley/mincemeatpy

Why?
----

mincemeatpy is a small, lightweight MapReduce library for Python.
It doesn't provide functionality for managing processes.

shepherdpy makes it easy to manage mincemeatpy clients.


First Example
-------------

This is the simplest example. It will use the identical dataset from [the mincemeat.py example](https://github.com/michaelfairley/mincemeatpy).


First, start the server:

```bash
python example.py
```

Second, start the client:

```bash
python shepherd.py
```

And the server will print out:

```python
{'a': 2, 'on': 1, 'great': 1, 'Humpty': 3, 'again': 1, 'wall': 1, 'Dumpty': 2, 'men': 1, 'had': 1, 'all': 1, 'together': 1, "King's": 2, 'horses': 1, 'All': 1, "Couldn't": 1, 'fall': 1, 'and': 1, 'the': 2, 'put': 1, 'sat': 1}
```


Notice that shepherd.py supplies reasonable default values to mincemeat,
so it is easier to start the mincemeat clients.

If you don't run
```bash
python example.py
```
before you run
```bash
python shepherd.py
```
then shepherd.py will quietly do nothing and exit.


Example for starting clients before server
------------------------------------------

You can use the -s option to start the clients before the server.
The -s option defines the number of seconds each client will sleep between
connection attempts.  This allows you to run

```bash
python shepherd.py -s 1
```

then to run

```bash
python example.py
```


Example for running clients forever
-----------------------------------

You can use the -8 flag to run the clients forever (or until ctrl+C) is pressed.
First run

```bash
python shepherd.py -8
```

then run

```bash
python example.py
```

You can then run the following again

```bash
python example.py
```

Note the example.py server returns an result both times and shepherd.py continues running.


Example for setting the number of client processes
--------------------------------------------------

The -n option controls how many client processes will be created.

For example, run the server
```bash
python example.py
```

next start 2 clients
```bash
python shepherd.py -n 2
```

Note that for very short tasks, such as example.py, both processes may not be used.


Other Options
-------------
* -v flag will use INFO logging level.
* -V flag will use DEBUG logging level.


Notes
-----

mincemeat.py 0.1.3 is included in this repo.  It is for testing and demo
purposes only.  It is recommended you use the official mincemeat.py version
from the [repo](https://github.com/michaelfairley/mincemeatpy).