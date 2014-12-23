# Chapter 7.7

## Meta Programming

```ruby
class String
  def foo
    "foo: #{self}"
  end
end


a = "hello"
a.foo # => "foo: hello"
```


```ruby
# Dortgen.new([sol_ust_x, sol_ust_y], boy, en)
# Dortgen.new([sol_ust_x, sol_ust_y], [sag_alt_x, sag_alt_y])
class Dortgen
  def initialize(*args)
    if args.size < 2  || args.size > 3
      "Bu sınıf en az 2 en fazla 3 parametre alır"
    else
      "Doğru parametre kullanımı"
    end
  end
end
Dortgen.new([0, 0], 10, 10)     # => #<Dortgen:0x007fe3ea1330f0>
Dortgen.new([0, 0], [10, 10])   # => #<Dortgen:0x007fe3ea132d58>
```


```ruby
class Developer
  class << self
    def personality
      "Awesome"
    end
  end
end

Developer.new         # => #<Developer:0x007fc9048a2738>
Developer.personality # => "Awesome"

a = Developer.new
a                     # => #<Developer:0x007fc9048a2120>
a.class               # => Developer
a.class.personality   # => "Awesome"

a.personality         # => undefined method `personality' for #<Developer:0x007fd3ca0a0e10> (NoMethodError)
```


```ruby
class Developer
  define_method :personality do |arg|
    "You are #{arg} developer!"
  end
end

Developer.new.personality("an awesome") # => "You are an awesome developer!"
a = Developer.new
a.personality("an awesome") # => "You are an awesome developer!"
a.class.instance_methods(false) # => [:personality]
```


```ruby
class Developer
  def hello(*args)
    "Hello #{args.join(" ")}"
  end
end
d = Developer.new
d.send(:hello, "vigo", "how are you?") # => "Hello vigo how are you?"
```


```ruby
class Developer
  def method_missing(m, *args, &block)
    "#{m} is not available!"
  end

  def hello
    "Hello from class Developer"
  end
end

class TurkishDeveloper < Developer
  def hello
    "Hello from class TurkishDeveloper"
  end
end

d = TurkishDeveloper.new
d.hello # => "Hello from class TurkishDeveloper"

class TurkishDeveloper
  remove_method :hello
end
d.hello # => "Hello from class Developer" # üst sınıfta varolduğu için çalıştı!
```


```ruby
class TurkishDeveloper
  undef_method :hello
end
d.hello # => "hello is not available!"
```


```ruby
eval("5 + 5")            # => 10
eval('"Hello".downcase') # => "hello"
```


```ruby
class Developer
  def initialize
    @star = 10
  end
end

d = Developer.new
d.instance_eval do
  puts self
  puts @star
end

# #<Developer:0x007fe549a91e70>
# 10
```


```ruby
class Developer
end
Developer.instance_eval do
  def who
    "vigo"
  end
end
Developer.who # => "vigo"
```


```ruby
class Developer
  @@geek_rate = 10
end
Developer.class_eval("@@geek_rate") # => 10
```


```ruby
class Developer
end

Developer.class_eval do
  def who
    "vigo"
  end
end
Developer.new.who # => "vigo"
```


```ruby
class Developer
  @@geek_rate = 10
end
Developer.class_variable_set(:@@geek_rate, "100") # => "100"
Developer.class_variable_get(:@@geek_rate)        # => "100"
```


```ruby
class Developer
  def initialize(name, star)
    @name = name
    @star = star
  end
  
  def show
    "Name: #{@name}, Star: #{@star}"
  end
end

d = Developer.new("vigo", 10)
d.instance_variable_get(:@name) # => "vigo"
d.instance_variable_get(:@star) # => 10
d.show # => "Name: vigo, Star: 10"

d.instance_variable_set(:@name, "lego") # => "lego"
d.show # => "Name: lego, Star: 10"
```


```ruby
class Box
end

Box.const_set("NAME", "web") # => "web"
Box.const_get("NAME")        # => "web"
Box::NAME                    # => "web"

a = Box.new
a.class.constants            # => [:NAME]
a.class::NAME                # => "web"
```


