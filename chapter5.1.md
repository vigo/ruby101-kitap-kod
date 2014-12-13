# Chapter 5.1

## Object (Nesne)


```ruby
mesaj = "Merhaba"
mesaj.class                                  # => String
mesaj.class.superclass                       # => Object
mesaj.class.superclass.superclass            # => BasicObject
mesaj.class.superclass.superclass.superclass # => nil
```

```ruby
numara = 1
numara.class # => Fixnum
numara.class.superclass # => Integer
numara.class.superclass.superclass # => Numeric
numara.class.superclass.superclass.superclass # => Object
numara.class.superclass.superclass.superclass.superclass # => BasicObject
numara.class.superclass.superclass.superclass.superclass.superclass # => nil
```


## Nesne Metodları (Object Instance Methods)

```ruby
o = Object.new # => #<Object:0x007fe552099a68>
o.__id__       # => 70311450299700
```


```ruby
o = Object.new # => #<Object:0x007f8c3b0a3420>
o.__id__       # => 70120131336720
o.object_id    # => 70120131336720
o.hash         # => -229260864779029724
```


```ruby
t = String.new("Hello")  # => "Hello"
t.__id__                 # => 70170408456140
t.methods                # => [:<=>, :==, :===, :eql?, :hash, :casecmp, :+, :*, :%, :[], :[]=, :insert, :length, :size, :bytesize, :empty?, :=~, :match, :succ, :succ!, :next, :next!, :upto, :index, :rindex, :replace, :clear, :chr, :getbyte, :setbyte, :byteslice, :scrub, :scrub!, :freeze, :to_i, :to_f, :to_s, :to_str, :inspect, :dump, :upcase, :downcase, :capitalize, :swapcase, :upcase!, :downcase!, :capitalize!, :swapcase!, :hex, :oct, :split, :lines, :bytes, :chars, :codepoints, :reverse, :reverse!, :concat, :<<, :prepend, :crypt, :intern, :to_sym, :ord, :include?, :start_with?, :end_with?, :scan, :ljust, :rjust, :center, :sub, :gsub, :chop, :chomp, :strip, :lstrip, :rstrip, :sub!, :gsub!, :chop!, :chomp!, :strip!, :lstrip!, :rstrip!, :tr, :tr_s, :delete, :squeeze, :count, :tr!, :tr_s!, :delete!, :squeeze!, :each_line, :each_byte, :each_char, :each_codepoint, :sum, :slice, :slice!, :partition, :rpartition, :encoding, :force_encoding, :b, :valid_encoding?, :ascii_only?, :unpack, :encode, :encode!, :to_r, :to_c, :>, :>=, :<, :<=, :between?, :nil?, :!~, :class, :singleton_class, :clone, :dup, :taint, :tainted?, :untaint, :untrust, :untrusted?, :trust, :frozen?, :methods, :singleton_methods, :protected_methods, :private_methods, :public_methods, :instance_variables, :instance_variable_get, :instance_variable_set, :instance_variable_defined?, :remove_instance_variable, :instance_of?, :kind_of?, :is_a?, :tap, :send, :public_send, :respond_to?, :extend, :display, :method, :public_method, :singleton_method, :define_singleton_method, :object_id, :to_enum, :enum_for, :equal?, :!, :!=, :instance_eval, :instance_exec, :__send__, :__id__]

t.method(:upcase).call   # => "HELLO"
```


```ruby
o = Object.new
o.methods # => [:nil?, :===, :=~, :!~, :eql?, :hash, :<=>, :class, :singleton_class, :clone, :dup, :taint, :tainted?, :untaint, :untrust, :untrusted?, :trust, :freeze, :frozen?, :to_s, :inspect, :methods, :singleton_methods, :protected_methods, :private_methods, :public_methods, :instance_variables, :instance_variable_get, :instance_variable_set, :instance_variable_defined?, :remove_instance_variable, :instance_of?, :kind_of?, :is_a?, :tap, :send, :public_send, :respond_to?, :extend, :display, :method, :public_method, :singleton_method, :define_singleton_method, :object_id, :to_enum, :enum_for, :==, :equal?, :!, :!=, :instance_eval, :instance_exec, :__send__, :__id__]

o.public_methods # => [:nil?, :===, :=~, :!~, :eql?, :hash, :<=>, :class, :singleton_class, :clone, :dup, :taint, :tainted?, :untaint, :untrust, :untrusted?, :trust, :freeze, :frozen?, :to_s, :inspect, :methods, :singleton_methods, :protected_methods, :private_methods, :public_methods, :instance_variables, :instance_variable_get, :instance_variable_set, :instance_variable_defined?, :remove_instance_variable, :instance_of?, :kind_of?, :is_a?, :tap, :send, :public_send, :respond_to?, :extend, :display, :method, :public_method, :singleton_method, :define_singleton_method, :object_id, :to_enum, :enum_for, :==, :equal?, :!, :!=, :instance_eval, :instance_exec, :__send__, :__id__]

o.private_methods # => [:initialize_copy, :initialize_dup, :initialize_clone, :sprintf, :format, :Integer, :Float, :String, :Array, :Hash, :warn, :raise, :fail, :global_variables, :__method__, :__callee__, :__dir__, :eval, :local_variables, :iterator?, :block_given?, :catch, :throw, :loop, :respond_to_missing?, :trace_var, :untrace_var, :at_exit, :syscall, :open, :printf, :print, :putc, :puts, :gets, :readline, :select, :readlines, :`, :p, :test, :srand, :rand, :trap, :exec, :fork, :exit!, :system, :spawn, :sleep, :exit, :abort, :load, :require, :require_relative, :autoload, :autoload?, :proc, :lambda, :binding, :caller, :caller_locations, :Rational, :Complex, :set_trace_func, :gem, :gem_original_require, :initialize, :singleton_method_added, :singleton_method_removed, :singleton_method_undefined, :method_missing]

o.protected_methods # => []

o.public_methods(false) # => []
```


## Method Missing


```ruby
class User
  def method_missing(method_name, *args, &block)
    if method_name == :show_user_info
      "This user has no information"
    else
      "You've called #{method_name}, You've passed: #{args}"
    end
  end
end

u = User.new
u.show_user_info # => "This user has no information"
u.show_user_age  # => "You've called show_user_age, You've passed: []"
```


```ruby
class Roman
  def roman_to_str(str)
    case str
    when "x", "X"
      10
    when "c", "C"
      100
    when "m", "M"
      1000
    end
  end
  def method_missing(method)
    roman_to_str method.id2name
  end
end

r = Roman.new
r.x # => 10
r.X # => 10
r.C # => 100
r.M # => 1000
```


```ruby
r.method(:C)      # => `method': undefined method `C' for class `Roman' (NameError)
```


```ruby
r.respond_to?(:C) # => false
```


```ruby
class Roman
  def roman_to_str(str)
    case str
    when "x", "X"
      10
    when "c", "C"
      100
    when "m", "M"
      1000
    end
  end
  def method_missing(method)
    roman_to_str method.id2name
  end
  def respond_to_missing?(method_name, include_private = false)
    [:x, :X, :c, :C, :m, :M].include?(method_name) || super 
  end
end

r.method(:C)      # => #<Method: Roman#C>
r.respond_to?(:C) # => true
r.respond_to?(:Q) # => false # olmayan method
```


