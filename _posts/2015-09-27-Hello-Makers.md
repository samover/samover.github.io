---
layout: post
title: My First Post!
---

This is my first post. I will start by inserting some markdown elements:
#### A Picture
![Some Picture](images/matera.jpg)
(http://github.com/samover)

#### A Youtube Clip
[![INTRO TO MAKERS](http://img.youtube.com/vi/-g3T8fbeR9g/0.jpg)](http://www.youtube.com/watch?v=-g3T8fbeR9g)

#### And just some code: a recursive factorial method
```ruby
def factorial(n)
  if n < 0
    return "Error. You can't factor negative numbers"
  elsif n <= 1
    1
  else
    n * factorial(n - 1)
  end
```


