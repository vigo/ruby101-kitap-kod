# Chapter 5.4

## Array (Dizi)

```ruby
a = []  # Ya bu şekilde
a.class # => Array

b = Array.new # => Ya da bu şekilde
b.class       # => Array
```


```ruby
a = Array.new(5)  # içinde 5 eleman taşıyacak Array oluştur
a # => [nil, nil, nil, nil, nil]
```


```ruby
aylar = Array.new(12, "ay") # 12 eleman olsun ve hepsi "ay" olsun
aylar # => ["ay", "ay", "ay", "ay", "ay", "ay", "ay", "ay", "ay", "ay", "ay", "ay"]
```


```ruby
[1, 2, 3].hash   # => 3384159031637530117
[1, 2, 3].__id__ # => 70147646473880
```


```ruby
dizi = Array.new(10) { |eleman| eleman = eleman * 4 }
dizi # => [0, 4, 8, 12, 16, 20, 24, 28, 32, 36]

# ya da aynı kodu

dizi = Array.new(10) do |eleman|
  eleman = eleman * 4
end
dizi # => [0, 4, 8, 12, 16, 20, 24, 28, 32, 36]
```


```ruby
aylar = Array.[]("oca", "şub", "mar", "nis", "may", "haz", "tem", "ağu", "eyl", "eki", "kas", "ara")
aylar # => ["oca", "şub", "mar", "nis", "may", "haz", "tem", "ağu", "eyl", "eki", "kas", "ara"]
```


```ruby
years = Array(1984..2000)
years # => [1984, 1985, 1986, 1987, 1988, 1989, 1990, 1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998, 1999, 2000]
```


```ruby
a = ["Hello", :word, 2014, 3.14] # içinde String, Symbol, Fixnum ve Float var!
a # => ["Hello", :word, 2014, 3.14]
```


```ruby
a = ["Uğur", "Yeşim", "Ezel", "Ömer"]
a[0]                       # => "Uğur"
a.fetch(0)                 # => "Uğur"

a[4]                       # => nil
a.fetch(4, "Hatalı Index") # => "Hatalı Index"

a = [1, 2, 3, 4]           # İlk N elemanı al
a.take(2)                  # => [1, 2]

a.drop(2) # => [3, 4]      # take'in tersi... İlk 2 haricini al
```


```ruby
isimler = ["Uğur", "Ömer", "Yeşim", "Ezel", "Eren"]
isimler.values_at(0)         # => ["Uğur"]
isimler.values_at(1, 2)      # => ["Ömer", "Yeşim"]

["a", "b", "c", "d", "e"].at(1)  # => "b"
["a", "b", "c", "d", "e"].at(-1) # => "e"
```


```ruby
a = [ "a", "b", "b", "b", "c" ]

a.rindex("b") # => 3 # 3 tane b var, en sağdaki son b'yi verdi!
a.rindex("z") # => nil
```


## Class Method’ları

```ruby
Array.methods # => [:[], :try_convert, :allocate, :new, :superclass, :freeze, :===, :==, :<=>, :<, :<=, :>, :>=, :to_s, :inspect, :included_modules, :include?, :name, :ancestors, :instance_methods, :public_instance_methods, :protected_instance_methods, :private_instance_methods, :constants, :const_get, :const_set, :const_defined?, :const_missing, :class_variables, :remove_class_variable, :class_variable_get, :class_variable_set, :class_variable_defined?, :public_constant, :private_constant, :singleton_class?, :include, :prepend, :module_exec, :class_exec, :module_eval, :class_eval, :method_defined?, :public_method_defined?, :private_method_defined?, :protected_method_defined?, :public_class_method, :private_class_method, :autoload, :autoload?, :instance_method, :public_instance_method, :nil?, :=~, :!~, :eql?, :hash, :class, :singleton_class, :clone, :dup, :taint, :tainted?, :untaint, :untrust, :untrusted?, :trust, :frozen?, :methods, :singleton_methods, :protected_methods, :private_methods, :public_methods, :instance_variables, :instance_variable_get, :instance_variable_set, :instance_variable_defined?, :remove_instance_variable, :instance_of?, :kind_of?, :is_a?, :tap, :send, :public_send, :respond_to?, :extend, :display, :method, :public_method, :singleton_method, :define_singleton_method, :object_id, :to_enum, :enum_for, :equal?, :!, :!=, :instance_eval, :instance_exec, :__send__, :__id__]
```


