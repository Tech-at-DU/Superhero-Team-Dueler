# Inheritance

One of the great features of object oriented programming is the idea of **inheritance**. Inheritance comes in handy because it allows for additional ways to reuse code.

Here is a simple demonstration of inheritance at work.

```python
class Animal:
  def __init__(self, name, sleep_duration):
    self.name = name
    self.sleep_duration = sleep_duration

  def sleep(self):
    print(f"{self.name} sleeps for hours {self.sleep_duration}")
```

Let's say we have the above `Animal` class. We can instantiate a new animal object the same way we've already seen it done.

```python
dog = Animal("Sophie", 12)
dog.sleep()
```

Here we have our dog Sophie that needs 12 hours of sleep every night. If we call our sleep method we'll see this:

```
Sophie sleeps for 12 hours
```

Our dog here is simply an instance of our `Animal` class, but what if we want specific dog functionality that only dogs have.

We don't want to put a bark method in `Animal` because not every animal barks. We also don't want to have to duplicate every method that dogs and animals have in common.

Let's use inheritance to make a `Dog` class that allows us to bark.

```python
class Animal:
  def __init__(self, name, sleep_duration):
    self.name = name
    self.sleep_duration = sleep_duration

  def sleep(self):
    print(f"{self.name} sleeps for hours {self.sleep_duration}")

# Note that the class Dog takes in Animal as a parameter!
class Dog(Animal):
  def bark(self):
    print("Woof! Woof!")
```

Instantiate a new `Dog` object and call the sleep and bark methods this way.

```
my_dog = Dog("Sophie", 12)
my_dog.sleep()
my_dog.bark()
```

You should see this output in the terminal.

```
Sophie sleeps for 12 hours
Woof! Woof!
```

**You can see that we didn't have to create another sleep method again in order to use it.** Our `Dog` class **inherited** this method from our **superclass** `Animal`.

In this example `Dog` is our **subclass** and it will inherit everything from its superclass. This allows us to write specific functionality for `Dog` while keeping all the original functionality that was already given to us in `Animal`. This is also why we did _not_ need to write an `__init__` method for `Dog`: it just uses the same one as `Animal`!

> Note the comment in the previous code snippet. Our `Dog` class takes in `Animal` as its parameter, which signals that `Dog` is a subclass of `Animal`, as all `Dogs` are created from `Animals`, and not just plain `objects`

Let's try this out ourselves now:

Create the file `animal.py` file

```bash
$ touch animal.py
```

Create a `class` named `Animal` which has the methods `eat` and `drink` as well as the property `name`.

The eat method should print the animal's name and "is eating"

The drink method should print the animal's name and "is drinking"

Once you do that, in the same file, create the `Frog` class, which is a subclass of `Animal`, and has the method `jump`, which prints the frog's name and "is jumping"

Finally, test your code by instantiating one `Animal` and one `Frog`, and making sure that your `Frog` object can eat, drink, and jump, and that your `Animal` can eat and drink.

Once you've tried it, check your code against the provided solution below:

<details>
<summary>Solution</summary>
<br>

```python
#animal.py
class Animal:
  def __init__(self, name):
    self.name = name

  def eat(self):
    print(f"{self.name} is eating")

  def drink(self):
    print(f"{self.name} is drinking")

class Frog(Animal):
    def jump(self):
      print(f"{self.name} is jumping")
```

</details>

Let's use what we learned here to give our superheroes more options for attacking.

# Weapon Class

In your project directory, make a file named `weapon.py` to contain the Weapon class

One of the powerful features of Object Oriented Programming has a large scary name but refers to a pretty simple concept: **Polymorphism**.

Polymorphism basically allows us to use different implementations of the same method.

For example, we've already built an `Ability` class that will give our superheroes a way to fight, but many superheroes have more than just abilities. Let's give our superheroes weapons! They can do this by importing the Weapon class from our new Weapon file.

We can reuse the functionality in `Ability` so that we can prevent code duplication. let's say that weapons aren't as effective as superhero abilities so we should rewrite our attack function to allow for greater variability in attack strength. let's make our weapons attack power range between half of the `max_damage` value, to the full `max_damage` value of the weapon.

For example, if the Weapon has a `max_damage` value of 80, then the Weapon's attack method should return a value between 40 and 80.

