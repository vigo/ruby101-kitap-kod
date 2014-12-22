# Chapter 6.2

## Ranges

```ruby
(0..5)           # => 0..5
(0..5).class     # => Range
(0..5).to_a      # => [0, 1, 2, 3, 4, 5]
(0..5).to_a.join # => "012345"
(0..5).each      # => #<Enumerator: 0..5:each>
```


```ruby
(-10..0).to_a      # => [-10, -9, -8, -7, -6, -5, -4, -3, -2, -1, 0]
(0..-10).to_a      # => []
("a".."e").to_a    # => ["a", "b", "c", "d", "e"]
```


```ruby
(0...5).to_a         # => [0, 1, 2, 3, 4]
("a"..."e").to_a     # => ["a", "b", "c", "d"]
```


```ruby
(5..10).exclude_end?          # => false
(5...10).exclude_end?         # => true
```


```ruby
r = Range.new(0,2)     # => 0..2
r.to_a                 # => [0, 1, 2]
```


```ruby
(0..2) == (0..2)            # => true
(0..2).eql?(0..2)           # => true
(0..2) == (0...2)           # => false
(0..2) == Range.new(0,2)    # => true
(0..2).eql?(Range.new(0,2)) # => true
```


```ruby
(5..10).begin               # => 5
(5..10).first               # => 5
(5..10).first(2)            # => [5, 6]  # ilk 2 değeri ver
```


```ruby
(5..10).cover?(6)               # => true
(5..10).cover?(4)               # => false
(5..10).cover?(11)              # => false
(5..10).cover?(9)               # => true
("a".."z").cover?("b")          # => true
("a".."z").cover?("1")          # => false
("a".."z").cover?(1)            # => false
("a".."z").cover?("abc")        # => true
```


```ruby
("a".."z").cover?("abc")        # => true
("a".."z").include?("abc")      # => false

("a".."z").cover?("a")        # => true
("a".."z").include?("a")      # => true
```


```ruby
(5..10).end                 # => 10
(5...10).end                # => 10
```


```ruby
(5..10).last                  # => 10
(5..10).last(3)               # => [8, 9, 10]
```


```ruby
(5..10).min        # => 5
(5..10).max        # => 10
(5..10).size       # => 6
```


```ruby
r = Range.new(0, 5)
r.step(2) # => #<Enumerator: 0..5:step(2)>
r.step(2).to_a # => [0, 2, 4]
```