## Instance Method'ları

```ruby
Array.new.methods # => [:inspect, :to_s, :to_a, :to_h, :to_ary, :frozen?, :==, :eql?, :hash, :[], :[]=, :at, :fetch, :first, :last, :concat, :<<, :push, :pop, :shift, :unshift, :insert, :each, :each_index, :reverse_each, :length, :size, :empty?, :find_index, :index, :rindex, :join, :reverse, :reverse!, :rotate, :rotate!, :sort, :sort!, :sort_by!, :collect, :collect!, :map, :map!, :select, :select!, :keep_if, :values_at, :delete, :delete_at, :delete_if, :reject, :reject!, :zip, :transpose, :replace, :clear, :fill, :include?, :<=>, :slice, :slice!, :assoc, :rassoc, :+, :*, :-, :&, :|, :uniq, :uniq!, :compact, :compact!, :flatten, :flatten!, :count, :shuffle!, :shuffle, :sample, :cycle, :permutation, :combination, :repeated_permutation, :repeated_combination, :product, :take, :take_while, :drop, :drop_while, :bsearch, :pack, :entries, :sort_by, :grep, :find, :detect, :find_all, :flat_map, :collect_concat, :inject, :reduce, :partition, :group_by, :all?, :any?, :one?, :none?, :min, :max, :minmax, :min_by, :max_by, :minmax_by, :member?, :each_with_index, :each_entry, :each_slice, :each_cons, :each_with_object, :chunk, :slice_before, :lazy, :nil?, :===, :=~, :!~, :class, :singleton_class, :clone, :dup, :taint, :tainted?, :untaint, :untrust, :untrusted?, :trust, :freeze, :methods, :singleton_methods, :protected_methods, :private_methods, :public_methods, :instance_variables, :instance_variable_get, :instance_variable_set, :instance_variable_defined?, :remove_instance_variable, :instance_of?, :kind_of?, :is_a?, :tap, :send, :public_send, :respond_to?, :extend, :display, :method, :public_method, :singleton_method, :define_singleton_method, :object_id, :to_enum, :enum_for, :equal?, :!, :!=, :instance_eval, :instance_exec, :__send__, :__id__]
```


```ruby
Array.class # => Class
Array.class.superclass # => Module
Array.class.superclass.superclass # => Object
Array.class.superclass.superclass.superclass # => BasicObject
Array.class.superclass.superclass.superclass.superclass # => nil
```


```ruby
Array.included_modules # => [Enumerable, Kernel]
```


```ruby
[1, 2, 3, 4].length # => 4
[1, 2, 3, 4].count  # => 4
```


```ruby
[1, 2, 3, 4].empty? # => false
[].empty?           # => true
```


```ruby
a = ["Uğur", "Yeşim", "Ezel", "Ömer"]

a.eql?(["Yeşim", "Ezel", "Ömer", "Uğur"]) # => false
a.eql?([])                                # => false
a.eql?(["Uğur", "Yeşim", "Ezel", "Ömer"]) # => true
```


```ruby
5.class.superclass # => Integer
Integer === 5      # => true
# 5, Integer subsetinde...

Integer.class # => Class
Integer.class.superclass # => Module
Integer.class.superclass.superclass # => Object
Integer.class.superclass.superclass.superclass # => BasicObject
Integer.class.superclass.superclass.superclass.superclass # => nil

# Integer, 5'in subsetinde değil.
5 === Integer      # => false
```


```ruby
[1, 2, 3, 4].include?(3)                   # => true

[1, 2, 3, 4].member?(1) # => true
[1, 2, 3, 4].member?(5) # => false

["Uğur", "Ezel", "Yeşim"].include?("Uğur") # => true
["Uğur", "Ezel", "Yeşim"].include?("Ömer") # => false
```


```ruby
a = [1, 2, 3, 4]
b = [3, 1, 10, 22]
a & b # => [1, 3]
```


```ruby
a = ["a", "b", "c"]
a * 5 # => ["a", "b", "c", "a", "b", "c", "a", "b", "c", "a", "b", "c", "a", "b", "c"]

a * "-vigo-" # => "a-vigo-b-vigo-c"
```


```ruby
a = ["Uğur", "Yeşim", "Ezel"]
b = ["Ömer"]

a + b # => ["Uğur", "Yeşim", "Ezel", "Ömer"]
```


