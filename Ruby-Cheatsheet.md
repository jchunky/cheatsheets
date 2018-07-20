# Ruby Cheatsheet

## Comment
```Ruby
# Comments start with a hash, '#'
```

## Variables
```Ruby
my_variable = “Hello”  
my_variable.capitalize! # ! changes the value of the var same as my_name = my_name.capitalize
my_variable ||= "Hi" # ||= is a conditional assignment only set the variable if it was not set before. 
```

## Constants
```Ruby
MY_CONSTANT = 3 # Constants are in screaming case (all caps, underscores)
```

## Strings
```Ruby
“Hello”.length # 5  
"Hello”.reverse # “olleH”  
"Hello”.upcase # “HELLO”  
"Hello”.downcase # “hello”  
“hello”.capitalize # “Hello”  
“Hello”.include? “i” # Equals to false because there is no i in Hello  
“Hello”.gsub!(/e/, “o”) # Hollo
"1".to_i # transform string to integer –– 1
"test".to_sym # Converts to :test
"test".intern # :test
:test.to_s # converts to "test"
"bla,bla".split(“,”) # Returns an array ["bla", "bla"]
```  

## Symbols
```Ruby
:symbol # symbol is like an ID in html. :Symbols != "Strings"
# Symbols are often used as Hash keys or referencing method names.
# They can not be changed once created. They save memory (only one copy at a given time). Faster.
:test.to_s # converts to "test"
"test".to_sym # converts to :test
"test".intern # :test
# Symbols can be used like this as well:
my_hash = { key: "value", key2: "value" } # is equal to { :key => "value", :key2 => "value" }
```

## Arrays
```Ruby  
my_array = [a,b,c,d,e]  
my_array[1] –– b  
my_array[2..-1] # c , d , e  
multi_d = [[0,1],[0,1]]
[1, 2, 3] << 4 # [1, 2, 3, 4] same as [1, 2, 3].push(4)
array = [5,4,1,3,2]
array.sort # = [1,2,3,4,5] – works with text and other as well.
```

## Hashes
```Ruby  
hash = { "key1" => "value1", "key2" => "value2" } # same as objects in JavaScript
hash = { key1: "value1", key2: "value2" } # the same hash using symbols instead of strings
my_hash = Hash.new # same as my_hash = {} – set a new key like so: pets["Stevie"] = "cat"
pets["key1"] # value1
pets["Stevie"] # cat
my_hash = Hash.new("default value")
hash.select{ |key, value| value > 3 } # selects all keys in hash that have a value greater than 3
hash.each_key { |k| print k, " " } # ==> key1 key2
hash.each_value { |v| print v } # ==> value1value2

my_hash.each_value { |v| print v, " " }
# ==> 1 2 3
```

## Calculation
Addition (+)  
Subtraction (-)  
Multiplication (*)  
Division (/)  
Exponentiation (**)  
Modulo (%)  
you can do 1 += 1 –– which gives you 2 but 1++ and 1-- does not exist in ruby  
The concatenation operator (<<)
"A " << "B" # "A B" but "A " + "B" would work as well but "A " + 4 + " B" not so rather use 
string interpolation (#{4})
"A #{4} B" # "A 4 B"

## Methods
```Ruby
def greeting(hello, *names) # *name is a splat argument, takes several parameters passed in an array
  return "#{hello}, #{names}"
end

start = greeting("Hi", "Justin", "Maria", "Herbert") # call a method by name

def name(variable=default)
  ### The last line in here get's returned by default
end
```




## Classes
```Ruby
class Person # Class names are written in camelcase
  NUMBERS = [0, 1, 2]

  def self.class_method
    # ...
  end

  def initialize(name)
    @name = name 
  end

  def show_name
    puts @name
  end 
end

matz = Person.new("Yukihiro")
matz.show_name # Yukihiro
```

## Blocks
*Blocks are not objects* A block is just a bit of code between do..end or {}. It's not an object on its own, but it can be passed to methods like .each or .select.
```Ruby
def yield_name(name, &block)
  block.call("Kim") # print "My name is Kim. "
  block.call(name) # print "My name is Eric. "
end

yield_name("Eric") { |n| print "My name is #{n}. " } # My name is Kim. My name is Eric. 
yield_name("Peter") { |n| print "My name is #{n}. " } # My name is Kim. My name is Peter. 
```

## Input
```Ruby
gets # is the Ruby equivalent to prompt in javascript (method that gets input from the user)
gets.chomp # removes extra line created after gets (usually used like this)
```

## Output
```Ruby
print “bla” 
puts “test” # puts the text in a separate line
```

## Conditions

**'if' Statements**
```Ruby
if 1 < 2  
  puts “one smaller than two”  
elsif 1 > 2 # *careful not to mistake with else if. In ruby you write elsif*  
  puts “elsif”  
else  
  puts “false”  
end
```

**Trailing 'if'**
```Ruby
puts "be printed" if true
```

**Ternary Operator**
```Ruby
puts 3 > 4 ? "if true" : "else" # else will be putted
```  

**Boolean Operators**
```Ruby
&& # and  
|| # or  
! # not  
(x && (y || w)) && z # Use parenthesis to combine arguments  
problem = false  
print "Good to go!" unless problem # Prints out because problem != true  
```  

## Loops

**'while' Loops**  
```Ruby
i = 1  
while i < 11  
  puts i  
  i = i + 1  
end  
```

**.each**  
```Ruby
things.each do |item| # for each things in things do something while storing that things in the variable item  
  print “#{item}"  
end  
```
on hashes like so:  
```Ruby
hashes.each do |x,y|
  print "#{x}: #{y}"
end
```

**.times**  
```Ruby
10.times do  
  print “this text will appear 10 times”  
end  
```

**.upto / .downto**
```Ruby
10.upto(15) { |x| print x, " " } # 10 11 12 13 14 15  
"a".upto("c") { |x| print x, " " } # a b c  
```
