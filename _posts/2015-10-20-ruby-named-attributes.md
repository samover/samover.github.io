---
layout: post
title: Keyword Arguments in Ruby
---
The 'normal' way of passing arguments to a method or class in Ruby can be illustrated as follows:

```ruby
def hello(message, receiver)
  "{message}, #{receiver}!"
end

hello('greetings', 'earthling')
# => greetings, earthling!
```

Positional agruments work fine in most cases, but have a look at this:

```ruby
class Airport
  DEFAULT = 20
  def initialize(capacity = DEFAULT, weather = :stormy)
    @capacity = capacity
    @weather = weather
  end
end
```
Now, when I initialize a new Airport, I can write :

```ruby
airport = Airport.new 
# <Airport:0x007fc3190a7c40 @capacity=20, @weather="stormy">
```
But what happens when I want to pass different weather? The only way of doing that would be:

```ruby
airport = Airport.new(Airport::DEFAULT, :stormy)
# <Airport:0x007fc3190a7c40 @capacity=20, @weather="rainy">
```
And that is a needless passing of a value that is defaulted any way, and we coders are lazy, right? Since Ruby 2.0 it is possible to use named arguments, which help a coder to be even more lazy. Have a look at this:

```ruby
class Airport
  DEFAULT = 20
  def initialize(capacity: DEFAULT, weather: :stormy)
    @capacity = capacity
    @weather = weather
  end
end

airport = Airport.new(weather: :rainy)
# <Airport:0x007fc3190a7c40 @capacity=20, @weather="rainy">
 ```
Using keyword arguments (or named attributes), the order in which arguments are passed doesn't matter:

```ruby
airport = Airport.new(weather: :sunny, capacity: 50)
# <Airport:0x007fc319047b10 @capacity=50, @weather=:sunny>
 ```
 The flexibility and code clarity of keyword arguments is, of course, a trade-off with the more concise code of the 'normal' way of passing arguments.

 [Further reading on keyword arguments](https://robots.thoughtbot.com/ruby-2-keyword-arguments)