```ruby
a = ["Uğur", "Yeşim", "Ezel"]
b = ["Uğur", "Yeşim"]

a - b # => ["Ezel"] # a'da olab b elemanları kayboldu
```


```ruby
a = ["Uğur", "Yeşim", "Ezel"]
b = ["Uğur", "Ömer"]

a | b # => ["Uğur", "Yeşim", "Ezel", "Ömer"]
```


```ruby
a = ["Uğur", "Yeşim", "Ezel"]
a << "Ömer"     # => ["Uğur", "Yeşim", "Ezel", "Ömer"]
a.push("Eren")  # => ["Uğur", "Yeşim", "Ezel", "Ömer", "Eren"]
```


```ruby
a.push("Tunç").push("Suat")  # => ["Uğur", "Yeşim", "Ezel", "Ömer", "Eren", "Tunç", "Suat"]
```


```ruby
a = [1, 2, 3]
a.concat([4, 5, 6])
a # => [1, 2, 3, 4, 5, 6]
```


```ruby
["Commodore 64", "Amiga", "Sinclair", "Amstrad"].join        # => "Commodore 64AmigaSinclairAmstrad"
["Commodore 64", "Amiga", "Sinclair", "Amstrad"].join(" , ") # => "Commodore 64 , Amiga , Sinclair , Amstrad"
```


```ruby
a = ["Uğur", "Yeşim", "Ezel"]
a.unshift("Ömer") # => ["Ömer", "Uğur", "Yeşim", "Ezel"]
```


```ruby
a = ["Uğur", "Yeşim", "Ezel"]
a.insert(1, "Ömer") # => ["Uğur", "Ömer", "Yeşim", "Ezel"]
a.insert(1, "Ahmet", "Ece", "Eren") # => ["Uğur", "Ahmet", "Ece", "Eren", "Ömer", "Yeşim", "Ezel"]
```


```ruby
a = ["Uğur", "Yeşim", "Ezel", "Ömer"]
a.replace(["Foo", "Bar"]) # => ["Foo", "Bar"]
a                         # => ["Foo", "Bar"]
```


```ruby
[1, 2, 3, 4] <=> [1, 2, 3, 4] # => 0 # Eşit
[1, 2, 3, 4] <=> [1, 2, 3]    # => 1 # İlk değer büyük
[1, 2, 3] <=> [1, 2, 3, 4]    # => -1 # İlk değer küçük
```


```ruby
a = ["Uğur", "Ömer", "Yeşim", "Ezel", "Eren"]
a.pop              # => "Eren"
a                  # => ["Uğur", "Ömer", "Yeşim", "Ezel"]
a.shift            # => "Uğur"
a                  # => ["Ömer", "Yeşim", "Ezel"]
a.delete("Ömer")   # => "Ömer"
a                  # => ["Yeşim", "Ezel"]
a.delete_at(1)     # => "Ezel"
a                  # => ["Yeşim"]

# not 50'den küçükse sil :)
notlar = [40, 45, 53, 70, 99, 65]
notlar.delete_if { |notu| notu < 50 } # => [53, 70, 99, 65]
```


```ruby
a = ["Uğur", "Ömer", "Yeşim", "Ezel", "Eren"]
a.pop(2) # => ["Ezel", "Eren"]
a        # => ["Uğur", "Ömer", "Yeşim"]
```


```ruby
["a", 1, nil, 2, nil, "b", 1, "a"].compact         # => ["a", 1, 2, "b", 1, "a"]
["a", 1, nil, 2, nil, "b", 1, "a"].uniq            # => ["a", 1, nil, 2, "b"]
["a", 1, nil, 2, nil, "b", 1, "a"].compact.uniq    # => ["a", 1, 2, "b"]
```


```ruby
[1, 2, 3, 4] == [1, 2, 3, 4]   # => true
[1, 2, 3, 4] == ["1", 2, 3, 4] # => false
[1, 2, 3, 4] == [1, 2, 3]      # => false
```


```ruby
a = ["renkler", "kırmızı", "sarı", "mavi"]
b = ["harfler", "a", "b", "c"]
c = "foo"

t  = [a, b, c]
t                 # => [["renkler", "kırmızı", "sarı", "mavi"], ["harfler", "a", "b", "c"], "foo"]
t.assoc("renkler") # => ["renkler", "kırmızı", "sarı", "mavi"]
t.assoc("foo")     # => nil

t.rassoc("kırmızı")   # => ["renkler", "kırmızı", "sarı", "mavi"]
```


