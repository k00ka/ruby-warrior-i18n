# RUBY AI WORKSHOP - Ruby Warrior

## Ruby Hack Night
## October 28, 2015

---

## Why this project?
This workshop integrates many of our past learnings with AI techniques.

## Approach
* You may use any techniques you wish to use.
* My recommendation is to pair program and follow the TDD workflow (fail test, write minimum code required to pass, pass test, refactor).
* Before writing code, discuss strategies based on your observations.
* Each time you pass, you have the option to progress to the next level.
* You develop skills and abilities as you progress, so RTFR!

* You may find debugging and introspection to be powerful techniques.

---
## 60-second AI primer
_Q._ What is AI (artificial intelligence)?  
_A._ It is the science and engineering of making intelligent machines, especially intelligent computer programs. It is related to the similar task of using computers to understand human intelligence, but AI does not have to confine itself to methods that are biologically observable.

_Q._ Yes, but what is intelligence?  
_A._ Intelligence is the computational part of the ability to achieve goals in the world. Varying kinds and degrees of intelligence occur in people, many animals and some machines.

_Q._ Isn't AI about simulating human intelligence?  
_A._ Sometimes, but not always. On the one hand, we can learn something about how to make machines solve problems by observing other people or just by observing our own methods. On the other hand, most work in AI involves studying the problems the world presents to intelligence rather than studying people or animals. AI researchers are free to use methods that are not observed in people or that involve much more computing than people can do.

_Q._ Does AI aim to put the human mind into the computer?  
_A._ Some researchers say they have that objective, but they are probably using the phrase metaphorically. The human mind has a lot of peculiarities, and I'm not sure anyone is serious about imitating all of them.

---

## 10-second AI primer
_Q._ What is AI?  
_A_. AI is the ability of a machine (usually software) to achieve goals through decision-making.

---

## Workshop setup steps
#### 1. Create a project directory
    % mkdir ruby-warrior
    % cd !$

#### (optional) 2. Set Ruby version and gemset for Rbenv/RVM
_IMPORTANT: Ruby must be < 2.2!_

If you’re using Rbenv, run:

    % echo 2.1.7 > .rbenv-version
    % echo rubywarrior > .rbenv-gemsets

#### 3. Install the gem
    % gem install rubywarrior-i18n

If you’re using Rbenv, run:

    % rbenv rehash

#### 4. Initialize the workshop files
    % rubywarrior

* create a new directory with a “beginner” tower  
* name your warrior

#### 5. Move into the new subdirectory
If you don’t do this, it will ask you which profile toplay each time:

    % cd <TAB><TAB>

---

## Workshop process

We will do several iterations of the following process. Follow it carefully to ensure success!

#### 1. Read the README
_IMPORTANT: Actually do this step as it provides important hints and tips (the README file updates every time you progress to the next level)_

    % cat README.rdoc

#### 2. Test your current code to prove that it fails
    % rubywarrior
_*(failure)*_

#### 3. Infer new strategies from the hints provided by the README and test output

* Discuss this with your pair

#### 4. Update your solution

#### 5. Test your new code. If not working, go back to 4.
    % rubywarrior
_*(working)*_

* Answer “n” to the final question

#### 6. Refactor your solution (don’t forget to use multiple class and files!)

#### 7. Re-test your refactored code
    % rubywarrior
_*(working)*_

* Answer “y” to the final question

#### 8. Go back to 1

---

## Level 1
You see before yourself a long hallway with stairs at the end. There is nothing in the way.

Tip: Call ```warrior.walk!``` to walk forward in the ```Player#play_turn``` method.


```
--------
|@      >|
 --------

> = Stairs
@ = Frodo (20 HP)
```

### Warrior Abilities

##### [NEW]
    warrior.walk!
> Move in the given direction (forward by default).

---

## Hints for Level 1
* Follow the TDD workflow.

---

## Level 2
It is too dark to see anything, but you smell sludge nearby.

Tip: Use ```warrior.feel.empty?``` to see if there is anything in front of you, and ```warrior.attack!``` to fight it. Remember, you can only do one action (ending in !) per turn.

```
 --------
 |@   s  >|
 --------

 > = Stairs
 @ = Frodo (20 HP)
 s = Sludge (12 HP)
```

### Warrior Abilities
##### [NEW]
    warrior.feel
> Returns a Space for the given direction (forward by default).

    warrior.attack!
> Attacks a unit in given direction (forward by default).

##### [EXISTING]
    warrior.walk!
> Move in the given direction (forward by default).

---

## Hints for Level 2
* Remember, you're working in Ruby here. Don't simply fill up the ```play_turn``` method with a lot of code. Organize it with methods and classes. The player directory is set up as a load path so you can include other ruby files from your player.rb file.

* If you ever get stuck on a level, review the ```README``` documentation and be sure you're trying each ability out.

* Make sure to try the different options you can pass to the rubywarrior command. Run ```rubywarrior –help``` to see them all.

* To run with no delay between steps:
```
    % rubywarrior -t 0
```

* *POWER TIP: The Space object returned by Warrior#feel can answer some interesting questions!*

---

## Level 3
The air feels thicker than before. There must be a horde of sludge.

Tip: Be careful not to die! Use ```warrior.health``` to keep an eye on your health, and ```warrior.rest!``` to earn 10% of max health back.

```
---------
 |@ s ss s>|
 ---------

 > = Stairs
 @ = Frodo (20 HP)
 s = Sludge (12 HP)
```

### Warrior Abilities
##### [NEW]
    warrior.health
> Returns an integer representing your health.


    warrior.rest!
> Gain 10% of max health back, but do nothing more.

##### [EXISTING]
    warrior.feel
> Returns a Space for the given direction (forward by default).

    warrior.attack!
> Attacks a unit in given direction (forward by default).

    warrior.walk!
> Move in the given direction (forward by default).

---

## Hints for Level 3
* If you get low on health be sure to ```rest!``` when no enemy is near.

* Sludges do 3 HP damage per round.

* ```warrior.walk!``` can take a direction!

* *POWER TIP: Use a debugger to develop code fast*

```
% gem install byebug
```
> insert ```require ‘byebug’``` at top of player.rb  
> insert ```byebug``` at point of importance  

```
% gem install pry-byebug
```
> insert ```require ‘pry-byebug’``` at top of player.rb  
> insert ```binding.pry``` at point of importance

---

## Level 4
You can hear bow strings being stretched.

Tip: No new abilities this time, but you must be careful not to rest while taking damage. Save a ```@health``` instance variable and compare it on each turn to see if you're taking damage.

```
 -------
 |@ Sa S>|
 -------

 > = Stairs
 @ = Frodo (20 HP)
 S = Thick sludge (24 HP)
 a = Archer (7 HP)
```

## Warrior Abilities
##### [EXISTING]
    warrior.health
> Returns an integer representing your health.

    warrior.rest!
> Gain 10% of max health back, but do nothing more.

    warrior.feel
> Returns a Space for the given direction (forward by default).

    warrior.attack!
> Attacks a unit in given direction (forward by default).

    warrior.walk!
> Move in the given direction (forward by default).

---

## Hints for Higher Levels
* Try to use far-ranged weapons whenever possible (such as the bow).

* Senses are cheap, so use them liberally. Store the sensed information to help you better determine what actions to take in the future.

* If you're aiming for points, remember to sweep the area. Even if you're close to the stairs, don't go in until you've gotten everything (if you have the health). Use far-ranged senses (such as look and listen) to determine if there are any enemies left.

---

# Finally, good luck and have fun!
