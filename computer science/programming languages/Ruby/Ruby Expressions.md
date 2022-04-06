# Expressions
In Ruby, anything that can reasonably return a value does. Things that are statements in C or Java are expressions in Ruby. For example, the `if` statement return the value of the last expression executed.

## Operator Expressions
Ruby has a basic set of operators. In Ruby, many operators actually make method calls, for example, the expression `a*b+c` evaluates to `(a.*(b)).+(c)`. Because everything is an object, and because we can redefine instance methods, we can even redefine basic operator functions

```
class Fixnum # base class for numbers
	alias oldPlus +
	def +(other)
		oldPlus(other).succ
	end
end

1 + 2 >> 4
```

## Miscellaneous Expressions
### Command Expression
If a string is enclosed in backquotes, or use the delimited form prefixed by `%x`, it will be executed as a command by the underlying operating system. Backquotes are shorthand for a method and can be modified.

```
`date` >> "Sun Jun  9 00:08:26 CDT 2002\n"
%x{echo "Hello there"} >> "Hello there\n"
```

### Assignment
There are two basic form of assignment in Ruby, first assigns an object reference to a variable or constant, the second involves having an object attribute or element reference on the left hand side.

Ruby assignments are effectively performed in parallel, so the values assigned are not affected by the assignment itself. The values on the right-hand side are evaluated in the order in which they appear before any assignment is made to variables or attributes on the left.

```
a, b, c   =   x, (x += 1), (x += 1)
>> a = 0, b = 1, c = 2, x = 2
```

### Conditional Execution
In Ruby,  any value that is not nil or the constant `false` is true (even 0 and 0 length strings evaluate to true).

Ruby supports all the standard boolean operators and introduces the new operator `defined?`. Both `and` and `&&` evaluate to true only if both operands are true. They evaluate the second operand only if the first is true.

Similarly, both `or` and `||` evaluate to true if either operand is true. They only evaluate their second operand if their first operand is false.

`not` and `!` return the opposite of their operand, their difference is in precedence.

The `defined?` operator returns `nil` if its argument is not defined. Otherwise it returns a description of the argument

```
defined? 1 >> "expression"
defined? dummy >> nil
```

### If and Unless
if in Ruby is similar to other languages, the `then` keyword can be used to compact code

```
if aSong.artist == "Gillespie" then  handle = "Dizzy"
elsif aSong.artist == "Parker" then  handle = "Bird"
else  handle = "unknown"
end
```

Ruby also provides `unless` as a negated form of the if statement

```
unless aSong.duration > 180 then
  cost = .25
else
  cost = .35
end
```

### Loops
While loop executes its body zero or more times as long as its condition remains true

```
while gets
	#...
end
```

There is also the negated form of while loop - `until`

```
until playList.duration > 60
	playList.add(song)
end
```

### Iterators
Ruby does not have a `for` loop like in C or Java. Ruby uses methods defined in various built in classes to provide equivalent functionalities

```
3.times do
	puts "hi"
end # puts 3 his

0.upto(9) do |x|
	puts x
end # 1,2 ... 9
```

Although Ruby does not have `for` loops, it still uses `for` as syntactic sugar, where `for ... in` are translated to `each do`

```
for aSong in songList
	aSong.play
end 

# is translated to

songList.each do |aSong|
	aSong.play
end
```