```ruby
[1, 2, 3, 4].slice(0, 2) # => [1, 2] # 0.dan itibaren 2 tane
[1, 2, 3, 4].slice(2..4) # => [3, 4] # 2.den itibaren 2 tane
```


```ruby
a = [1, 2, 3, 4, 5]
a.first # => 1
a.last # => 5
```


```ruby
a = [1, 2, 3, 4, 5]
a.first(2) # => [1, 2]
a.last(2)  # => [4, 5]
```


```ruby
["Uğur", "Yeşim", "Ezel", "Ömer"].find { |n| n.length > 3 } # => "Uğur"
["Uğur", "Yeşim", "Ezel", "Ömer"].find_all { |n| n.length > 3 } # => ["Uğur", "Yeşim", "Ezel", "Ömer"]
```


```ruby
["a", "b", "c", "d", "e"].index("e")                 # => 4
["Uğur", "Yeşim", "Ezel", "Ömer"].index("Ezel")      # => 2
["Uğur", "Yeşim", "Ezel", "Ömer"].find_index("Ezel") # => 2
```


```ruby
a = [1, 2, 3]
a.clear # => []
a       # => []
```


```ruby
a = [1, 2, 3, 4, 5]
a.reverse # => [5, 4, 3, 2, 1]
```


```ruby
a = [1, 2, 3, 4, 5]
a.sample    # => 3
a.sample(3) # => [5, 1, 3]
```


```ruby
a = [1, 2, 3, 4, 5]
a.shuffle # => [5, 4, 1, 3, 2]
a.shuffle # => [1, 2, 3, 5, 4]
```


```ruby
a = [1, 4, 2, 3, 11, 5]
a.sort # => [1, 2, 3, 4, 5, 11]

b = ["a", "c", "b", "z", "d"]
b.sort # => ["a", "b", "c", "d", "z"]
```


```ruby
a = ["Uğur", "Yeşim", "Ezel", "Ömer"]
a.fill("x")       # => ["x", "x", "x", "x"] # tüm elemanları x yaptı
a                 # => ["x", "x", "x", "x"] # artık a'nın yeni değeri bu

a = ["Uğur", "Yeşim", "Ezel", "Ömer"]
a.fill("y", 2)    # => ["Uğur", "Yeşim", "y", "y"] # 2.den itibaren y ile doldur

a = ["Uğur", "Yeşim", "Ezel", "Ömer"] # 2.den itibaren 1 tane doldur
a.fill("z", 2, 1) # => ["Uğur", "Yeşim", "z", "Ömer"]
```


```ruby
a = [1, 2, 3, 4, 5]
a.fill { |i| i * 5 }     # => [0, 5, 10, 15, 20]
a                        # => [0, 5, 10, 15, 20]
```


```ruby
[1, 2, ["a", "b", :c], [66, [5.5, 3.1]]].flatten # => [1, 2, "a", "b", :c, 66, 5.5, 3.1]
```


```ruby
a = [1, 2, 3, 4, 5]

a.rotate    # => [2, 3, 4, 5, 1] # 1 kaydırdı
a.rotate(2) # => [3, 4, 5, 1, 2] # 2 kaydırdı, ilk 2 elemanı sona koydu!
```


```ruby
a = [ 4, 5, 6 ]
b = [ 7, 8, 9 ]

[1, 2, 3].zip(a, b)   # => [[1, 4, 7], [2, 5, 8], [3, 6, 9]]
[1, 2].zip(a, b)      # => [[1, 4, 7], [2, 5, 8]]
a.zip([1, 2], [8])    # => [[4, 1, 8], [5, 2, nil], [6, nil, nil]]
```


```ruby
a = [[1, 2], [3, 4], [5, 6]]
a.transpose   # => [[1, 3, 5], [2, 4, 6]]

# [
#   [1, 2],
#   [3, 4],
#   [5, 6]
# ]
# -> [1, 3, 5], [2, 4, 5]
#
```


```ruby
["a", 1, "b", 2].to_a       # => ["a", 1, "b", 2]
["a", 1, "b", 2].to_ary     # => ["a", 1, "b", 2]
[["a", 1], ["b", 2]].to_h   # => {"a"=>1, "b"=>2}
["a", 1, "b", 2].to_s       # => "[\"a\", 1, \"b\", 2]"
["a", 1, "b", 2].inspect    # => "[\"a\", 1, \"b\", 2]"
```


