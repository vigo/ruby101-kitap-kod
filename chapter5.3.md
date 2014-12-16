# Chapter 5.3

## String

```ruby
m = "Merhaba"
m.class # => String
```


```ruby
m = "Merhaba"
puts "#{m} Uğur" # Merhaba Uğur
puts '#{m} Uğur' # #{m} Uğur
```


```ruby
puts "Saat: #{Time.now}" # Saat: 2014-08-12 10:37:22 +0300
```


```ruby
puts "Merhaba\nDünya"

# Merhaba
# Dünya
```


```ruby
m = ""
m << 65
puts m # A
```


```ruby
puts "öz" "yıl" "maz" "el" # özyılmazel
```


## String Literals (String Kalıpları)

```ruby
%{Merhaba Dünya Ben vigo nasılsınız?} # => "Merhaba Dünya Ben vigo nasılsınız?"

%{Bu işlemlerin %80'i "uydurma"} # => "Bu işlemlerin %80'i \"uydurma\""
```


```ruby
%w{foo bar baz}       # => ["foo", "bar", "baz"]
%w{foo bar baz}.class # => Array
```


```ruby
%i{foo bar baz} # => [:foo, :bar, :baz]
```


```ruby
person = "Uğur"
%q{Merhaba #{person}} # => "Merhaba \#{person}"
%Q{Merhaba #{person}} # => "Merhaba Uğur"
```


```ruby
%s{my_variable} # => :my_variable
%s{email} # => :email
```


```ruby
%r{(.*)hello}i # => /(.*)hello/i
```


```ruby
%x{ls -1 $HOME} # => "Applications\nDesktop\nDevelopment\nDocuments\nDotfiles\nDownloads\nLibrary\nVirtualBox VMs\nWorks\nbin\n"
```


```ruby
%x{ls -1 $HOME}.split("\n")
```


## Here Document Kullanımı

```ruby
mesaj = <<END
Merhaba nasılsınız?
Biz de çok iyiyiz
Görüşürüz!
END
puts mesaj

# Merhaba nasılsınız?
# Biz de çok iyiyiz
# Görüşürüz!
```


```ruby
mesaj = [<<BİR, <<İKİ, <<ÜÇ]
  Bu Bir
BİR
  Bu iki....
İKİ
  Bu da üüüüüüüüç
ÜÇ

puts mesaj

# - Bu Bir
# - Bu iki....
# - Bu da üüüüüüüüç
```


## String Method'ları

```ruby
"Merhaba %s" % "Uğur" # => "Merhaba Uğur"
"Sayı: %010d" % 2014  # => "Sayı: 0000002014"
"Kullanıcı Adı: %s, E-Posta: %s" % [ "vigo", "vigo@foo.com" ] # => "Kullanıcı Adı: vigo, E-Posta: vigo@foo.com"
"Merhaba %{username}!" % { :username => 'vigo' } # => "Merhaba vigo!"
```


```ruby
"Merhaba!" * 3 # => "Merhaba!Merhaba!Merhaba!"
"Merhaba!" * 0 # => ""
```


```ruby
"Merhaba" + " " + "Dünya" # => "Merhaba Dünya"
```


```ruby
a = "Merhaba"
a << " dünya" # => "Merhaba dünya"
a # => "Merhaba dünya"
a.concat(33) # => "Merhaba dünya!"
a << 33 # => "Merhaba dünya!!"
```


```ruby
"vigo" <=> "vigo"    # => 0   # eşit
"vigo" <=> "vig"     # => 1   # vigo büyük
"vigo" <=> "vigoo"   # => -1  # vigo küçük
"vigo" <=> 3         # => nil # alakasız iki şey
```


```ruby
"Saat tam 4'de buluşalım" =~ /\d/ # => 9

# \d sayı yakaladı ve indeksi döndü

"Saat tam 4'de buluşalım"[9] # => "4"
```


```ruby
m = "Merhaba Dünya"
m[0]         # => "M"  # 0.karakter
m[0, 2]      # => "Me" # 0'dan itibaren 2 karakter
m[0..4]      # => "Merha" # range, 0'dan 4 dahil
m[-1,]       # => "a" # son karakter
m[-13..-1]   # => "Merhaba Dünya" # sondan başa
m[15, 1]     # => nil # olmayan indeks
m[/(?<sesli>[aeiou])/, "sesli"] # => "e" # regexp
m["Merhaba"] # => "Merhaba" # metni bul
m["vigo"] # => nil # olmayan metin
```


```ruby
m = "merhaba"
m.slice(2,5) # => "rhaba"
```


