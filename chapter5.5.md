# Chapter 5.5

## Hash

```ruby
{key1: "value1", key2: "value2", ....}
```


```ruby
{"key1" => "value1", "key2" => "value2", ...}
```


```ruby
{:key1 => "value1", :key2 => "value2", ...}
```


```ruby
Hash.new # => {}
```


```ruby
Hash.class                                  # => Class
Hash.class.superclass                       # => Module
Hash.class.superclass.superclass            # => Object
Hash.class.superclass.superclass.superclass # => BasicObject
Hash.class.superclass.superclass.superclass.superclass # => nil
```


```ruby
Hash.included_modules # => [Enumerable, Kernel]
```


```ruby
h = Hash.new("Tanımsız") # => {}
h[:isim] = "Uğur"        # => "Uğur"
h                        # => {:isim=>"Uğur"}
h[:soyad]                # => "Tanımsız"
h.default                # => "Tanımsız"
```


```ruby
h = Hash.new               # => {}
h[:isim] = "Uğur"          # => "Uğur"
h[:soyad]                  # => nil
```


```ruby
h = Hash.new { |hash, key| hash[key] = "User: #{key}" }
h["vigo"]             # => "User: vigo"
h["foobar"]           # => "User: foobar"
h["animal"] = "horse" # => "horse"
h                     # => {"vigo"=>"User: vigo", "foobar"=>"User: foobar", "animal"=>"horse"}
```


## Hash Class Method'ları

```ruby
Hash["user_count", 5]                            # => {"user_count"=>5}
Hash[ [["user_count", 5], ["active_users", 2]] ] # => {"user_count"=>5, "active_users"=>2}
Hash["user_count" => 5, "active_users" => 2]     # => {"user_count"=>5, "active_users"=>2}
```


```ruby
h = Hash.new
h # => {}
h["user_count"] = 5
h # => {"user_count"=>5}

h = Hash.new { |hash, key| hash[key] = "User ID: #{key}" }
h["1"] # => "User ID: 1"
h["2"] # => "User ID: 2"
h # => {"1"=>"User ID: 1", "2"=>"User ID: 2"}
```


```ruby
Hash.try_convert({"user_count"=>5})   # => {"user_count"=>5}
Hash.try_convert("user_count=>5")     # => nil
```


## Hash Instance Method'ları

```ruby
h = {username: "vigo", password: "1234"} # => {:username=>"vigo", :password=>"1234"}
```


```ruby
h.keys # => [:username, :password]
```


```ruby
h.keys # => [:username, :password, "useremail"]
```


```ruby
h.keys.map(&:class) # => [Symbol, Symbol, String]
```


```ruby
h = Hash.new
h.methods # => [:rehash, :to_hash, :to_h, :to_a, :inspect, :to_s, :==, :[], :hash, :eql?, :fetch, :[]=, :store, :default, :default=, :default_proc, :default_proc=, :key, :index, :size, :length, :empty?, :each_value, :each_key, :each_pair, :each, :keys, :values, :values_at, :shift, :delete, :delete_if, :keep_if, :select, :select!, :reject, :reject!, :clear, :invert, :update, :replace, :merge!, :merge, :assoc, :rassoc, :flatten, :include?, :member?, :has_key?, :has_value?, :key?, :value?, :compare_by_identity, :compare_by_identity?, :entries, :sort, :sort_by, :grep, :count, :find, :detect, :find_index, :find_all, :collect, :map, :flat_map, :collect_concat, :inject, :reduce, :partition, :group_by, :first, :all?, :any?, :one?, :none?, :min, :max, :minmax, :min_by, :max_by, :minmax_by, :each_with_index, :reverse_each, :each_entry, :each_slice, :each_cons, :each_with_object, :zip, :take, :take_while, :drop, :drop_while, :cycle, :chunk, :slice_before, :lazy, :nil?, :===, :=~, :!~, :<=>, :class, :singleton_class, :clone, :dup, :taint, :tainted?, :untaint, :untrust, :untrusted?, :trust, :freeze, :frozen?, :methods, :singleton_methods, :protected_methods, :private_methods, :public_methods, :instance_variables, :instance_variable_get, :instance_variable_set, :instance_variable_defined?, :remove_instance_variable, :instance_of?, :kind_of?, :is_a?, :tap, :send, :public_send, :respond_to?, :extend, :display, :method, :public_method, :singleton_method, :define_singleton_method, :object_id, :to_enum, :enum_for, :equal?, :!, :!=, :instance_eval, :instance_exec, :__send__, :__id__]
```