```ruby
(1..3)         # => 1..3
(1..3).entries # => [1, 2, 3]
(1..3).to_a    # => [1, 2, 3]
```


```ruby
(1..10).to_a        # => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# 2'den 5'e kadar (5 dahil)
(1..10).grep 2..5   # => [2, 3, 4, 5]

# sadece .com olan elemanları al
["a", "http://example.com", "b", "foo", "http://webbox.io"].grep(/^http.+\.com/) # => ["http://example.com"]
```


```ruby
# A: String olarak işle, space karakteri kullan
# 5: Uzunluğu 5 karakter olsun
["a", "b", "c"].pack("A5A5A5")            # => "a    b    c    "

# Uzunluğu 5'ten büyük olan kesintiye uğradı
["ali", "burak", "cengiz"].pack("A5A5A5") # => "ali  burakcengi"

# a: String olarak işle, null yani \x00 karakteri kullan
["a", "b", "c"].pack("a3a3a3")            # => "a\x00\x00b\x00\x00c\x00\x00"
```


## İterasyon ve Block Kullanımı

```ruby
a = [1, 2, 3, 4, 5]
a.collect { |i| i * 2 }       # => [2, 4, 6, 8, 10]
a.collect { |i| "sayı #{i}" } # => ["sayı 1", "sayı 2", "sayı 3", "sayı 4", "sayı 5"]
```


```ruby
["Uğur", "Yeşim", "Ezel", "Ömer"].map { |isim| "İsim: #{isim}" } # => ["İsim: Uğur", "İsim: Yeşim", "İsim: Ezel", "İsim: Ömer"]
["Uğur", "Yeşim", "Ezel", "Ömer"].collect { |isim| "İsim: #{isim}" } # => ["İsim: Uğur", "İsim: Yeşim", "İsim: Ezel", "İsim: Ömer"]
```


```ruby
[1, 2, 3, 10, 15, 20].select { |n| n % 2 == 0 } # => [2, 10, 20] # 2'ye tam bölünenler
[1, 2, "3", "ali", 15, 20].select { |n| n.is_a?(Fixnum) } # => [1, 2, 15, 20] # sadece sayılar
```


```ruby
[1, 2, 3, 10, 15, 20].reject { |n| n % 2 == 0 } # => [1, 3, 15] # 2'ye tam bölülenleri at
[1, 2, "3", "ali", 15, 20].reject { |n| n.is_a?(Fixnum) } # => ["3", "ali"] # Sayı olanları at
```


```ruby
a = [1, 2, 3, 10, 15, 20]
a.keep_if { |n| n % 2 == 0 } # => [2, 10, 20] # 2'ye bölünemeyenler false geldiği için düştüler.
a # => [2, 10, 20] # a artık bu!
```


```ruby
a = [1, 2, 3]
a.combination(1).to_a # => [[1], [2], [3]]
a.combination(2).to_a # => [[1, 2], [1, 3], [2, 3]]

a.combination(2) { |c| puts "Olasıklar: #{c.join(" ve ")}" }

# Olasıklar: 1 ve 2
# Olasıklar: 1 ve 3
# Olasıklar: 2 ve 3
```


```ruby
[1, 2, 3].permutation.to_a # => [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]]
```


```ruby
[1, 2, 3].permutation(1).to_a # => [[1], [2], [3]]
[1, 2, 3].permutation(2).to_a # => [[1, 2], [1, 3], [2, 1], [2, 3], [3, 1], [3, 2]]
```


```ruby
[1, 2, 3].combination(1).to_a # => [[1], [2], [3]]
[1, 2, 3].repeated_combination(1).to_a # => [[1], [2], [3]]

[1, 2, 3].combination(2).to_a # => [[1, 2], [1, 3], [2, 3]]
[1, 2, 3].repeated_combination(2).to_a # => [[1, 1], [1, 2], [1, 3], [2, 2], [2, 3], [3, 3]]
```


```ruby
[1, 2, 3].permutation(1).to_a # => [[1], [2], [3]]
[1, 2, 3].repeated_permutation(1).to_a # => [[1], [2], [3]]

[1, 2, 3].permutation(2).to_a # => [[1, 2], [1, 3], [2, 1], [2, 3], [3, 1], [3, 2]]
[1, 2, 3].repeated_permutation(2).to_a # => [[1, 1], [1, 2], [1, 3], [2, 1], [2, 2], [2, 3], [3, 1], [3, 2], [3, 3]]
```


