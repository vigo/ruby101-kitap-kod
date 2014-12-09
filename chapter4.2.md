# Chapter 4.2

## Blocks (Bloklar)

```ruby
family_members = ["Yeşim", "Ezel", "Uğur", "Ömer"]

family_members.each do |member_name|
  puts member_name
end

# Yeşim
# Ezel
# Uğur
# Ömer
```


```ruby
family_members = ["Yeşim", "Ezel", "Uğur", "Ömer"]

family_members.each { |member_name| puts member_name }

# Yeşim
# Ezel
# Uğur
# Ömer
```


```ruby
def test_function
  yield
end

test_function {
  puts "Merhaba"
}

# Merhaba

test_function do
  puts "Ben block içinden geliyorum"
end

Ben block içinden geliyorum

test_function do
  [1, 2, 3, 4].each do |n|
    puts "Sayı #{n}"
  end
end

# Sayı 1
# Sayı 2
# Sayı 3
# Sayı 4
```


```ruby
def test_function
  if block_given?
    yield
  else
    puts "Lütfen bana block veriniz!"
  end
end
```


```ruby
def numerator
  yield 10
  yield 4
  yield 8
end

numerator do |number|
  puts "Geçilen sayı #{number}"
end
```


```ruby
def print_users
  ["Uğur", "Yeşim", "Ezel"].each do |name|
    yield name
  end
end

print_users do |name|
  puts "Kullanıcı Adı: #{name}"
end

# Kullanıcı Adı: Uğur
# Kullanıcı Adı: Yeşim
# Kullanıcı Adı: Ezel
```


```ruby
5.times { puts "Merhaba" }
5.times { |i| puts "Sayı #{i}" }
5.times do |i|
  puts "Sayı #{i}"
end
```