**NOTE:** Make sure to use integer division ( Using the `//` operator) to be certain that you return an integer. This way if the `max_damage` value was 57, it will return 28 instead of 28.5

Write the `attack` method for our new `Weapon` class.

**HINT:** Use what you learned for the `attack` method in the `Ability` class if you get stuck.

```python
class Weapon(Ability):
  def attack(self):
    """  This method returns a random value
    between one half to the full attack power of the weapon.
    """
    # TODO: In the attack method, use integer division to find half of the max_damage value
    # then return a random integer between half of max_damage and max_damage
    pass
```

Now that we have a weapon, we need to allow heroes to add a weapon for them to use. You will do this one on your own as well, refer to your other `add` methods for guidance.

Make sure to import the Weapon class into your Hero class

Add the following to the Hero class:

**HINT:** Remember, self.abilities is just a list!

```python
from weapon import Weapon

class Hero:
  # The code you have already written should be here.
  # Add the following method to your hero class...

  def add_weapon(self, weapon):
    '''Add weapon to self.abilities'''
    # TODO: This method will append the weapon object passed in as an
    # argument to self.abilities.
    # This means that self.abilities will be a list of
    # abilities and weapons.
    pass
  ....
```

Use these tests to make sure you implemented `Weapon` correctly:

Test out your code using these method calls at the bottom of your file.

```python
if __name__ == "__main__":
    # If you run this file from the terminal
    # this block is executed.
    hero = Hero("Wonder Woman")
    weapon = Weapon("Lasso of Truth", 90)
    hero.add_weapon(weapon)
    print(hero.attack())
```

Your output should be a number between 45 and 90.

Congrats, you've re-defined a method that already exists in our inherited `Ability` class!

This is called **method overriding** and it is a form of **Polymorphism. It allows you to specify a different functionality for methods that are inherited from the superclass.** When we call `attack()` on our `Weapon` object it will run the `attack` method specified in the `Weapon` class and not the one in `Ability`.

What is polymorphism doing in practicale terms? In this case we have two classes that are similar but act differently. And one we can replace one with another in software without any problems. Let's look at why.

First lets look at the word:

> Polymorphism is a greek word meaning: to have multiple forms.
> Poly means multiple
> and morph means to change form

We often write code that works with one type of thing. Integers, Floats, Strings for example. Sometimes we run into situations where we have multiple different kinds of things but we want to work with all these different things without having to write a new system!

`Ability` stores an attribute called `max_damage`. Since `Weapon` extends `Ability` we can use `Weapon` anywhere our code requires an object with a `max_damage` attribute because `Weapon` will inherit `max_damage`.

When we use an ability we call it's attack method. Both `Ability` and `Weapon` implement an attack method. Any code that receives an Object and tries to invoke that object's attack method can work with either an `Ability` or a `Weapon`.

`Ability` and `Weapon` are both different. When invoking an attack with a weapon the amount of damage returned will be a higher number. So internally the `Ability` and `Weapon` work differently but externally they look the same!

Let's look at that idea with some code:

```python
# define an ability and a weapon
# both have the same max damage
eye_rays = Ability('Eye Rays', 50)
laser_blast = Weapon('Laser Blast', 50)

# Let's put these in an array together
# This list contains different types: Ability and Weapon
powers = [eye_rays, laser_blast]

# We know that all Abilities and Weapons share the same attribute
for power in powers:
  print(power.max_damage)

# We know that all Abilities and Weapns implement the attack method
for power in powers:
  print(power.attack())

# Note! While both implement attack() a Weapon will always return
# a higher average damage!
```

Form the code sample above we can see that we have a list of different types but our code here can treat them the same. This is polymorphism.

Where would this not work?

```python
# imagine we have a list of strings and ints
stuff = [1, 4, 'two', 3, 'five']

# we can loop over these elements but we can't
# use the capitalize() method on integers!
for thing in stuff:
  print(thing.capitalize()) # Error

```

In this second example you can see that an integer can't be used where our code expects a string! Int and String are not polymorphic!

# Commit

Commit your changes to GitHub. Feel free to use a custom message of your own, as long as it accuratley describes what you did.

```bash
$ git add . && git commit -m "implemented inheritance" && git push
```

# Next

Click [here](../P05-Building-a-Team) to move onto the next section.