```ruby
String.new.methods # => [:<=>, :==, :===, :eql?, :hash, :casecmp, :+, :*, :%, :[], :[]=, :insert, :length, :size, :bytesize, :empty?, :=~, :match, :succ, :succ!, :next, :next!, :upto, :index, :rindex, :replace, :clear, :chr, :getbyte, :setbyte, :byteslice, :scrub, :scrub!, :freeze, :to_i, :to_f, :to_s, :to_str, :inspect, :dump, :upcase, :downcase, :capitalize, :swapcase, :upcase!, :downcase!, :capitalize!, :swapcase!, :hex, :oct, :split, :lines, :bytes, :chars, :codepoints, :reverse, :reverse!, :concat, :<<, :prepend, :crypt, :intern, :to_sym, :ord, :include?, :start_with?, :end_with?, :scan, :ljust, :rjust, :center, :sub, :gsub, :chop, :chomp, :strip, :lstrip, :rstrip, :sub!, :gsub!, :chop!, :chomp!, :strip!, :lstrip!, :rstrip!, :tr, :tr_s, :delete, :squeeze, :count, :tr!, :tr_s!, :delete!, :squeeze!, :each_line, :each_byte, :each_char, :each_codepoint, :sum, :slice, :slice!, :partition, :rpartition, :encoding, :force_encoding, :b, :valid_encoding?, :ascii_only?, :unpack, :encode, :encode!, :to_r, :to_c, :>, :>=, :<, :<=, :between?, :nil?, :!~, :class, :singleton_class, :clone, :dup, :taint, :tainted?, :untaint, :untrust, :untrusted?, :trust, :frozen?, :methods, :singleton_methods, :protected_methods, :private_methods, :public_methods, :instance_variables, :instance_variable_get, :instance_variable_set, :instance_variable_defined?, :remove_instance_variable, :instance_of?, :kind_of?, :is_a?, :tap, :send, :public_send, :respond_to?, :extend, :display, :method, :public_method, :singleton_method, :define_singleton_method, :object_id, :to_enum, :enum_for, :equal?, :!, :!=, :instance_eval, :instance_exec, :__send__, :__id__]
```


```ruby
m = "merhaba"

m.capitalize # => "Merhaba"
m # => "merhaba"

m.capitalize! # => "Merhaba" # m'in değeri artık değişti!
m # => "Merhaba"

"vigo".center(12) # => "    vigo    "
"vigo".center(12, "*") # => "****vigo****"

"merhaba".chars # => ["m", "e", "r", "h", "a", "b", "a"]

"merhaba\n".chomp # => "merhaba"
"merhaba dünya".chomp(" dünya") # => "merhaba"

"merhaba vigo".chop # => "merhaba vig"
"merhaba vigo\n".chomp # => "merhaba vigo"

"a".chr # => "a"

x = "Merhaba"
x.clear # => ""

"Merhaba Dünya".count("a") # => 3  # 3 adet a
"Merhaba Dünya".count("ab") # => 4 # a ve b toplam 4 tane
"Merhaba Dünya".count("e") # => 1  # e'den 1 tane

"Merhaba Dünya".delete("e") # => "Mrhaba Dünya"
"Merhaba Dünya".delete("a", "ba") # => "Merhb Düny"

"MERHABA".downcase # => "merhaba"
"merhaba".upcase # => "MERHABA"
"Merhaba".swapcase # => "mERHABA"

"merhaba".size # => 7
"merhaba".length # => 7

"merhaba".ljust(20)      # => "merhaba             "
"merhaba".ljust(20, "*") # => "merhaba*************"
"merhaba".rjust(20)      # => "             merhaba"
"merhaba".rjust(20, "*") # => "*************merhaba"

"   merhaba  ".strip  # => "merhaba"
"  merhaba".lstrip    # => "merhaba"
"merhaba  ".rstrip    # => "merhaba"

"merhaba".index("m") # => 0
"merhaba".index("ba") # => 5

"merhaba".rindex("m") # => 0
"merhaba".rindex("h") # => 3

"a".next     # => "b"
"abcd".next  # => "abce" # d'den sonra e geldi...
"b".succ     # => "c"

# baş, ayraç, son
"merhaba".partition("r") # => ["me", "r", "haba"]
"merhaba".partition("a") # => ["merh", "a", "ba"]
"merhaba".partition("x") # => ["", "", "merhaba"]

"merhaba dünya".reverse # => "aynüd abahrem"

"hey seeeeeeeeeeeeeeen! aloooooooo".squeeze # => "hey sen! alo"

"Merhaba".dump # => "\"Merhaba\""
"merhaba".getbyte(0) # => 109 # m'in ascii değeri

"0x0f".hex # => 15
"0x0fff".hex # => 4095

"merhaba".insert(0, "X") # => "Xmerhaba"
"merhaba".insert(3, "A") # => "merAhaba"
"merhaba".insert(-1, ".") # => "merhaba."

"123".oct # => 83 # Octal'e çevirdi (8'lik)

"A".ord # => 65  # Ascii değeri
"a".ord # => 97 # Ascii değeri

"dünya".prepend("Merhaba ") # => "Merhaba dünya" # öne ekledi

# transform
"merhaba hello".tr("el", "ip") # => "mirhaba hippo" # e=>i, l => p oldu
"ArkAdAşlar nasılsınız?".tr("A", "a") # => "arkadaşlar nasılsınız?"

# a'dan e'y kadar X ile transform yap
"merhaba dünya".tr("a-e", "X") # => "mXrhXXX XünyX"
```


