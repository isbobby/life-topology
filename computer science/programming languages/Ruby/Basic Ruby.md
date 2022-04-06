# Basic Ruby
### Method definition
```
def sayGoodnight(name)
  result = "Goodnight, " + name
  return result
end
```

### String Interpolation
```
def sayGoodnight(name)
  "Goodnight, #{name}"
end
```

Arbitrarily complex expressions are allowed in the `#{...}` construct. The value returned by a Ruby method is the value of the last expression evaluated, so we can get rid of the return statement.

### Ruby Names
Ruby uses a **convention** to help it distinguish the usage of a name. The first character of a name indicate how to name is used.

- Local variables, method parameters and method names should start with a lowercase letter or underscore
- Global variables are prefixed with ($)
- Instance variables begin with (@) signs
- Class variables start with two (@@) signs
- Class name, module names, constants should start with uppercase letter

### Array and Hashes
Both Ruby array and hashes are indexed collections. Both store collections of objects, accessible using a key. Array has integer key, hashes have objects as keys.
```
# array
a = [1, "cat", nil]
# hash
h = {
	'cello' => 'string',
	'drum'  => 'percussion'
}
```

### Control Structures
Ruby uses the keyword `end` to signify the end to a body
```
if count > 10
  puts "Try again"
elsif tries == 3
  puts "You lose"
else
  puts "Enter a number"
end

while square < 1000
   square = square*square
end
```

### Blocks and Iterators
Code blocks in Ruby are chunks of code that you can associate with method invocations. Code blocks are just chunks of code between braces or `do ... end`

```
{puts "Hello"} # This is a block

# This is also a block
do
	club.enroll(person)
	person.socialize
end 
```

Once a block is created, it can be associated with a call to a method. The method can then invoke the block one or more times using the Ruby `yield` statement.

```
def callBlock
  yield
  yield
end

callBlock { puts "In the block" }
```

We can also provide parameters to the call to `yield`, these will be passed to the block. Within the block, we need to list the names of the arguments to receive these parameters between "|"

```
def callBlock
	yield ,
end

callBlock {|,| ... }
```

This is how `each` allows iteration through a collection of objects. The value is extracted into the code block via the `|` operator

```
s = [1,2,3]
s.each do |value|
	puts value
end

# outputs 1,2,3
```


