# Chapter 6.1

## Enumeration ve Iteration

```ruby
["a", "b", "c"].class      # => Array
["a", "b", "c"].each.class # => Enumerator
```


```ruby
enumerator = ["a", "b", "c"].each
enumerator_with_foo = enumerator.each_with_object("foo")
enumerator_with_foo.to_a # => [["a", "foo"], ["b", "foo"], ["c", "foo"]]
```


```ruby
enumerator = ["a", "b", "c"].each
enumerator_with_foo = enumerator.each_with_object("foo")
enumerator_with_foo.each do |element, obj|
  puts "eleman: #{element}, obj: #{obj}"
end

# eleman: a, obj: foo
# eleman: b, obj: foo
# eleman: c, obj: foo
```


```ruby
sayilar = [1, 2, 3, 4].each
sayilar.next # => 1
sayilar.next # => 2
sayilar.next # => 3
sayilar.next # => 4
sayilar.next # => StopIteration hatası!
```


```ruby
["Uğur", "Yeşim", "Ezel", "Ömer"].each_with_index do |name, index|
  puts "İsim: #{name}, index: #{index}"
end
# İsim: Uğur, index: 0
# İsim: Yeşim, index: 1
# İsim: Ezel, index: 2
# İsim: Ömer, index: 3
```


```ruby
isimler = ["Uğur", "Yeşim", "Ezel", "Ömer"]
for isim in isimler
  puts "isim: #{isim}"
end
# isim: Uğur
# isim: Yeşim
# isim: Ezel
# isim: Ömer
```


```ruby
a = [1, 2, 3, 4].each
a.next        # => 1
a.next_values # => [2]
a.next_values # => [3]
```


```ruby
a = [1, 2, 3, 4].each
a.next        # => 1
a.peek        # => 2

a.next        # => 2
a.peek        # => 3

a.next        # => 3
a.peek        # => 4

a.next        # => 4
a.peek        # => StopIteration: iteration reached an end
```


```ruby
a = [1, 2, 3, 4].each
a.next        # => 1
a.next        # => 2
a.next        # => 3
a.rewind      # => #<Enumerator: [1, 2, 3, 4]:each>
a.peek_values # => [1]
a.next        # => 1
```


## Diğer Nesnelerdeki Enumeration Durumları

### Fixnum

```ruby
10.downto(5){ |i| puts "Sayı: #{i}" }
5.upto(10){ |i| puts "Sayı: #{i}" }
3.times{ |i| puts "#{i}" }
```


### String

```ruby
"A".upto("M"){ |s| puts s }
"AB".upto("AE"){ |s| puts s }
```