## Convert Method'ları

```ruby
"merhaba".to_i   # => 0 # integer'a çevirdi
"merhaba".to_f   # => 0.0 # float'a çevirdi
"5".to_i          # => 5
"1.5".to_f        # => 1.5
"merhaba".to_s    # => "merhaba" # string
"merhaba".to_str  # => "merhaba" # string
"merhaba".to_sym  # => :merhaba # symbol
"merhaba".to_r    # => (0/1) # Rasyonel sayı
"0.2".to_r        # => (1/5) # Rasyonel sayı
"merhaba".to_c    # => (0+0i) # Kompleks sayı
"1234".to_c       # => (1234+0i)
"merhaba".to_enum # => #<Enumerator: "merhaba":each> # Enumeratör'e çevirdi
```


## Kontrol Method'ları

```ruby
"merhaba".start_with?("m") # => true
"merhaba".start_with?("mer") # => true
"merhaba".start_with?("f") # => false

"merhaba".end_with?("a") # => true
"merhaba".end_with?("haba") # => true
"merhaba".end_with?("zoo") # => false

"merhaba".eql?("Merhaba") # => false
"merhaba".eql?("merhaba") # => true

"merhaba dünya".include?("dünya") # => true

"merhaba".empty? # => false
"".empty? # => true

"kedi".between?("at", "balık") # => false # başlangıç harfi a ve b arasındamı? gibi düşünün
"kedi".between?("fare", "sinek") # => true
```


## Array ve Block ile İlişkili Methodlar

```ruby
"Selam millet nasıl sınız?".split # => ["Selam", "millet", "nasıl", "sınız?"]
"Selam millet-nasıl sınız?".split("-") # => ["Selam millet", "nasıl sınız?"]
"A takımı: 65 B takımı: 120".split(/ +\d+ ?/) # => ["A takımı:", "B takımı:"]
"1,2,3,4,5".split(",") # => ["1", "2", "3", "4", "5"]
```


```ruby
"merhaba".each_byte {|c| puts c }

# 109 (m)
# 101 (e)
# 114 (r)
# 104 (h)
# 97  (a)
# 98  (b)
# 97  (a)
```


```ruby
"merhaba".each_char {|c| puts c }

# m
# e
# r
# h
# a
# b
# a
```


```ruby
"Merhaba\nDünya\nNasıl sın?".each_line {|l| puts l }

# Merhaba
# Dünya
# Nasıl sın?

"Merhaba@@Dünya@@Nasıl sın?".each_line("@@") {|l| puts l }
# Merhaba@@
# Dünya@@
# Nasıl sın?
```


```ruby
"a1".upto("b1"){ |t| puts t }

# a1
# a2
# a3
# a4
# a5
# a6
# a7
# a8
# a9
# b0
# b1
```


## Pattern Yakalama (Regexp)

```ruby
"merhaba dünya, merhaba uzay".sub("merhaba", "olaa") # => "olaa dünya, merhaba uzay"
"merhaba dünya, merhaba uzay".gsub("merhaba", "olaa") # => "olaa dünya, olaa uzay"


"Merhaba Dünya".gsub(/[aeiou]/, "x") # => "Mxrhxbx Dünyx"
"Merhaba Dünya".gsub(/([aeiou])/, '(\1)') # => "M(e)rh(a)b(a) Düny(a)"
"Merhaba dünya, merhaba uzay, merhaba evren".gsub(/((m|M)erhaba)/){|c| c.upcase } # => "MERHABA dünya, MERHABA uzay, MERHABA evren"
"Merhaba Dünya".gsub(/(?<sesli_harf>[aeiou])/, '{\k<sesli_harf>}') # => "M{e}rh{a}b{a} Düny{a}"
"Merhaba Dünya".gsub(/[ea]/, 'e' => 1, 'a' => 'X') # => "M1rhXbX DünyX"
```


```ruby
"merhaba".match("a") # => #<MatchData "a">

"merhaba".match("(a)") # => #<MatchData "a" 1:"a"> # 1 tane yakaladı, (a) ve Array geldi
"merhaba".match("(a)")[0] # => "a" # yakalanan

"merhaba 2014".match(/\d/) # => #<MatchData "2">

"merhaba 2014".match(/(\d)/) # => #<MatchData "2" 1:"2">
"merhaba 2014".match(/(\d+)/) # => #<MatchData "2014" 1:"2014">
"merhaba 2014".match(/(\d+)/)[0] # => "2014"
"merhaba 2014".match(/(\d+)/)[0].to_i # => 2014
```


```ruby
"Merhaba millet!".scan(/\w+/) # => ["Merhaba", "millet"]
"Merhaba millet!".scan(/./) # => ["M", "e", "r", "h", "a", "b", "a", " ", "m", "i", "l", "l", "e", "t", "!"]
"Merhaba millet! Saat 10'da buluşalım".scan(/Saat \d+/) # => ["Saat 10"]
```


