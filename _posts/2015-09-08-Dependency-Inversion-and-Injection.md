---
layout: post
title: Dependency Injection, and Why Dependency Inversion is A Misnomer.
---
Dependency Inversion is the 'D' in the five SOLID principles of object oriented software design. It is badly named because it doesn't so much 'invert' dependencies as (almost) do away with them altogether.

Traditionally we might code a complex high level object (eg a keyboard) in terms of a simple low level one (eg a key). The high level one depends on the low level one.  If we change the low level object, it might prevent the high level object from functioning properly. Altering an object has knock on effects on anything on anything that depends on that object.

With Dependency Inversion, we no longer have any concept of high or low level. Both objects (the keyboard and the key) depend on an abstracted interface that sits between them.  Interactions between the objects take place through this interface.  Consequently we no longer have a situation where one object is dependent on the other.  Instead, both are dependent on a common abstraction.  

Using this technique we can alter objects as much as we like. Providing we preserve the interfaces, we should not get changes in one object affecting the functioning of others. This allows our system to have a naturally modular design. We can test each individual module in isolation rather than worrying about how they work in ensemble.

##Dependency Injection
Dependency injection is a means of implementing Dependency Inversion. It results in less coupling between objects and increased flexibility. In particular it makes mocking and stubbing during tests considerably more straightforward.

Without Dependency Injection, we might do something like the following to create a board with a ship on it:

```
class Board
def initialize
    @ship = Ship.new
  end
end
```


Note that the Board class depends on the Ship class. Every time we create a new board, the Board class calls the Ship class's 'new' method.

With Dependency Injection, we would inject the ship into the board when we create the latter:

```
class Board
  def initialize(ship)
    @ship = ship
  end
end
```

The Board class no longer depends on the Ship Class. We create the ship independently and then pass it to the board.
