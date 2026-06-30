 Special-Methods.Assignment
 NAme:Anita Somiah
 F.O.E.21.006.033.24
From __getitem__ to __del__

1. WHAT ARE SPECIAL METHODS?

Special Methods = "Dunder Methods" or "Magic Methods"

Definition: Built-in methods in Python that use double underscores: __name__
Purpose: They let you define how your objects interact with Python’s built-in syntax and functions.

How they work: You don’t call them directly. Python calls them for you when you use operators or built-ins.

Example:
a + b -> calls a.__add__(b)
len(a) -> calls a.__len__()
a[0] -> calls a.__getitem__(0)

2. __getitem__(self, key) : ITEM ACCESS

Called by: obj[key]
Purpose: Defines behavior for indexing and slicing.

def __getitem__(self, key):
    return self._data[key]

Usage: obj[0], obj[1:5]

3. __setitem__(self, key, value) : ITEM ASSIGNMENT

Called by: obj[key] = value
Purpose: Defines behavior for assigning to an index or key.

def __setitem__(self, key, value):
    self._data[key] = value

Usage: obj[0] = 10

4. __contains__(self, item) : MEMBERSHIP TESTING

Called by: item in obj
Purpose: Defines behavior for the `in` operator.

def __contains__(self, item):
    return item in self._data

Usage: 5 in obj -> True or False

5. __call__(self, *args, **kwargs) : CALLABLE OBJECTS

Called by: obj()
Purpose: Allows instances to be called like functions.

def __call__(self, x):
    return x * 2

Usage: obj(5) -> 10

6. __iter__(self), __next__(self) : ITERATION SUPPORT

Called by: for x in obj:
Purpose: Makes an object iterable. __iter__ returns an iterator. __next__ returns the next item.

def __iter__(self):
    self._n = 0
    return self

def __next__(self):
    if self._n < len(self._data):
        val = self._data[self._n]
        self._n += 1
        return val
    raise StopIteration

7. __bool__(self) : BOOLEAN EVALUATION

Called by: bool(obj) or if obj:
Purpose: Defines the truth value of an object.

def __bool__(self):
    return len(self._data) > 0

Usage: if obj:...

8. __del__(self) : DESTRUCTOR

Called by: Python when the object is about to be destroyed.
Purpose: Defines cleanup actions before an object is deleted.

def __del__(self):
    print("Object is being deleted"
