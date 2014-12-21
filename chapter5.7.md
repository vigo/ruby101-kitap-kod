# Chapter 5.7

## Class (Sınıf)


```ruby
class MyClass
  end

class OtherClass
end

a = MyClass.new    # => #<MyClass:0x007ffa2b09b758>
b = OtherClass.new # => #<OtherClass:0x007ffa2b09b3c0>
```


```ruby
class Merhaba
  def initialize(isim)
    @isim = isim
  end

  def selam_sana
    "Selam sana, #{@isim}"
  end
end

hey = Merhaba.new "Uğur"
hey.selam_sana # => "Selam sana, Uğur"
```


```ruby
class Person
end

jack = Person.new # => #<Person:0x007fb0521a4820>
```


```ruby
Person = Class.new do
end

jack = Person.new # => #<Person:0x007fc42c0c8648>
```


## Public Instance Method'ları

```ruby
String.superclass      # => Object
Object.superclass      # => BasicObject
BasicObject.superclass # => nil
```


## Private Instance Method'ları

```ruby
class Animal
  def self.inherited(subclass)
    puts "Yeni subclass: #{subclass}"
  end
end

class Cat < Animal
end

class Tiger < Cat
end

# Yeni subclass: Cat
# Yeni subclass: Tiger
```


## Accessors (getter + setter)

```ruby
class Person
  def name
    @name
  end
  def name=(name)
    @name = name
  end
end

vigo = Person.new  # => #<Person:0x007f903b8d0590>
vigo.name          # => nil
vigo.name = "Uğur" # => "Uğur"
vigo.name          # => "Uğur"
```


```ruby
class Person
  attr_accessor :name
end

vigo = Person.new  # => #<Person:0x007fb7c9a4c620>
vigo.name          # => nil
vigo.name = "Uğur" # => "Uğur"
vigo.name          # => "Uğur"
```


```ruby
class Person
  attr :name, true
end

Person.instance_methods - Object.instance_methods # => [:name, :name=]
```


```ruby
class Person
  attr_accessor :name
end

Person.instance_methods - Object.instance_methods # => [:name, :name=]
```


```ruby
class Person
  attr_reader :name
end

Person.instance_methods - Object.instance_methods # => [:name]

vigo = Person.new
vigo.name # => nil
vigo.name = "Uğur" # => NoMethodError: undefined method `name=' for #<Person:0x007ffe4d0e8528>
```


```ruby
class Person
  attr_writer :name
end

Person.instance_methods - Object.instance_methods # => [:name=]

vigo = Person.new
vigo.name = "Uğur" # => "Uğur"
vigo.name # => NoMethodError: undefined method ‘name’ for #<Person:0x007fb92b9d45b8 @name="Uğur">
```


```ruby
class Person
  attr_writer :name
  def initialize(name)
    @name = name
  end
  def greet
    "Hello #{@name}"
  end
end

vigo = Person.new "Uğur"
vigo.greet # => "Hello Uğur"
```


## Class Variables

```ruby
class Person
  attr_accessor :name
  @@amount = 0
  def initialize(name)
    @@amount += 1
    @name = name
  end
  def greet
    "Hello #{name}"
  end
  def how_many_people_created
    "Number of people: #{@@amount}"
  end
end

user1 = Person.new "Uğur"
user2 = Person.new "Yeşim"
user3 = Person.new "Ezel"

Person.class_variable_get(:@@amount) # => 3
user3.how_many_people_created        # => "Number of people: 3"
```


## Class Methods

```ruby
class Person
  attr_accessor :name
  @@amount = 0
  def initialize(name)
    @@amount += 1
    @name = name
  end
  def greet
    "Hello #{name}"
  end
  def how_many_people_created
    "Number of people: #{@@amount}"
  end

  def self.how_many_people_created
    "We have #{@@amount} copie(s)"
  end
end

user1 = Person.new "Uğur"
user2 = Person.new "Yeşim"
user3 = Person.new "Ezel"

Person.how_many_people_created # => "We have 3 copie(s)"
```


## Singletons

```ruby
class Area
 class << self
   def calculate(width, height)
     width * height
   end
 end
end

Area.calculate(5, 5) # => 25
```


```ruby
class Area
end

x = Area.new
def x.calculate(width, height)
  width * height
end
x.calculate 5,5 # => 25
```


## Inheritance (Miras)

```ruby
class Animal
  attr_accessor :name, :kind
  def initialize(name)
    @name = name
  end
  def say_hi
    "Hello! I'm a #{@kind}, my name is #{@name}"
  end
end

class Cat < Animal
end

class Horse < Animal
end

bidik = Cat.new "Bıdık"
bidik.kind = "cat"

zuzu = Horse.new "Zuzu"
zuzu.kind = "horse"

bidik.say_hi # => "Hello! I'm a cat, my name is Bıdık"
zuzu.say_hi  # => "Hello! I'm a horse, my name is Zuzu"
```


## Access Level (Erişim): Public, Private, ve Protected Method'lar


```ruby
class User
  def bu_sayede_private_cagirabilirim
    bu_sadece_iceriden
  end

  private
  def bu_sadece_iceriden
    puts "Bu private method. Bu method instance'dan çağırılamaz!"
  end

  protected
  def bu_sadece_subclass_veya_instance_dan
    puts "Bu proteced method."
  end
