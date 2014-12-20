# Chapter 5.6

## Symbol

```ruby
user = "vigo"
user.object_id # => 70122132113780

# şimdi başka değer atayalım
user = "bronx"
user.object_id # => 70122132113340
# object_id değişti!
```


```ruby
user = :vigo
user.object_id # => 420488

user = :bronx
user.object_id # => 420648
```


```ruby
full_name = "Uğur"         # => "Uğur"
full_name.to_sym           # => :Uğur
full_name == :Uğur.id2name # => true
user_full_name = :Uğur     # => :Uğur
user_full_name.object_id   # => 420428

:is_user_admin.id2name     # => "is_user_admin"
:is_user_admin.to_s        # => "is_user_admin"
```


```ruby
{:user=>"vigo"}
```
