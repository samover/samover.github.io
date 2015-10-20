---
layout: post
title: solid_code.include? srp
---
#### What is SRP?
The Single Responsibility Principle (SRP) is a way of making your code more
elegant and flexible. It is part of the [SOLID design principles](https://scotch.io/bar-talk/s-o-l-i-d-the-first-five-principles-of-object-oriented-design) in computer
programming. The principle states that every class should do only one thing, i.e. have only one job.

#### Code Example with too many responsibilities

``` ruby
class Airport
  attr_reader :planes

  def intialize
    @planes = []
  end

  def land(plane)
    fail if stormy?
    planes << plane
  end

  def stormy?
    conditions = [:stormy, :sunny, :rainy, :cloudy].sample
    conditions == :stormy
  end
end
```
In this example, the Airport class has two responsibilities:
1. Predicting the weather
2. Land a plane

According to SRP, we need to pull them into two separate classes.

#### Refactored code example
``` ruby
class Weather
  OUTLOOK = [:stormy, :sunny, :rainy, :cloudy]
  def self.stormy?
    OUTLOOK.sample == :stormy
  end    
end

class Airport
  attr_reader :planes, :weather

  def intialize(weather: Weather)
    @planes = []
    @weather = weather
  end

  def land(plane)
    fail if weather.stormy?
    planes << plane
  end
end
```

As you can see, Weather predicts the weather, and Airport lands a plane. Each class has a clear responsibility. This makes for elegant and readable code, which is also flexible. If you need to change how the weather is predicted, you only need to change Weather, without touching Airport.
