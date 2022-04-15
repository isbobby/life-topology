# Modules in Ruby
Modules are a way of grouping methods, classes and constants together. Modules give two main benefits

1. Provides a *namespace* and prevent name clashes
2. Modules implement the mixin facility

## Namespaces
The module mechanism define a namespace, a sandbox in which your methods and constants can play without having to worry about being stepped on by other methods and constants. 

```
module Cow
	def Cow.moo
	end
end

module Bull
	def Bull.moo
	end
end

# Both methods are defined in their own namespace
```

## Mixins
Modules provide a functionality called *mixin* which eliminate the need for multiple inheritance.

```
module Debug
	def print
		"#{self.type.name}"
	end
end

class Photograph
	include Debug
end

class Char
	include Debug
end

Photograph.new().debug >> "Photograph"
Chair.new().debug >> "Chair"
```

The `include` keyword in Ruby does not copy over files like C programs. It makes a reference from the class to included module. If multiple classes include that module, they will all point to the same thing.