```ruby
[1, 2, 3].product            # => [[1], [2], [3]]
[1, 2, 3].product([4, 5])    # => [[1, 4], [1, 5], [2, 4], [2, 5], [3, 4], [3, 5]]
[1, 2, 3].product([7, 8, 9]) # => [[1, 7], [1, 8], [1, 9], [2, 7], [2, 8], [2, 9], [3, 7], [3, 8], [3, 9]]
[1, 2, 3].product(["a", "b"], ["x", "y"]) # => [[1, "a", "x"], [1, "a", "y"], [1, "b", "x"], [1, "b", "y"], [2, "a", "x"], [2, "a", "y"], [2, "b", "x"], [2, "b", "y"], [3, "a", "x"], [3, "a", "y"], [3, "b", "x"], [3, "b", "y"]]
```


```ruby
a = [1, 2, 3, 4, 2]

a.count                    # => 5 # eleman sayısı
a.count(2)                 # => 2 # kaç tane 2 var?
a.count { |n| n % 2 == 0 } # => 3 # kaç tane 2'ye tam bölünen var?
```


```ruby
a = [1, 2, 3]

a.cycle(2).to_a # => [1, 2, 3, 1, 2, 3] # 2 defa
a.cycle(4).to_a # => [1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3] # 3defa
a.cycle(2) { |o| puts "Sayı #{o}" }

# Sayı 1
# Sayı 2
# Sayı 3
# Sayı 1
# Sayı 2
# Sayı 3
```


```ruby
notlar = [40, 45, 53, 70, 99, 65]
notlar.drop_while {|notu| notu < 50 }   # => [53, 70, 99, 65]
```


```ruby
notlar = [40, 45, 53, 70, 99, 65]
notlar.take_while { |notu| notu < 50 } # => [40, 45]
```


```ruby
a = ["Uğur", "Yeşim", "Ezel", "Ömer"]

a.each # => #<Enumerator: ["Uğur", "Yeşim", "Ezel", "Ömer"]:each>
a.each { |isim| puts "İsim: #{isim}" }

# İsim: Uğur
# İsim: Yeşim
# İsim: Ezel
# İsim: Ömer
```


```ruby
a = ["Uğur", "Yeşim", "Ezel", "Ömer"]

a.each_index # => #<Enumerator: ["Uğur", "Yeşim", "Ezel", "Ömer"]:each_index>
a.each_index.to_a # => [0, 1, 2, 3]
a.each_index { |i| puts "Index: #{i}, Değeri: #{a[i]}" }

# Index: 0, Değeri: Uğur
# Index: 1, Değeri: Yeşim
# Index: 2, Değeri: Ezel
# Index: 3, Değeri: Ömer
```


```ruby
a = ["Uğur", "Yeşim", "Ezel", "Ömer"]
a.each_with_index { |eleman, index| puts "index: #{index}, eleman: #{eleman}" }

# index: 0, eleman: Uğur
# index: 1, eleman: Yeşim
# index: 2, eleman: Ezel
# index: 3, eleman: Ömer
```


```ruby
a = ["Uğur", "Yeşim", "Ezel", "Ömer"]
a.each_slice(2) # => #<Enumerator: ["Uğur", "Yeşim", "Ezel", "Ömer"]:each_slice(2)>
a.each_slice(2).to_a # => [["Uğur", "Yeşim"], ["Ezel", "Ömer"]]
a.each_slice(2) { |ikili_grup| puts "#{ikili_grup}" }

# ["Uğur", "Yeşim"]
# ["Ezel", "Ömer"]
```


```ruby
# 3'lü üret
[1, 2, 3, 4, 5,6].each_cons(3).to_a # => [[1, 2, 3], [2, 3, 4], [3, 4, 5], [4, 5, 6]]

# 4'lü üret
[1, 2, 3, 4, 5,6].each_cons(4).to_a # => [[1, 2, 3, 4], [2, 3, 4, 5], [3, 4, 5, 6]]
```


```ruby
[1, 2, 3, 4].each_with_object([]) { |number, given_object|
  given_object << number * 2
} # => [2, 4, 6, 8]
```


