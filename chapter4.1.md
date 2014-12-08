# Chapter 4.1

## Methods

```ruby
def merhaba
  "Merhaba"
end

merhaba        # => "Merhaba"
```


```ruby
def merhaba
  "Merhaba"
end

merhaba # => "Merhaba"

undef merhaba

merhaba # =>
# ~> -:9:in `<main>': undefined local variable or method `merhaba' for main:Object (NameError)
```


```ruby
def merhaba(isim)
  "Merhaba #{isim}"
end

merhaba("vigo") # => "Merhaba vigo"
```


```ruby
def merhaba isim
  "Merhaba #{isim}"
end

merhaba "vigo" # => "Merhaba vigo"
```


## Method Yazma Kuralları (_Method Conventions_)

```ruby
a = "ali"
b = "ali"

a.eql? b  # => true
a.eql?(b) # => true
```


```ruby
a = "deneme"

a.upcase   # => "DENEME"
a          # => "deneme"

a.upcase!  # => "DENEME"
a          # => "DENEME"
```


```ruby
class User
  def email=(email)
    @email = email
  end
end

u = User.new
u # => #<User:0x007ff7229ed880>

u.email = "vigo@xyz.com"
u # => #<User:0x007ff7229ed880 @email="vigo@xyz.com">
```


## Varsayılan Argümanlar (_Default Arguments_)

```ruby
def merhaba(isim="insalık!")
  "Merhaba #{isim}"
end

merhaba          # => "Merhaba insalık!"
merhaba("vigo")  # => "Merhaba vigo"
```


## Değişken Argümanları (_Variable Arguments_)

```ruby
def merhaba(*isimler)
  "Merhaba #{isimler.join(" ve ")}"
end

merhaba("vigo")                        # => "Merhaba vigo"
merhaba("vigo", "yeşim", "ezel")       # => "Merhaba vigo ve yeşim ve ezel"

merhaba "dünya", "uzay", "evren", "ay" # => "Merhaba dünya ve uzay ve evren ve ay"
```


```ruby
def custom_numbers(first, second, *others)
  puts "ilk sayı: #{first}"
  puts "ikinci sayı : #{second}"
  puts "diğer sayılar : #{others.join(",")}"
end

custom_numbers 1,2,50,100 # => nil
# >> ilk sayı: 1
# >> ikinci sayı : 2
# >> diğer sayılar : 50,100
```


## Method’a Takma İsim Vermek (_Aliasing_)

```ruby
def merhaba(isim)
  "Merhaba! #{isim}"
end

alias naber merhaba

merhaba "Uğur" # => "Merhaba! Uğur"
naber "Uğur"   # => "Merhaba! Uğur"
```


