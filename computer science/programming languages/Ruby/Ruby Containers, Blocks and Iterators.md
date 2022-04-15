# Containers, Blocks and Iterators
Containers are objects that hold *references* to one or more other objects. Containers need a similar set of methods - adding objects, removing objects and returning a list of objects.

## Containers
To implement a container, we can use Ruby's `Array`, `Hash` or implement our own list class

### Array
The class `Array` holds a collection of object references, each object reference occupies a position in the array, identified by a non-negative integer index. Arrays are indexed using `[]`, this is actually a method and hence can be overridden in its subclass. Besides indexing, `[]` also provides other functionalities

```
a = [1,3,5,7,9]
a[1,3] >> [3,5,7] # [start, count] returns new array from index + count elements
a[-3, 2] >> [5,7] # negative indedx means from the back

# We can provide range for arrays, two period includes end position
a[1..3] >> [3,5,7] 

# Three period does not 
a[1...3] >> [3,5] 
```

### Hashes
Hashes are like arrays, but the indexing is done using other objects. When a value is stored in a hash, two objects are supplied - the key and the value. Unlike array, the hashes are not ordered so we cannot use hash as a stack or queue.

## Blocks and Iterators
A Ruby iterator is a method that can invoke a block of code. 

First, a block may appear only in the source adjacent to a method call; the block is written starting on the same line as the methods' last parameter. Second, a block is not executed at the time it is encountered, Ruby only remembers its context.

```
def threeTimes
  yield
  yield
  yield
end
threeTimes { puts "Hello" } # block only executed here
```

The block `{puts "Hello}"` is associated with the call to the method `threeTimes`, within the method, `yield` is called three times in a row. Blocks can take in and return values. For example, the following returns the Fibonacci series

```
def fibUpTo(max)
  i1, i2 = 1, 1        # parallel assignment
  while i1 <= max
    yield i1
    i1, i2 = i2, i1+i2 # this is returned (i1, i2)
  end
end

fibUpTo(1000) { |f| print f, " " }
```

The yield statement here has a parameter, this value is passed to the associated block. In the definition of the block, the argument list appears between vertical bars. In this instance, a variable `f` receives the value passed to the `yield`. 