```ruby
computers = ["Commodore 64", "Amiga", "Sinclair", "Amstrad"]
computers.reverse_each # => #<Enumerator: ["Commodore 64", "Amiga", "Sinclair", "Amstrad"]:reverse_each>
computers.reverse_each.to_a # => ["Amstrad", "Sinclair", "Amiga", "Commodore 64"]

computers.reverse_each { |c| puts "Bilgisayar: #{c}" }

# Bilgisayar: Amstrad
# Bilgisayar: Sinclair
# Bilgisayar: Amiga
# Bilgisayar: Commodore 64
```


```ruby
computers = ["Commodore 64", "Amiga", "Sinclair", "Amstrad"]
computers.find_index { |c| c == "Amstrad" } # => 3
```


```ruby
a = ["Uğur", "Yeşim", "Ezel", "Ömer"]
a.freeze
a << "Fazilet"  # Yeni isim eklemek mümkün değildir!
```

    RuntimeError: can't modify frozen Array

```ruby
a = ["Uğur", "Yeşim", "Ezel", "Ömer"]
a.freeze  # => ["Uğur", "Yeşim", "Ezel", "Ömer"]
a.frozen? # => true
```


```ruby
a = ["Uğur", "Yeşim", "Ezel", "Ömer"]
a.freeze  # => ["Uğur", "Yeşim", "Ezel", "Ömer"]
a.frozen? # => true
```


```ruby
a = [6, 1, 8, 4, 11]
a.min # => 1
a.max # => 11
```


```ruby
m = ["a", "ab", "abc", "abcd"]
m.min # => "a"
m.max # => "abcd"
```


```ruby
m = ["a", "ab", "abc", "abcd", "111111111"]

m.min # => "111111111" # ?
m.max # => "abcd"
```


```ruby
m = ["a", "ab", "abc", "abcd", "111111111"]
m.min { |a, b| a.length <=> b.length }  # => "a"
m.max                                   # => "abcd"
```


```ruby
m = ["a", "ab", "abc", "abcd", "111111111"]
m.min_by { |x| x.length }   # => "a"
m.max_by { |x| x.length }   # => "111111111"
```


```ruby
m = ["a", "ab", "abc", "abcd"]
m.min    # => "a"
m.max    # => "abcd"
m.minmax # => ["a", "abcd"]
```


```ruby
m = ["a", "ab", "abc", "abcd"]
m.minmax_by { |x| x.length } # => ["a", "abcd"]
```


```ruby
# acaba hayvanlar dizisindeki isimlerin hepsinin uzunluğu
# en az 2 karakter mi?

hayvanlar = ["Kedi", "Köpek", "Kuş", "Kurbağa", "Kaplumbağa"]
hayvanlar.all? { |hayvan_ismi| hayvan_ismi.length >= 2 } # => true

# Acaba ilk karfleri K harfimi?

hayvanlar.all? { |hayvan_ismi| hayvan_ismi.start_with?("K") } # => true

# Elemanların her biri true mu?
[true, false, nil].all? # => false
```


```ruby
# En azından bir hayvan ismi A ile başlıyor mu?

hayvanlar = ["Kedi", "Köpek", "At", "Yılan", "Balık"]
hayvanlar.any?{ |hayvan_ismi| hayvan_ismi.start_with?("A") } # => true
```


```ruby
hayvanlar = ["Kedi", "Köpek", "At", "Yılan", "Balık", "Kaplumbağa"]

# Sadece bir ismin uzunluğu 6 karaterten büyük olmalı!
hayvanlar.one?{ |hayvan_ismi| hayvan_ismi.length > 6 } # => true

# Uzunluğu 3'ten büyük 5 isim olduğu için false döndü!
hayvanlar.one?{ |hayvan_ismi| hayvan_ismi.length > 3 } # => false
```


```ruby
hayvanlar = ["Kedi", "Köpek", "At", "Yılan", "Balık", "Kaplumbağa"]

# Hiçbir ismin uzunluğu 2 karakter olmamalı ? false. At'ın uzunluğu 2
hayvanlar.none?{ |hayvan_ismi| hayvan_ismi.length == 2 } # => false

# C ile başlayan hayvan ismi olmasın! true. Hiçbir isim C ile başlamıyor
hayvanlar.none?{ |hayvan_ismi| hayvan_ismi.start_with?("C") } # => true
```


