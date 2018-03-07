# tempstore

A simple container for handling multiple tempfiles

Example:

```shell
>>> import tempstore
>>> s = tempstore.TempStore('somedata')
>>> s.create('banana')
'/var/folders/ng/c57k6x7n1qn9f6hw_hw4zrlcnxhmy8/T/tmpsvzuj4bd/tmp3gh1vid9'
>>> s.copy('./')
>>> s.cleanup()
>>>
```

# `tempstore.TempStore(name=None)`

Create a new TempStore. This is handy for keeping track of multiple tempfiles.


# `TempStore.create(name)`

Create a new tempfile. Later, it can be referenced with
`TempStore.paths[name]` or `TempStore.objs[name]`.


# `TempStore.paths`

Access the paths of items in the tempstore


# `TempStore.objs`

Access the `tempfile.NamedTemporaryFile` objects of items in the tempstore


# `TempStore.cleanup()`

Remove all the temporary files in the store


# `TempStore.copy(path=None, exist_ok=True)`

Copy all items in the TempStore to a given path. If TempStore.name is not None,
a new directory will be created in `path` with the name, and all files will be
copied there.

`exist_ok` will be passed to `os.makedirs` if TempStore.name is not None