```ruby
a = [ "a", "b" ]
c = [ "c", "d" ]
h = { a => 100, c => 300 } # => {["a", "b"]=>100, ["c", "d"]=>300}
```


```ruby
h.keys                     # => [["a", "b"], ["c", "d"]]
```


```ruby
h[a]                       # => 100
h[["a", "b"]]              # => 100
h[c]                       # => 300
h[["c", "d"]]              # => 300
```


```ruby
a[0] = "v"                 # => "v"
a                          # => ["v", "b"]
h[a]                       # => nil ????????
```


```ruby
h.rehash                   # => {["v", "b"]=>100, ["c", "d"]=>300}
h[a]                       # => 100
```


```ruby
h = {:foo => "bar"}
h                                 # => {:foo=>"bar"}
h.to_hash                         # => {:foo=>"bar"}
h.to_h                            # => {:foo=>"bar"}
["foo", "bar"].respond_to?(:to_h) # => true
[[:foo, "bar"]].to_h              # => {:foo=>"bar"}

[["a", 1], ["b", 2]].to_h   # => {"a"=>1, "b"=>2}

h.to_a                            # => [[:foo, "bar"]]
h.to_s                            # => "{:foo=>\"bar\"}"
```


```ruby
h1 = { "a" => 100, "c" => 200 }
h2 = { 70 => 350, "x" => 22, "y" => 11 }
h3 = { "y" => 11, "x" => 22, 70 => 350 }

h1 == h2 # => false
h2 == h3 # => true

h1.eql?(h2)  # => false
h2.eql?(h3)  # => true
```


```ruby
h = {:user => "vigo", :password => "secret"}
puts h.fetch(:user) # "vigo"
puts h.fetch(:email)

KeyError: key not found: :email
```


```ruby
h = {:user => "vigo", :password => "secret"}
h.fetch(:user)               # => "vigo"
h.fetch(:email, "Not found") # => "Not found"
```


```ruby
h = {:user => "vigo", :password => "secret"}
h.fetch(:email) { |element| "key: #{element} is not defined!" } # => "key: email is not defined!"
```


```ruby
h = {:user => "vigo", :password => "secret"}
h.store(:email, "vigo@example.com") # => "vigo@example.com"
h                                   # => {:user=>"vigo", :password=>"secret", :email=>"vigo@example.com"}

# ya da

h[:url] = "http://webbox.io"        # => "http://webbox.io"
h                                   # => {:user=>"vigo", :password=>"secret", :email=>"vigo@example.com", :url=>"http://webbox.io"}
```


```ruby
h = Hash.new(10)
h[:user_age]            # => 10
h                       # => {}
h.default               # => 10
h.default(:user_weight) # => 10
```


```ruby
h = Hash.new
h                         # => {}
h.default = 100           # => 100
h[:user_weight]           # => 100
h[:foo]                   # => 100
```


```ruby
h = {:user => "vigo", :password => "secret"}
h.key("vigo")   # => :user
h.key("foobar") # => nil
```


```ruby
h = {:user => "vigo", :password => "secret"}
h.length # => 2
h.size   # => 2
h.count  # => 2
```


## Key, Value Kontrolleri