```ruby
[1, 2, 3, 4, 5].inject{ |toplam, eleman| toplam + eleman } # => 15

# işlem şu şekilde ilerliyor
# toplam: 0, eleman: 1
# toplam: 1, eleman: 2
# toplam: 3, eleman: 3
# toplam: 6, eleman: 4
# toplam: 10, eleman: 5
# sona geldiğinde toplam 10, eleman 5 -> 10 + 5 = 15
```


```ruby
[1, 2, 3, 4, 5].inject(10){ |toplam, eleman| toplam + eleman } # => 25

# toplam: 10, eleman: 1
# toplam: 11, eleman: 2
# toplam: 13, eleman: 3
# toplam: 16, eleman: 4
# toplam: 20, eleman: 5
# sona geldiğinde toplam 20, eleman 5 -> 20 + 5 = 25
```


```ruby
[1, 2, 3, 4, 5].reduce(:+) # => 15
```


```ruby
en_uzun_hayvan_ismi = ["kedi", "köpek", "kamplumbağa"].inject do |buffer, hayvan|
   buffer.length > hayvan.length ? buffer : hayvan
end

en_uzun_hayvan_ismi # => "kamplumbağa"
```


```ruby
[1, 2, 3, 4, 5, 6].partition{ |n| n.even? } # => [[2, 4, 6], [1, 3, 5]]

# Çift sayılar, true_array yani ilk parça:    [2, 4, 6]
# Tek sayılar, false_array yani ikinci parça: [1, 3, 5]

# Sadece çift sayılar gelsin:
[1, 2, 3, 4, 5, 6].partition{ |n| n.even? }[0] # => [2, 4, 6]
```


```ruby
[1, 2, 3, 4, 5, 6].group_by{ |n| n % 3 } # => {1=>[1, 4], 2=>[2, 5], 0=>[3, 6]}

# 3'e bölünce kalanı;
# 1 olanlar: [1, 4]
# 2 olanlar: [2, 5]
# 0 olanlar (tam bölünenler) : [3, 6]
```


```ruby
notlar = [50, 20, 44, 60, 80, 100, 99, 81, 5]
notlar.group_by{ |notu| notu > 40 }[true] # => [50, 44, 60, 80, 100, 99, 81]
```


```ruby
[3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5].chunk { |n| n.even? }.to_a

# => [
#  [false, [3, 1]],
#  [true, [4]],
#  [false, [1, 5, 9]],
#  [true, [2, 6]],
#  [false, [5, 3, 5]]
# ]
```


```ruby
[1, 2, 3, 'a' , 4, 5, 6, 'a' , 7 , 8 , 9 , 'a' , 1 , 3 , 5].slice_before {|i| i == 'a'}.to_a
# => [[1, 2, 3], ["a", 4, 5, 6], ["a", 7, 8, 9], ["a", 1, 3, 5]]
```


```ruby
pos_neg = [1, 2, 3, 4, 5, 6].map { |n| [n, -n] }
pos_neg         # => [[1, -1], [2, -2], [3, -3], [4, -4], [5, -5], [6, -6]]
pos_neg.flatten # => [1, -1, 2, -2, 3, -3, 4, -4, 5, -5, 6, -6]

# yerine:
[1, 2, 3, 4, 5, 6].flat_map { |n| [n, -n] } # => [1, -1, 2, -2, 3, -3, 4, -4, 5, -5, 6, -6]
```


```ruby
hayvanlar = ["kamplumbağa", "at", "eşşek", "kurbağa", "ayı"]

# isimleri uzunluklarına göre küçükten büyüğe doğru sıralayalım
hayvanlar.sort_by{ |isim| isim.length } # => ["at", "ayı", "eşşek", "kurbağa", "kamplumbağa"]

# isimleri uzunluklarına göre büyükten küçüğe doğru sıralayalım
hayvanlar.sort_by{ |isim| -isim.length } # => ["at", "ayı", "eşşek", "kurbağa", "kamplumbağa"]
```


```ruby
# 2'den büyük 3, 4 ve 5 olmasına rağmen tek sonuç
[1, 2, 3, 4, 5].bsearch{ |n| n > 2 }  # => 3

[1, 2, 3, 4, 5].bsearch{ |n| n >= 4 } # => 4
```


## Tehlikeli İşlemler

```ruby
a = [1, 2, 3, 4, 5]
a.reverse! # => [5, 4, 3, 2, 1]

# a artık reverse edilmiş halde!
a          # => [5, 4, 3, 2, 1]
```
