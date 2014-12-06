# Chapter 3.1

## Syntax (Söz Dizimi)

```ruby
puts "Merhaba" if a > 5
```


```ruby
def greet_user(user_name)
  puts "Merhaba #{user_name}"
end

greet_user("Uğur") # Merhaba Uğur
```


```ruby
def greet_user user_name
  puts "Merhaba #{user_name}"
end

greet_user "Uğur" # Merhaba Uğur
```


```ruby
def greet_user user_name
  "Merhaba #{user_name}"
end

puts greet_user "Uğur" # Merhaba Uğur
```


## Comments

```ruby
# Bu satır yorum satırı

# Bu kısım block-comment
#
# def test_user
#   true
# end

# ya da

=begin
Bu comment...
Bu da comment...
Hatta bu da...
=end
```