```ruby
h = {:user => "vigo", :password => "secret", :email => "vigo@foo.com"}
h.keys                        # => [:user, :password, :email]
h.values                      # => ["vigo", "secret", "vigo@foo.com"]
h.values_at(:user, :password) # => ["vigo", "secret"]
```


```ruby
h = {:user => "vigo", :password => "secret", :email => "vigo@foo.com"}
h.key?(:user)          # => true
h.has_key?(:user)      # => true

h.key?(:full_name)     # => false
h.has_key?(:full_name) # => false

h.value?("vigo")       # => true
h.has_value?("vigo")   # => true

h.value?("lego")       # => false
h.has_value?("lego")   # => false
```


```ruby
h = {:user => "vigo", :password => "secret", :email => "vigo@foo.com"}
h.include?(:user)        # => true
h.member?(:user)         # => true
```


```ruby
{:user => "vigo", :password => "secret", :email => "vigo@foo.com"}.empty? # => false
{}.empty? # => true
```


```ruby
# value'su boş olan var mı?
{:user => "vigo", :password => "secret", :email => "vigo@foo.com"}.all?{ |k,v| v.empty? } # => false
{:user => "", :password => "", :email => ""}.all?{ |k,v| v.empty? }                       # => true
{:user => "vigo", :password => "", :email => ""}.all?{ |k,v| v.empty? }                   # => false
```


```ruby
{:is_admin => true, :notifications_enabled => true}.all?{ |option, value| value } # => true
{:is_admin => true, :notifications_enabled => false}.any?{ |option, value| value } # => true
{:is_admin => true, :notifications_enabled => false}.one?{ |option, value| value } # => true
{:is_admin => false, :notifications_enabled => false}.one?{ |option, value| value } # => false
{:is_admin => false, :notifications_enabled => false}.all?{ |option, value| value } # => false
{:is_admin => false, :notifications_enabled => false}.none?{ |option, value| value } # => true
{:is_admin => false, :notifications_enabled => false}.any?{ |option, value| value } # => false
```


```ruby
h = {:user => "vigo", :password => "secret", :email => "vigo@foo.com"}
h.shift # => [:user, "vigo"]
h       # => {:password=>"secret", :email=>"vigo@foo.com"}
h.shift # => [:password, "secret"]
h       # => {:email=>"vigo@foo.com"}
h.shift # => [:email, "vigo@foo.com"]
h       # => {}
```


```ruby
h = {:user => "vigo", :password => "secret", :email => "vigo@foo.com"}
h.delete(:user) # => "vigo"
h               # => {:password=>"secret", :email=>"vigo@foo.com"}
```


```ruby
h.delete(:phone){ |key| "-#{key}- bulunamadı?" } # => "-phone- bulunamadı?"
```


```ruby
# 40'dan büyükleri silelim
h = { point_a: 10, point_b: 20, point_c: 50 } # => {:point_a=>10, :point_b=>20, :point_c=>50}
h.delete_if{ |k,v| v > 40 }                   # => {:point_a=>10, :point_b=>20}
h                                             # => {:point_a=>10, :point_b=>20}
```


```ruby
# 20'dan küçükleri tutalım sadece
h = { point_a: 10, point_b: 20, point_c: 50 }
                         # => {:point_a=>10, :point_b=>20, :point_c=>50}
h.keep_if{ |k,v| v < 20} # => {:point_a=>10}
h                        # => {:point_a=>10}
```


```ruby
h = { "a" => 100, "b" => 200 } # => {"a"=>100, "b"=>200}
h.keys                         # => ["a", "b"]
h.invert                       # => {100=>"a", 200=>"b"}


```ruby
h1 = { "a" => 100, "b" => 200 }
h2 = { "x" => 1, "y" => 2, "z" => 3 }
h1.merge(h2) # => {"a"=>100, "b"=>200, "x"=>1, "y"=>2, "z"=>3}
h1           # => {"a"=>100, "b"=>200}
```


```ruby
h1 = { "a" => 100, "b" => 200 }
h2 = { "x" => 1, "y" => 2, "z" => 3 }
h1.update(h2) # => {"a"=>100, "b"=>200, "x"=>1, "y"=>2, "z"=>3}
h1            # => {"a"=>100, "b"=>200, "x"=>1, "y"=>2, "z"=>3}

