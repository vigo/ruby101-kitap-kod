# Chapter 5.2

## Number (Sayılar)


```ruby
3.class # => Fixnum
3.class.superclass # => Integer
3.class.superclass.superclass # => Numeric
3.class.superclass.superclass.superclass # => Object
```


```ruby
2014.class                  # => Fixnum
2_014.class                 # => Fixnum
201.4.class                 # => Float
1.2e3.class                 # => Float
7e4.class                   # => Float
7E-4.class                  # => Float
0664.class                  # => Fixnum
0xfff.class                 # => Fixnum
0b1111.class                # => Fixnum
45678327041234321312.class  # => Bignum
```


## Number Method'ları

```ruby
5.methods # => [:to_s, :inspect, :-@, :+, :-, :*, :/, :div, :%, :modulo, :divmod, :fdiv, :**, :abs, :magnitude, :==, :===, :<=>, :>, :>=, :<, :<=, :~, :&, :|, :^, :[], :<<, :>>, :to_f, :size, :bit_length, :zero?, :odd?, :even?, :succ, :integer?, :upto, :downto, :times, :next, :pred, :chr, :ord, :to_i, :to_int, :floor, :ceil, :truncate, :round, :gcd, :lcm, :gcdlcm, :numerator, :denominator, :to_r, :rationalize, :singleton_method_added, :coerce, :i, :+@, :eql?, :remainder, :real?, :nonzero?, :step, :quo, :to_c, :real, :imaginary, :imag, :abs2, :arg, :angle, :phase, :rectangular, :rect, :polar, :conjugate, :conj, :between?, :nil?, :=~, :!~, :hash, :class, :singleton_class, :clone, :dup, :taint, :tainted?, :untaint, :untrust, :untrusted?, :trust, :freeze, :frozen?, :methods, :singleton_methods, :protected_methods, :private_methods, :public_methods, :instance_variables, :instance_variable_get, :instance_variable_set, :instance_variable_defined?, :remove_instance_variable, :instance_of?, :kind_of?, :is_a?, :tap, :send, :public_send, :respond_to?, :extend, :display, :method, :public_method, :singleton_method, :define_singleton_method, :object_id, :to_enum, :enum_for, :equal?, :!, :!=, :instance_eval, :instance_exec, :__send__, :__id__]
```


```ruby
5.to_s # => "5"
# Sayısal değeri String'e çevirdik

-5.abs # => 5
# Mutlak değer

5.zero? # => false
# Sıfır mı?

5.even? # => false
# Çift sayı mı?

5.odd?  # => true
# Tek sayı mı?

5.next # => 6
# Sonraki sayı?

5.pred # => 4
# Önceki sayı?

3.14.floor # => 3
# Taban değeri

3.14.ceil # => 4
# Tavan değeri

1.49.round # => 1
1.51.round # => 2
# Yuvarlama

1.bit_length # => 1
15.bit_length # => 4
255.bit_length # => 8
# Bit cinsinden uzunluğu/boyu

1.size        # => 8
10.size       # => 8
10242048.size # => 8
1024204810242048102420481024.size # => 12
# Byte cinsinden kapladığı yer
```
