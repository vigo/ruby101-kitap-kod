# Chapter 7.1

## Monkey Patching

```ruby
"Hello".length # => 5 # Bu normali

# Monkey Patching yapıyoruz ve length method'unu değiştiriyoruz.
class String
  def length
    "Uzunluk: #{self.size} karakterdir."
  end
end

"Hello".length # => "Uzunluk: 5 karakterdir."
```


```ruby
class Fixnum
  def kere(n)
    self * n
  end
end
```


```ruby
5.kere(5)         # => 25
5.kere(5).kere(2) # => 50
```


```ruby
class Fixnum
  def gün
    self * 24 * 60 * 60
  end
  
  def önce
    Time.now - self
  end

  def sonra
    Time.now + self
  end
end
```


```ruby
Time.now    # => 2015-02-09 12:55:33 +0200
5.gün.önce  # => 2015-02-04 12:55:33 +0200
1.gün.sonra # => 2015-02-10 12:55:33 +0200
```