h1 = { "a" => 100, "b" => 200 }
h2 = { "x" => 1, "y" => 2, "z" => 3 }
h1.merge!(h2) # => {"a"=>100, "b"=>200, "x"=>1, "y"=>2, "z"=>3}
h1            # => {"a"=>100, "b"=>200, "x"=>1, "y"=>2, "z"=>3}
```


```ruby
h1 = { "a" => 100, "b" => 200, "c" => 0 }
h1.__id__ # => 70320602334320
```


```ruby
h1.replace({ "foo" => 1, "bar" => 2 })
h1        # => {"foo"=>1, "bar"=>2}
h1.__id__ # => 70320602334320
```


```ruby
h1 = { "foo" => 1, "bar" => 2 }
h1.__id__ # => 70216424232360
```


## İterasyon ve Block Kullanımı

```ruby
h = { "a" => 100, "b" => 200, "c" => 0 }
h.each { |key, value| puts "key: #{key}, value: #{value}" }
h.each_pair { |key, value| puts "key: #{key}, value: #{value}" }

# key: a, value: 100
# key: b, value: 200
# key: c, value: 0
```


```ruby
h = { "a" => 100, "b" => 200, "c" => 0 }

h.each_value { |value| puts "value: #{value}" }

# value: 100
# value: 200
# value: 0

h.each_key { |key| puts "key: #{key}" }

# key: a
# key: b
# key: c
```


```ruby
h = { "a" => 100, "b" => 200, "c" => 0 }
h.each_entry{ |o| puts "o: #{o}" }

# o: ["a", 100]
# o: ["b", 200]
# o: ["c", 0]
```


```ruby
h = { "a" => 100, "b" => 200, "c" => 0 }

# 2'li dilimlere ayırdık
h.each_slice(2){ |s| puts "slice: #{s}" }

# slice: [["a", 100], ["b", 200]]
# slice: [["c", 0]]
```


```ruby
h = { "a" => 100, "b" => 200, "c" => 0 }
h.each_cons(2){ |s| puts "grup: #{s}" }

# grup: [["a", 100], ["b", 200]]
# grup: [["b", 200], ["c", 0]]
```


```ruby
h = Hash.new { |hash, key| hash[key] = "User: #{key}" }
```


```ruby
h.default_proc # => #<Proc:0x007f85f2250fd8@-:7>
```


```ruby
h = Hash.new {|obj, key| obj[key] = key * 4 } # => {}
h[1] # => 4
h[2] # => 8
h    # => {1=>4, 2=>8}
```


```ruby
h.default_proc.call(Array.new, 9) # => 36
h.default_proc.call([], 9) # => 36
h.default_proc.call({}, 9) # => 36
```


```ruby
h = Hash.new { |hash, key| hash[key] = "User: #{key}" }
h.default_proc # => #<Proc:0x007feea39bbd80@-:7>
h[1] # => "User: 1"

# Yeni prosedür veriyoruz
h.default_proc = proc do |hash, key|
  hash[key] = "hello #{key}"
end
h # => {1=>"User: 1"}
h[2] # => "hello 2"
h # => {1=>"User: 1", 2=>"hello 2"}
```


```ruby
h = { "a" => 1, "b" => 2, :c => "c" }
h["a"] # => 1
h.compare_by_identity? # => false
h.compare_by_identity  # => {"a"=>1, "b"=>2, :c=>"c"}
h.compare_by_identity? # => true

# acaba key ile value benziyormu?
h["a"]                 # => nil

# burada benzer :)
h[:c]                  # => "c"
```


