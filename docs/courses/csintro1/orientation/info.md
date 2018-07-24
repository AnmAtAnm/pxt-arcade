# Activity: Info Category Variable Properties

We have previously worked with variables we created. A lot of the time, software developers need to interact with variables and values that were created elsewhere.

The ``||info:info||`` category in blocks contains a few variables (data properties) which we are allowed to update. These properties have to do with score, life, and time. We will take a quick look at how to use these as variables in our code.

In this activity students will:

* use the ``||info:score||`` and ``||info:life||`` variables
* combine numeric values with math operators (\*)
* identify the benefits of using ``||info:score||`` and ``||info:life||`` over other options
* use the ``||info:countdown||`` block to put a time limit on a game
* use the ``||loops:pause||`` block to wait a set amount of time

## Concept: Using ``||info:score||`` to keep track of button presses

The first example will be a simple one - simply counting the number of buttons pressed and keeping track of them as a score. We will discuss ``||controller:on any button pressed||`` block in more detail later, but for we just need to know that whatever is inside of the block will happen each time a button (``||controller:A||``, ``||controller:up||``, and so on) is pressed.

## Example: Counting button presses

https://youtu.be/7JkbbfBJCdI

1. Review the code below
2. Create the sample code and run the code
3. Save the code for the task (name it "button count")

```blocks
controller.anyButton.onEvent(ControllerButtonEvent.Pressed, function () {
    info.changeScoreBy(1)
})
```

Noticed that the score popped up in the top right corner - that is one benefit of using the ``||info:score||`` variable to keep track of points the player has earned. Now, we will add in code to add a timer, to see some of the other benefits of the ``||info:info||`` blocks.

## Student Task 1: 10 second button smash
1. Start with the code saved as "button count" in the prior example.
2. Create an ``||loops:on start||`` block

### ~hint

Remember that you can find blocks easily by using the search bar

### ~

3. Add in a ``||info:start countdown 10 (s)||`` block into the ``||loops:on start||`` block

Run the code you created in task 1 a few times, and try to get different scores. Notice the benefits that using just the ``||info:countdown||`` and ``||info:change score by||`` blocks - the countdown creates a timer that counts down to 0, and then ends the game at that point. The score keeps track of the value for you which is shown in the top right corner, and when the game is over, maintains a high score through multiple runs of the game.

## Concept: Using ``||info:life||``

Beyond score, another important value to keep track of is the players life total. This lets us make games where players can be penalized for mistakes, without simply ending the game immediately when they make one.

## Example: changing ``||info:life||`` totals
https://youtu.be/YiZ-yl5CbYM

1. Review the code below
2. Create the sample code and run the code
3. Save the code for the task (name it "do not touch the buttons")

```blocks
controller.anyButton.onEvent(ControllerButtonEvent.Pressed, function () {
    info.changeLifeBy(-1)
})
info.setLife(1)
```

This simple game gives the user a simple task - to not touch a button. If they do touch a button, the life will go down to 0, and they will lose. The game is a bit boring, but it does demonstrate a few of the benefits of using ``||info:life||``: life total shows up in the corner as a number of hearts, and when you run out of the lives, the game will end.

## Student Task 2: Touch the button 15 times
1. Start with the code saved as "do not touch the buttons" in the prior example.
2. Modify the initial value of the life to be 15, instead of just 1.
3. Add in the ``||info:change score by||`` block used in the first task, and modify it to add 2 to the score each time a button is pressed.
4. Add in a ``||info:countdown||``, and set it to run out after 2 seconds.

### Simplify Blocks chained together with JavaScript

![simplify join blocks with JavaScript](/static/courses/csintro1/orientation/join-javascript.gif)

## Student Task 3: Estimate rate of presses
### Overview
When a nurse needs to take a patient's heart rate with their other vital signs, they do not want to (or have time to) sit around for a full minute to count how many beats there are. Instead, they can use another, quicker approach to estimate the patient's heart rate - count how many heart beats there are over 15 seconds, and then multiply that value by 4 to get an estimate for the full minute. In this task, we will use the score to do the same thing, only with button presses. The ``||loops:pause||`` block is new in this example, and pauses the code at that point for however many milliseconds it is provided - in this case, we pass 6000 ms so that it pauses for 6 seconds, and then multiply by 10 to get an estimate for 60 seconds (one minute).

