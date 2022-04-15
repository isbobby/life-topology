# Classes, Objects and Variables
## Classes
Classes in Ruby have names that start with an uppercase letter, while method names start with a lower case letter. `initialize` is a special method in Ruby programs, when we call `.new` to create a new object.

Ruby first creates an uninitialized object then calls the `initialize` method, passing any parameters that were passed to `new`

```
class Song
	def initialize(name, artist, duration)
		@name 	  = name
		@artist   = artist
		@duration = duration
	end
end
```

Each `song` object represents its own song. Values such as song name and artist have to be stored together with the song object. In Ruby, an instance variable is a name preceded by "@" sign.

```
aSong = Song.new("Bicylops", "Fleck", 260)
aSong.inspect 

<Song:0x401b4924 @duration=260, @artist=\"Fleck\", @name=\"Bicylops\">
```

## Inheritance and Messages
Inheritance allows you to create a class that is a refinement or specialization of another class. For example, a subclass with an additional attribute can be defined in the following way. The `KaraokeSong < Song` definition tells Ruby that `KaraokeSong` is a subclass of `Song`.

```
class KaraokeSong < Song
	def initialize(name, artist, duration, lyrics)
		super(name, artist, duration)
		@lyrics = lyrics
	end
end
```

When we execute a class method, Ruby will first run a matching class method. If such method is not found, it will search for this method in the parent class, and the grandparent class, and so on.

### Mixins
Some object oriented languages support multiple inheritance, where a class can have more than one immediate parent. Ruby class can have only one direct parent. However, Ruby classes can include the functionality of any number of mixins (a mixin is like a partial class definition).

## Objects and Attributes
The above `Song` class have an internal state. The state is private to those objects, no other object can access an object's instance variables. We will therefore define methods which allow us to access and manipulate the state of an object.

```
class Song
	def name
		@name # makes use of Ruby - automatically return last 
		      # statement
	end
```

### Writable Attributes
The class methods can be modified to write to an object attribute.

```
class Song
	def duration=(newDuration)
		@duration = newDuration
	end
end
```

The assignment `aSong.duration = 257` invokes the method `duration=` in the `aSong` object, passing it `257` as an argument. Defining a method name ending *in an equal sign* makes the name eligible to appear on the left-hand side of an assignment.

## Class Variables and Class Methods
The classes so far have contained instance variables and instance methods: variables that are *associated with a particular instance* of the class. Sometimes classes themselves need to have their own states. This is handled by class variables

### Class Variables
A class variable is *shared among all objects* of a class, and it is also accessible to the class methods (in later sections). There is only one copy of a particular class variable for a given class. Class variable names start with two `@` signs. 

Unlike global and instance variables, they have to be initialized before they are used. Often this initialization is just a simple assignment in the body of the class definition. For the `Song` example, we can use a class variable to track how many times a song has been played globally.

```
class Song
	@@played = 0
	def initialize(name,artist,duration)
		@name     = name
		@artist   = artist
		@duration = duration
		@played   = 0
	end
	def play
		@played  += 1
		@@played += 1
	end
end
```

### Class Methods
Sometimes a class needs to provide methods that work without being tied to any particular object. Class methods are distinguished from instance methods by their definition.

```
class Example
	def instanceMeth
	end
	
	def Example.classMeth
	end
```

### Singletons and Other Constructors
The following defines how a singleton object is created. By making `new` private, we prevent anyone from creating a logging object using the conventional new constructor. Instead, we use `create` to provide access to the single instance of logger.

```
class Logger
  private_class_method :new
  @@logger = nil
  def Logger.cr
  eate
    @@logger = new unless @@logger
    @@logger
  end
end
```

## Access Control
When designing a class interface, it's important to consider the access to the class we are exposing to the outside world. The only way to change object states is by calling one of its methods, so managing the access to the methods means managing the access to the class states.

**Public Methods** - can be called by anyone, methods are public by default except `initialize`

**Protected Method** - can be invoked only by objects of the defining class and its subclass, access is kept within the family

**Private Method** - can only be called with an explicit receiver, they can only be called in the defining class and by direct descendants of within the same object.

```
class MyClass
		def method1 # public by default
		end
	
	protected
		def method2 # protected
		end
	
	private
		def method3 # private
		end
	public
		def method4 # public
		end
end
```

## Variables
Variables are used to keep track of objects, each variable holds a reference to an object. In Ruby, a variable is not an object but a reference to an object, objects are kept in the heap and pointed by the variables.

```
person1 = "Tim"
person2 = person1

person1[0] = "J"

person1 >> "Jim"
person2 >> "Jim"
```

In the above example, the assignment of `person1` to `person2` does not create new objects, it only copies `person1`'s object reference to `person2`, so both variables refer to the same object.


