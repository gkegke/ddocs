## TL;DR

> pip install ddocs

ddocs numpy => [list of functions and classes in numpy]

ddocs math sqrt => Details of the sqrt function, displays it's __doc__ and etc.

ddocs-gui => opens a very simple gui version based on dearpygui

```
usage: ddocs [-h] [--gui [GUI]] [--search SEARCH] [--update [UPDATE]] [--update-module UPDATE_MODULE]
                [--reset-database [RESET_DATABASE]] [--list-all [LIST_ALL]]
                [module] [entities [entities ...]]

Offline and fast documentation (+ source code) cli viewer for python libraries. For when using a browser can be a pain. Also an optional gui.

positional arguments:
  module                Name of the module e.g. builtins, math, numpy
  entities              Optional name of entities in the module e.g. str, sqrt, vectorize

optional arguments:
  -h, --help            show this help message and exit
  --gui [GUI]           Open simple gui version of ddocs.
  --search SEARCH       Search for modules starting with the argument.
  --update [UPDATE]     Update the database to match the modules located in the languages/python.txt file.
  --update-module UPDATE_MODULE
                        Deletes the input module data from the database and re-downloads the latest data if the module
                        is found in the languages/python.txt file.
  --reset-database [RESET_DATABASE]
                        Resets the entire database, then downloads module data given the languages/python.txt file.
                        This can take some time.
  --list-all [LIST_ALL]
                        List all modules in the database
```

## About

A simple and quick offline terminal based python doc search.

When you want to find what's in a module, it's classes and functions..
OR you remember the functions in a module, but want a quick refresher.

Orginally I was going to add javascript/Go support, but it feels meh to in this era of GPTs. For now it's a possible future todo.

You can add and generate the data for non-standard library modules by adding libraries to the python.txt file. then running

> ddocs --update

python.txt file locations,

Linux:        

> ~/.local/share/ddocs

Mac:

> ~/Library/Application Support/ddocs/python.txt

Windows:

> C:\Documents and Settings\<User>\Application Data\Local Settings\gkegke\ddocs

or

> C:\Documents and Settings\<User>\Application Data\gkegke\ddocs

So theoretically you could do something like,

> ./ddocs.py numpy vectorize

# Troubleshooting

Concrete solution is to delete the ddocs folder, and re-run ddocs.

Then, re-add all the modules you want tracked in your languages/python.txt file.

### python.txt

```
# popular non-standard library libraries 
flask
numpy
django
## add more custom libraries you want ddocs to track and store offline data for
# popular 70 libraries from the standard library
argparse
array
ast
asyncio
...
```

Add new libraries you want to track to the list, remove any you feel you don't need/use very
often. Adding a # to the line skips it.

It's simple enough..

e.g.

```
flask
numpy
django
rich
pandas
# popular 70 libraries from the standard library
argparse
builtins
...
```

## Examples

> ddocs bisect bisect_left

```
Module bisect:

Bisection algorithms.

-----------------

Entity bisect_left (function):

Signature: 
Return: 

bisect_left(a, x[, lo[, hi]]) -> index

Return the index where to insert item x in list a, assuming a is sorted.

The return value i is such that all e in a[:i] have e < x, and all e in
a[i:] have e >= x.  So if x already appears in the list, i points just
before the leftmost x already there.

Optional args lo (default 0) and hi (default len(a)) bound the
slice of a to be searched.

Source: 

-----------------
Children entities:
- __call__ (function)
- __class__ (class)
- __delattr__ (function)
- __dir__ (function)
- __eq__ (function)
- __format__ (function)
- __ge__ (function)
- __getattribute__ (function)
- __gt__ (function)
- __hash__ (function)
- __init__ (function)
- __init_subclass__ (function)
- __le__ (function)
- __lt__ (function)
- __ne__ (function)
- __new__ (function)
- __reduce__ (function)
- __reduce_ex__ (function)
- __repr__ (function)
- __setattr__ (function)
- __sizeof__ (function)
- __str__ (function)
- __subclasshook__ (function)
```

> ddocs itertools product

```
Module itertools:

Functional tools for creating and using iterators.

Infinite iterators:
count(start=0, step=1) --> start, start+step, start+2*step, ...
cycle(p) --> p0, p1, ... plast, p0, p1, ...
repeat(elem [,n]) --> elem, elem, elem, ... endlessly or up to n times

Iterators terminating on the shortest input sequence:
accumulate(p[, func]) --> p0, p0+p1, p0+p1+p2
chain(p, q, ...) --> p0, p1, ... plast, q0, q1, ...
chain.from_iterable([p, q, ...]) --> p0, p1, ... plast, q0, q1, ...
compress(data, selectors) --> (d[0] if s[0]), (d[1] if s[1]), ...
dropwhile(pred, seq) --> seq[n], seq[n+1], starting when pred fails
groupby(iterable[, keyfunc]) --> sub-iterators grouped by value of keyfunc(v)
filterfalse(pred, seq) --> elements of seq where pred(elem) is False
islice(seq, [start,] stop [, step]) --> elements from
       seq[start:stop:step]
starmap(fun, seq) --> fun(*seq[0]), fun(*seq[1]), ...
tee(it, n=2) --> (it1, it2 , ... itn) splits one iterator into n
takewhile(pred, seq) --> seq[0], seq[1], until pred fails
zip_longest(p, q, ...) --> (p[0], q[0]), (p[1], q[1]), ...

Combinatoric generators:
product(p, q, ... [repeat=1]) --> cartesian product
permutations(p[, r])
combinations(p, r)
combinations_with_replacement(p, r)

-----------------

Entity product (class):

Signature: 
Return: 

product(*iterables, repeat=1) --> product object

Cartesian product of input iterables.  Equivalent to nested for-loops.

For example, product(A, B) returns the same as:  ((x,y) for x in A for y in B).
The leftmost iterators are in the outermost for-loop, so the output tuples
cycle in a manner similar to an odometer (with the rightmost element changing
on every iteration).

To compute the product of an iterable with itself, specify the number
of repetitions with the optional repeat keyword argument. For example,
product(A, repeat=4) means the same as product(A, A, A, A).

product('ab', range(3)) --> ('a',0) ('a',1) ('a',2) ('b',0) ('b',1) ('b',2)
product((0,1), (0,1), (0,1)) --> (0,0,0) (0,0,1) (0,1,0) (0,1,1) (1,0,0) ...

Source: 

-----------------
Children entities:
- __class__ (class)
- __delattr__ (function)
- __dir__ (function)
- __eq__ (function)
- __format__ (function)
- __ge__ (function)
- __getattribute__ (function)
- __gt__ (function)
- __hash__ (function)
- __init__ (function)
- __init_subclass__ (function)
- __iter__ (function)
- __le__ (function)
- __lt__ (function)
- __ne__ (function)
- __new__ (function)
- __next__ (function)
- __reduce__ (function)
- __reduce_ex__ (function)
- __repr__ (function)
- __setattr__ (function)
- __setstate__ (function)
- __sizeof__ (function)
- __str__ (function)
- __subclasshook__ (function)
```
