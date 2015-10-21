---
layout: post
title: Single-Responsibility Principle
---
The Single-responsibility principle (SRP) is a way of making your code more elegant and flexible. It is part of the [SOLID design principles](https://scotch.io/bar-talk/s-o-l-i-d-the-first-five-principles-of-object-oriented-design) in computer
programming which stand for:

  S – Single-responsiblity principle

  O – Open-closed principle

  L – Liskov substitution principle

  I – Interface segregation principle

  D – Dependency Inversion Principle

The Single-responsibility principle states that every class should do only one thing, i.e. have only one job. The following code goes against this principle: 

```ruby
class Plane
  def land
    raise 'Too stormy to land' if rand > .75
    @landed = true
  end
end
```
What is wrong? Looks kinda neat, no? Well, the class has two responsibilities:

1. It lands a plane by setting @landed to true

2. It decides whether the weather is stormy and raises an error if that is the case.

To correct this, we need to pull the two responsibilities into separate classes.

```ruby
class Weather
  def self.stormy?
    rand > .75
  end    
end

class Plane
  def land
    raise 'Too stormy to land' if Weather.stormy?
    @landed = true
  end
end
```

Adhering to the single-responsibility principle keeps your code lean, readable and flexible. When the client changes one aspect of her story, only one class should be changed. With a growing codebase, this is a lifesaver and your colleagues will love you for it. 
