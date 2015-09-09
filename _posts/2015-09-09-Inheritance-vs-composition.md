---
layout: post
title: Inheritance vs composition
---

The question of when to use inheritance, and when to use composition, is largely guided by two principles - keeping your code 'DRY', and giving your code good semantic meaning.

```
module Gun
 def fire
   'bang!'
 end
end

class Ship
 def receive_hit
   @hits =+ 1
 end
end

class Destroyer < Ship
 include Gun
end

d = Destroyer.new
d.receive_hit #=> 1
d.fire #=> 'bang!'
```

A simple test as to whether something should be a sub class of an existing class, is the 'is a' rule.  In our example, a destroyer is a ship, and a ship therefore would be a suitable class to inherit from.

In our game, all our ships can 'receive hit', therefore this method can logically be put in the ship class..  We could choose to add a 'fire' method, into our ship class.  However, some of our ships might be lifeboats that do not have guns, and therefore we would not want to give lifeboats the ability to fire a non existent gun!  Seeing as our game may also eventually include tanks that can also fire guns, it would therefore make sense to put this 'fire' method into a module (a use of composition)which we can mix into classes that need this behaviour.
