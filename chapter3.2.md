# Chapter 3.2

## Değişkenler

```ruby
a = 5
user_email = "example@foo.com"
```


```ruby
a = 41
puts "Siz tam #{a} yaşındasınız"
```


```ruby
a = 41
puts 'Siz tam #{a} yaşındasınız'
```


## Local (Bölgesel)

```ruby
out_text = "vigo"
def greet_user(user_name)
  out_text = "Merhaba #{user_name}"
  puts out_text
end

puts out_text       # vigo
greet_user("vigo")  # Merhaba vigo
```


## Global (Genel)

```ruby
$today = "Pazartesi"
def greet_user(user_name)
  out_text = "Merhaba #{user_name}, bugün #{$today}"
  puts out_text
end

puts "Bugün günlerden ne? #{$today}"
greet_user("vigo")  # Merhaba vigo, bugün Pazartesi
```


## Constants (Sabitler)

```ruby
My_Age = 18
your_age = 22

puts defined?(My_Age)    # constant
puts defined?(your_age)  # local-variable
```


```ruby
My_Age = 18

puts defined?(My_Age)    # constant
puts "My_Age: #{My_Age}" # My_Age: 18

My_Age = 22

puts defined?(My_Age)    # constant
puts "My_Age: #{My_Age}" # My_Age: 22
```


## Paralel Atama

```ruby
x, y, z = 5, 11, 88
puts x # 5
puts y # 11
puts z # 88

a, b, c = "Uğur", 5.81, 1972
puts a # Uğur
puts b # 5.81
puts c # 1972
```


## Instance Variable

```ruby
class User
  attr_accessor :name
  def initialize(name)
    @name = name
  end

  def greet
    "Merhaba #{@name}"
  end
end

u = User.new("Uğur")
puts u.greet         # Merhaba Uğur
puts u.name          # Uğur
```


## Class Variable

```ruby
class User
  attr_accessor :name
  @@instance_count = 0   # Kullanmadan önce init ettim
  def initialize(name)
    @name = name
    @@instance_count += 1 # Class'dan her instance oluşmasında sayacı 1 arttırıyorum
  end

  def greet
    "Merhaba #{@name}"
  end

  def self.instance_count # burası öneli
    @@instance_count
  end
end

user1 = User.new("Uğur")
user2 = User.new("Ezel")
user3 = User.new("Yeşim")

puts "Kaç defa User instance'ı oldu? #{User.instance_count}" # Kaç defa User instance'ı oldu? 3
```
