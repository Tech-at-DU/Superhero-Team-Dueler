# Build A Team class

In your project directory, make a 'team.py' file to contain the Team class

Superheroes should be team players, so let's create a team class that can manage all of our superheroes.

Here's an overview of some of the methods we'll need.

1. `__init__`: Parameters: name: String
2. `add_hero`: Parameters: hero: String
3. `remove_hero`: Parameters name: String
4. `view_all_heroes`: Parameters: None

You'll need to use methods that exist in the built-in Python list (`self.heroes`) to add and remove heroes to the team. This code is going to be very similar to the code that you wrote in Rainbow Checklist except that instead of adding strings to our list, we want to add `Hero` objects.

## Aggregation Vs Inheritance

Before we move forward, let's review what we just said about the `Team` class: it will contain a list of `Hero` objects. An important distinction here is that **`Team` does not inherit from the `Hero` class, and `Hero` does not inherit from the `Team` class.**

Rather, the `Team` class **contains** `Hero` objects (using a list), see below for a visualized example:

![hero_team](assets/hero_visual.png)

In a similar manner, your `Hero` has a list of abilities and armors. This does not mean your `Hero` has `Ability` or `Armor` methods or properties, but that the `Hero` can contain `Ability` or `Armor` objects that have their own methods/properties, and can only be used/accessed by the `Ability` or `Armor` objects

> This concept is known as **Aggregation** in OOP. Another way to think about it is that inheritance vs aggregation is "is a" vs. "has a".
>
> For example, a `Weapon` "is a(n)" `Ability`, whereas a `Team` "has a" list of `Hero` objects

# Build the Constructor

Build the constructor for the Team class:

```python
class Team:
  def __init__(self, name):
    ''' Initialize your team with its team name and an empty list of heroes
    '''
    self.name = name
    self.heroes = list()
```

# Remove a Hero from the Team

This method should find a Hero by its name and remove them from the team's list of Heroes. If you cannot find a hero, return 0

Build the `remove_hero` method for the Team class:

```python
def remove_hero(self, name):
  '''Remove hero from heroes list.
  If Hero isn't found return 0.
  '''
  foundHero = False
  # loop through each hero in our list
  for hero in self.heroes:
    # if we find them, remove them from the list
    if hero.name == name:
      self.heroes.remove(hero)
      # set our indicator to True
      foundHero = True
  # if we looped through our list and did not find our hero,
  # the indicator would have never changed, so return 0
  if not foundHero:
    return 0
```

# View the teams heroes

You'll build this one on your own. This method should print a list of all the teams heroes to the terminal.

Build the `view_all_heroes` function for the Team class:

**HINT:** Remember self.heroes is a list!

```python
def view_all_heroes(self):
  '''Prints out all heroes to the console.'''
  # TODO: Loop over the list of heroes and print their names to the terminal one by one.
  pass
```

# Add Hero to Team

You will build this one on your own as well. We need to add heroes to our team. Let's create a method to do that. This will be similar to the methods we already wrote when adding armors to our hero.

Build the `add_hero` method for the the Team Class:

**HINT:** Remember self.heroes is a list!

```python
def add_hero(self, hero)
  '''Add Hero object to self.heroes.'''
  # TODO: Add the Hero object that is passed in to the list of heroes in
  # self.heroes
  pass
```

# Test Driven Development

Previously we've used user stories to visualize what our finished application should look like before we began to build it. Here instead of user stories we'll use automated tests in much the same way.

Test Driven Development (commonly abbreviated as **TDD**) is another way of imagining the end result before you dive into coding. However, instead of writing narratives, with TDD we actually write _code_ that verifies the behavior we want our program to perform before we even write the program.

By writing the test first you focus on functionality first instead of implementation. In the spirit of TDD, we wrote some tests already for you to use, which your class methods must pass.

## Install `pytest`

We'll use the automated testing tool [pytest](https://docs.pytest.org/en/latest/) to verify the code.

Pytest must be installed into your system first before you can use it. While you don't need pytest to run the tests included in this project, pytest gives a lot of additional helpful tools and loggin.

To install, simply open your terminal and type:

```bash
$ pip3 install pytest
```

You should be able to verify that pytest is installed by checking which version you have.

```bash
pytest --version
```

You should see something similar to this output.

```bash
This is pytest version 5.1.0, imported from /usr/local/lib/python3.7/site-packages/pytest.py
```

# Pass Your First Test

Tests have been provided to help you with this assignment.

You can download the test [here](https://github.com/Tech-at-DU/Superhero-Team-Dueler/blob/master/hero_test.py) and place it in the same folder as `hero.py`

To run the provided tests `cd` into to the project directory in the terminal

```
cd name-of-project-dir
```

then run

```
pytest
```

This command will automatically look at any file that contains `test` in the filename then run any function that begins with `test_`.

Fortunately `pytest` has options that allow us to specify which tests to run and how many tests to focus on.

If you want pytest to stop after the first failure you can use this command instead.

```
pytest -x
```

This will run all tests in `hero_test.py` and stop after the first failure.

For additional `pytest` options see their documentation [here](https://docs.pytest.org/en/latest/usage.html).

Make sure all the tests in the `hero_test.py` file pass.

## A Note About Python 2 vs Python 3

One of the exciting features about python3 is that it supports unicode! This is great but it can cause compatibility issues when running python2.

If you receive an error saying that there's a unicode error you'll need to force pytest to use python3 this way.

`python3 -m pytest`

# Commit

Commit your changes to GitHub. Feel free to use a custom message of your own, as long as it accuratley describes what you did.

```bash
$ git add . && git commit -m "implemented inheritance" && git push
```

# Next

Click [here](../P06-Team-Attack-And-Defense) to move onto the next section.