end

u = User.new
u.bu_sadece_iceriden # => NoMethodError: private method ‘bu_sadece_iceriden’ called for #<User:0x007feb9d0d2560>
```


```ruby
u.bu_sayede_private_cagirabilirim # => "Bu private method. Bu method instance'dan çağırılamaz!"
```


```ruby
u.bu_sadece_subclass_veya_instance_dan # => NoMethodError: protected method ‘bu_sadece_subclass_veya_instance_dan’ called for #<User:0x007fff131c60a0>
```


```ruby
class SuperUser < User
  def initialize
    bu_sadece_subclass_veya_instance_dan
  end
end

y = SuperUser.new # => "Bu proteced method."
```


## Method Aliasing

```ruby
class User
  attr_accessor :name
  def initialize(name)
    @name = name
  end

  def give_random_age
    (20..45).to_a.sample
  end
end

class SuperUser < User
  alias :yedek :give_random_age # üst sınıftaki give_random_age’i sakladık, yedek adını verdik
  def give_random_age
    rnd = self.yedek
    "Kendi yaşım: 43, rnd= #{rnd}"
  end
end

u = User.new "vigo"
u.name            # => "vigo"
u.give_random_age # => 29

v = SuperUser.new "Uğur"
v.give_random_age # => "Kendi yaşım: 43, rnd= 44"
```


## Sınıflar Açıktır, Modifiye Edilebilir!

```ruby
class String
  def hello
    "Hello: #{self}"
  end
end


"Deneme".hello # => "Hello: Deneme"
```


## Nested Class

```ruby
class Animal
  attr_reader :name
  def initialize(name)
    @name = name
  end
  
  class Cat < Animal
  end
  class Horse < Animal
  end
  class Uber
  end
end

horse = Animal::Horse.new "Furry"
horse.name             # => "Furry"
horse.class            # => Animal::Horse
horse.class.superclass # => Animal

cat = Animal::Cat.new "Bıdık"
cat.name               # => "Bıdık"
cat.class              # => Animal::Cat
cat.class.superclass   # => Animal

alien = Animal::Uber.new
alien.respond_to?(:name) # => false
alien.class            # => Animal::Uber
alien.class.superclass # => Object
```


## Module

```ruby
module RandomNumbers
  def generate
    rand(10)
  end
end

class DiceGame
  include RandomNumbers
end

class RaceGame
  include RandomNumbers
end

g = DiceGame.new
g.generate # => 3

x = RaceGame.new
x.generate # => 7
```


```ruby
module Framework
  module HttpFunctions
    def self.fetch_url
      "This is url fetcher"
    end
  end
end

Framework::HttpFunctions.fetch_url # => "This is url fetcher"
```


```ruby
module Framework
end

module Framework::HttpFunctions
  def self.fetch_url
    "This is url fetcher"
  end
end

Framework::HttpFunctions.fetch_url # => "This is url fetcher"
```


```ruby
module Sinatra::MyFeature
end
```


```ruby
module A
  SABIT = 5
end

A::SABIT # => 5
```


```ruby
module A
  SABIT = 5
  module B
    def self.sabit_degeri_ver
      SABIT
    end
  end
end

A::SABIT              # => 5
A::B.sabit_degeri_ver # => 5
```


```ruby
SABIT = 5 # en dıştaki global
module A
  SABIT = 10 # içerideki
  module B
    def self.sabit_degeri_ver
      "#{::SABIT}, #{SABIT}"
    end
  end
end

A::B.sabit_degeri_ver # => "5, 10"
```


```ruby
module A
  def sadece_iceriden
    "Bu private method"
  end

  def bu_sayede_private_erisim_olur
    sadece_iceriden
  end

  private :sadece_iceriden
end

class Deneme
  include A
end

c = Deneme.new
c.sadece_iceriden # => NoMethodError: private method ‘sadece_iceriden’ called for #<Deneme:0x007f8f7c9188c8>
c.bu_sayede_private_erisim_olur # => "Bu private method"
```


## Extend ve Include Durumları

```ruby
module Person
  attr_accessor :name
  def say_hi
    "Hello #{@name}"
  end
end

Person # => Person

class User
  include Person
  def initialize(name)
    @name = name
  end
end

User # => User

u = User.new("Uğur") # => #<User:0x007fcd42976de8 @name="Uğur">
u.say_hi # => "Hello Uğur"

u.name = "vigo"
u.say_hi # => "Hello vigo"
```


```ruby
User.new("Ezel").say_hi # => "Hello Ezel"
```


```ruby
User.say_hi # => undefined method `say_hi' for User:Class (NoMethodError)
```


```ruby
module Person
  attr_accessor :name
  def say_hi
    @name ||= "Undefined name"
    "Hello #{@name}"
  end
end

class User
  extend Person
  def initialize(name)
    @name = name
  end
end
```


```ruby
user = User.new("Yeşim") # => #<User:0x007f87c39702a0 @name="Yeşim">
user.name # => undefined method `name' for #<User:0x007f87c39702a0 @name="Yeşim"> (NoMethodError)
```


```ruby
User.say_hi # => "Hello Undefined name"
User.instance_methods - Object.instance_methods # => [] # boş array
```


