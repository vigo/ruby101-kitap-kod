# Chapter 4.4

## Çoklu Kontrol


```ruby
a = 5
b = 10
if a == 5 && b == 10
  puts "İşleme devam edebiliriz!"
end
```


```ruby
if a == 5
  puts "Merhaba"
end
```


```ruby
if a == b
  puts "a, b'ye eşit"
elsif a != b
  puts "a, b'ye eşit değil"
elsif a > b
  puts "a, b'ten büyük"
else
  puts "a, b'den küçük"
```


```ruby
unless a == b
  puts "Eşit değil"
end
```


```ruby
i = 0
while i < 5 do
  puts "i = #{i}"
  i += 1
end
```


```ruby
i = 0
while i < 5 do
  puts "i = #{i}"
  break if i == 3
  i += 1
end
```


```ruby
i = 0
until i == 10 do
  puts "i = #{i}"
  i += 1
end
```


```ruby
computer = "c64"
year = case computer
  when "c64" then "1982"
  when "c16" then "1984"
  when "amiga" then "1985"
  else
    "Tarih bilinmiyor"
end

puts "#{computer} çıkış yılı #{year}"

# c64 çıkış yılı 1982
```


```ruby
student_grade = 8
case student_grade
when 0
  puts "Çok kötü"
when 1..4
  puts "Başarısız"
when 5..7
  puts "İyi"
when 8..9
  puts "Çok İyi"
when 10
  puts "Süper"
end
```


```ruby
for i in 1..10
  puts "i = #{i}"
end

# i = 1
# i = 2
# i = 3
# i = 4
# i = 5
# i = 6
# i = 7
# i = 8
# i = 9
# i = 10
```


```ruby
amount = 2
pluralize = amount == 1 ? "apple" : "apples"
puts "#{amount} #{pluralize}."
```


```ruby
BEGIN { puts "Kodun başlama saati #{Time.now.to_s}" }

def say_hello(username)
  "Merhaba #{username}"
end

puts say_hello "Uğur"
sleep 5  # zaman farkı için 5 saniye bekle

END { puts "Kodun bitme saati #{Time.now.to_s}" }

# Kodun başlama saati 2014-08-04 09:30:24 +0300
# Merhaba Uğur
# Kodun bitme saati 2014-08-04 09:30:29 +0300
```


