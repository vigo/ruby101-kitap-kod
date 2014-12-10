# Chapter 4.3

## Proc ve Lambda

```ruby
def multiplier(with)
  return Proc.new {|number| number * with }
end
```


```ruby
multiply_with_5 = multiplier(5)
```


```ruby
puts multiply_with_5
# #<Proc:0x007fcc9c94a938@/Users/vigo/Desktop/ruby101_book_tests.rb:2>

puts multiply_with_5.class
# Proc
```


```ruby
puts multiply_with_5.call(5)  # 25
puts multiply_with_5.call(10) # 50
```


```ruby
def multiplier(number, with)
  return number * with
end

puts multiplier 5, 5 # 25
```


```ruby
multiplier = Proc.new { |*number|
  number.collect { |n| n ** 2 }
}

multiplier.call(1)       # => [1]
multiplier.call(2,4,6)   # => [4, 16, 36]
multiplier[2,4,6].class  # => Array
```


## Lambda

```ruby
custom_print = lambda { |txt| puts txt }
custom_print.call("Hello") # Hello
```


```ruby
custom_print = lambda { |txt| puts txt }
custom_print.call("Hello", "World")

# ArgumentError: wrong number of arguments (2 for 1)
```


```ruby
l = lambda { "Merhaba" }
puts l.call # Merhaba
```


```ruby
l = lambda do |user_name|
  if user_name == "vigo"
    "Selam vigo! nasılsın?"
  else
    "Selam sana #{user_name}"
  end
end

puts l.call("vigo")   # Selam vigo! nasılsın?
puts l.call("uğur")   # Selam sana uğur
```


## Proc ve Lambda Farkı

```ruby
def arguments(input)
  one, two = 1, 2
  input.call(one, two)
end

puts arguments(Proc.new{ |a, b, c| puts "#{a} ve #{b} ve #{c.class}" })

# 1 ve 2 ve NilClass

puts arguments(lambda{ |a, b, c| puts "#{a} ve #{b} ve #{c.class}" })

# ArgumentError: wrong number of arguments (2 for 3)
```


## Proc'u Block'a çevirmek

```ruby
items = ["Bu bir", "bu iki", "bu üç"]
print_each_element = lambda { |item| puts item }
items.each(&print_each_element)
```


```ruby
items = ["Bu bir", "bu iki", "bu üç"]
def print_each_element(item)
  puts item
end
items.each(&method(:print_each_element))
```


