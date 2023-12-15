# Getting Started: Build a Hero Class

Let's use what we've learned to build the hero class in a file named `hero.py`. Create that file right now. **Not all of the code for this tutorial will be contained in this file!**

Before we get started, it's important to know how we will build out this file:

- Some classes we will give you the code to use. Be sure to read through it and reference the comments so that you know what it is doing. This is important because...
- Other classes we will _NOT_ give you the code, and will only give you a docstring that describes what the code is supposed to do. Use this as a template and replace `pass` with your own code.
  - Use your prior learnings and the code we gave you to help build out the code needed for these classes

Here is an overview of what you will build in this chapter:

- Hero Class
  1. `__init__`: Parameters: name:String, starting_health:Int (default value: 100)
  2. `fight`: Parameters: opponent: Hero Class

# Build out the Hero Class

Here we define what we want our `Hero` class to look like. Each hero will need attributes such as starting and current health. Let's set these as some starting value when we create each Hero in memory.

Let's walk through each method and smoke test them as we go.

Build out the Hero class constructor:

```python
# hero.py
class Hero:
  # We want our hero to have a default "starting_health",
  # so we can set that in the function header.
  def __init__(self, name, starting_health=100):
    '''Instance properties:
      name: String
      starting_health: Integer
      current_health: Integer
    '''

    # we know the name of our hero, so we assign it here
    self.name = name
    # similarly, our starting health is passed in, just like name
    self.starting_health = starting_health
    # when a hero is created, their current health is
    # always the same as their starting health (no damage taken yet!)
    self.current_health = starting_health
```

Ok, we can initialize a hero! Now let's test it:

After completing the method, add a call to your newly created constructor at the bottom of the file. This will let you test what you just did.

**Hint:** The bottom of your file should look like this:

```python
if __name__ == "__main__":
  # If you run this file from the terminal
  # this block is executed.
  my_hero = Hero("Grace Hopper", 200)
  print(my_hero.name)
  print(my_hero.current_health)
```

If you've done it correctly you should be able to set the values and see them in the terminal when running the file:

```
Grace Hopper
200
```

Note that we can still provide a value for `starting_health` which replaces the default value of 100 that we gave in the `__init__` method! If when we instantiated our hero with only a name: `Hero("Grace Hopper")`, then their `current_health` would've been 100!

**NOTE!** The code above is inside the `if __name__ == "__main__":` block. This block will only run if this script is called directly. The if/code block here prevents this block from being run when this script is imported by another script.

Why? This allows us to test the code here by running: `python3 hero.py`. Later we want to import the `Hero` class but we won't want to run this test code.

# Fight!

It's time to get a one vs one battle happening! Your job is to create a method that will allow each hero to attack the other.

The `fight()` method will take an `opponent` as a parameter. An `opponent` is another instance of `Hero`.

Since we haven't added abilities and armor to our heroes, we'll start by randomly choosing a winner.

The core functionality for this method will come from calling methods that exist in the current instantiated object (using `self`) as well as calling methods on the `opponent` object that is passed in as a parameter.

Build the `fight` method for the Hero class! Take everything you've learned so far in this chapter and apply it to creating this method!

Add this method to the Hero class:

```python
def fight(self, opponent):
  ''' Current Hero will take turns fighting the opponent hero passed in.
  '''
  # TODO: Fight each hero until a victor emerges.
  # Phases to implement:
  #1) randomly choose winner,
  # Hint: Look into random library, more specifically the choice method
```

Import random: `import random` at the top of your script and use one of the random methods to generate a random number. For example: `random.randint(0,1)` would return a number between 0 and 1.

Print the name of the victor. It should either be the hero instance or the opponent instance. Print a message something like:

`Wonder Woman Wins!` or `Dumbledore Wins!`

**Stretch Goal:** Make the message fancy! Print something like:

`Wonder Woman defeats Dumbledore!` or `Dumbledore defeats Wonder Woman!`

## Continue To Test it out

You can test out whether your `Hero` class is working properly by adding these tests to your file:

```python
if __name__ == "__main__":
    # If you run this file from the terminal
    # this block is executed.
    hero1 = Hero("Wonder Woman")
    hero2 = Hero("Dumbledore")

    hero1.fight(hero2)
```

You should see an output similar to:

```
Wonder Woman won!
```

Test your code a few times. You should get a different results. Test enough to make sure both heroes win at some point. You'll have to test a few times because contest is random it's possible for a hero to win a few times in a row!

Since we randomly chose a winner, either hero has an equal likelihood to win. In later chapters, we'll add armor and abilities to the heroes to make the battle much more interesting!

**Stretch Goal:** consider the hero's power when deciding a winner! There are a few ways you can handle this. Here is one possible solution. Add the two powers together. Then divide power of a hero by the total. This should give you a decimal percent chance that hero should win the contest.

For example:

```python
hero1 = Hero("Wonder Woman", 300)
hero2 = Hero("Dumbledore", 250)
```

Get the total: 300 + 250 = 550

Wonder Woman's chance of winning is: 300 / 550 = 0.55 or 55%

Dumbledore's chance of winning is: 250 / 550 = 0.45 or 45%

# Commit

Commit your changes to GitHub. Feel free to use a custom message of your own, as long as it accurately describes what you did.

```bash
$ git add . && git commit -m "created hero class" && git push
```

# Next

Great work on building out your first few classes! Now that we have the basic functionality that allows our heroes to duel each other, we can expand on this to make our Superhero Dueler much more complex.
Click [here](../P02-Abilities-and-Armor/) to move onto the next section.
