---
layout: post
title: Encapsulation in Ruby
---
![Data Encapsulation in Nature](../images/encapsulation.jpg)

Data encapsulation restricts access to data or methods from outside the class. For methods, this is achieved in Ruby by setting methods to private. Instance and class variables are encapsulated by default, and cannot be accessed from outside the class. Access can be given by using [setter and getter methods](https://rubymonk.com/learning/books/4-ruby-primer-ascent/chapters/45-more-classes/lessons/110-instance-variables). A shortcut in Ruby for such methods are accessors.

The following is an example of a poorly-encapsulated class that uses an attr_accessor:

```ruby
class BankAccount
attr_accessor :name
  def initialize(name)
    @name = name
  end
end
```

This is bad practice, because any simple Joe can change the name of my bank account. So how do I change my code, so only authorized people can change the name of my account?

```ruby
class BankAccount
attr_reader :name

  def initialize(name)
    @name = name
  end

  def change_name(name)
    raise 'no access' unless user == admin
    @name = name
  end
end
```

In this way, I restrict the changing of the name of my bank account to admin users. I succesfully encapsulated my data and only opened it up as far as it is needed for my program. 