1. Review the code below
2. Create the sample code and run the code
3. Save the code for the task (name it "button rate")
4. Change the ``||sprites:say||`` block so that after 6 seconds have passed it says the ``||info:score||``. You may also want it to show a message explaining what the value represents

### ~hint

Review the [Variable Math](/courses/csintro1/orientation/variable-math) activity if you're having trouble making the sprite say the ``||info:score||`` - it is stored as a number.

### ~

5. Use the ``||math:x||`` block to multiply the ``||info:score||`` by 10 and store it in a variable called `minuteScore`, so it will correspond to one minute's worth of button presses.
6. Make the sprite ``||sprites:say||`` the result stored in `minuteScore`. Edit the sprite so it looks better.
7. Challenge: instead of outputting an exact estimate, give a range that the button presses will likely fall into - estimate this by making the low end of the range correspond to ``(score - 1) * 10``, and the high end of the range correspond to ``(score + 1) * 10``. For example, if the score were 5, the output should be something along the lines of "between 40 and 60".

### ~hint

For the Challenge 
Remember to use order of operations and parenthesis (JavaScript) to get the right equation,

For multiple joins we can chain the ``||text:join||`` blocks just as we did for addition. 

```blocks
enum SpriteKind {
    Player,
    Enemy
}
let mySprite: Sprite = null
mySprite = sprites.create(img`
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . 6 6 6 6 6 6 6 6 6 6 6 . . . 
. . 6 . . . . . . . . . 6 . . . 
. . 6 . 6 6 . . . 6 6 . 6 . . . 
. . 6 . . . . . . . . . 6 . . . 
. . 6 . . . . . . . . . 6 . . . 
. . 6 . 6 . . . . 6 6 . 6 . . . 
. . 6 . 6 6 6 6 6 6 . . 6 . . . 
. . 6 . . . . . . . . . 6 . . . 
. . 6 6 6 6 6 6 6 6 6 6 6 . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
`, SpriteKind.Player)
mySprite.say("score " + ("is " + "here"))
```

### ~

```blocks
enum SpriteKind {
    Player,
    Enemy
}
controller.anyButton.onEvent(ControllerButtonEvent.Pressed, function () {
    info.changeScoreBy(1)
})
let mySprite: Sprite = sprites.create(img`
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . d d d d d d . . . . . 
. . . . d d d d d d d d . . . . 
. . . . d d f d d f d d . . . . 
. . . . d d d d d d d d . . . . 
. . . . d d f d d f d d . . . . 
. . . . d d d f f d d d . . . . 
. . . . . d d d d d d . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
`, SpriteKind.Player)
mySprite.setPosition(25, 60)
game.splash("Press buttons for 6 seconds!")
pause(6000)
mySprite.say(":)")
```

## What did we learn? 
1. List one extra behavior you get for each of the three values we used in the ``||info:info||`` category (``||info:score||``, ``||info:lives||``, and ``||info:countdown||``).
2. List one potential downside of using ``||info:score||`` over just using your own variables to keep track of the state of your game.

### ~hint

What would you do if you needed to keep track of the number of coins the player has earned, the number of keys they have collected, and the number of chicken legs they have to eat. Would using ``||info:score||`` be helpful in storing all these values?

### ~

### Task rubrics

| points | 5 | 7 | 9 | 10 |
|:---:|:---:|:---:|:---:|:---:|
| Button Presses | Completed Task 1 | Completed Task 2 | Completed Task 3 | Completed the **challenge code** in Task 3 |

### Score = \_\_\_\_\_\_ /10 

### What did we learn rubric
|   | 5pts | 7pts | 9pts | 10pts |
|:---:|:---:|:---:|:---:|:---:|
| Explanation | answered at least 1 question fully or answered both questions but parts are unclear or lack detail | Explanations address all three parts of question 1 fully | all answers have clear explanations |  has an exceptional explanation using an original example and/or analogy |

### Score = \_\_\_\_\_\_ /10 