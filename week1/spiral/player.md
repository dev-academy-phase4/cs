Now that we have a board, it's time to add the protagonist. In the running program we'll need a `player` object, so to create the object we'll need a `Player` class. The class will need a way to track the player's current position on the board: we suggest you create properties for `Row` and `Col`.

Write a test that checks to see that a newly instantiated object of class `Player` has both these properties set to 0. Remember, you'll need to create a new class file called `PlayerTests` in the `SpiralTests` project. The framework for your test will look like this:

```cs
using Spiral;
using Xunit;

namespace SpiralTests
{
    public class PlayerTests
    {
        [Fact]
        public void PlayerStartsAt0 ()
        {
            // Arrange & Act
            var player = new Player();

            // Assert
			// ...
        }
    }
}
```
Write assertions to make sure the properties on `player` are 0 after it's created. To make the test pass, presumably you'll need to write a constructor for your Player class that takes no arguments... 


### Movement

When you've got the test passing, it's time to teach your player how to move. Write a new test that checks to see what `Row` and `Col` are set to after a method named `Move` is called with the argument 's' (for 'south'). Don't forget, you won't ever want the player to move to a location with a negative number! Make the test pass, then write another one each for `Move('e')`, `Move('n')`, and `Move('w')`. Then if you want even more practice (and you want your player to be able to move diagonally) write tests for `Move('nw')`, `Move('ne')`, `Move('sw')`, and `Move('se')`. Repetition is great for getting the basics down!

In the `Arrange` part of some tests, you might need to set artificial starting values for `Row` and `Col`. After all, you can hardly move 'north' if your player is already at 0,0! One way would be to define a constructor that accepts two arguments, one each for `Row` and `Col`. Another would be to simply make the properties public, if they aren't already, and set them directly:

```cs
player.Row = 5;
player.Col = 4;
```

For each step, make the test fail, make it pass, refactor anything that you think needs it, and do a Git commit. Be strict with yourself: good habits are especially important when no-one else is watching! Behave as if a potential employer will be looking at your commit history (which might very well be true).


### Players need a place to play

Now we need to teach our `Board` class about our `Player` class. Every board we create will have its own player: this is a simple example of the OOP concept _object composition_ (or _aggregation_, depending on who you talk to). We give the `Board` class new characteristics by making it a container for other types, instead of _inheriting_ characteristics from a parent class.

```cs
public class Board 
{
	public Player player;

	// ...
}
```

Now we can write tests that depend on the board having a player object. Say our player is represented by an '@' symbol. Write a test that checks to see that an '@' is returned at the correct position when you call `.ToString()` on the board. You're probably going to want to come up with two methods: one that _blanks_ the board with its default character (a dot), and one that _updates_ the board with all the additional features on it (just the player '@' for now).


### Need input

Time to get some keyboard input happening. The methods we wrote for the `Player` class will happily move the player to any coordinates eventually, but we don't want the player to move outside the confines of the board. When we react to user input, we have to ignore any moves which would drop the player off the edge of our tiny world and into the swirling darkness of the console below.

Write a test that calls a `MovePlayer("e")` method on `Board`. Make sure it moves the player to the correct coordinates. Once that's passing, write another test that starts with a 1x1 board and calls `MovePlayer("s")`. With the player at the default starting position of 0,0 this would normally move the player off the board: make sure the player coordinates stay the same.

To have your game respond to input, we can use a `while` loop to listen continuously for key presses until we receive the 'Q' (for 'quit') key:

```cs
            string key = "";
            while((key = Console.ReadKey(true).KeyChar.ToString()) != "q")
            {
			    // Use a switch statement here to act on the input
			}
```

Set up some cases that call `MovePlayer()` for various directions and try moving your player around the board. After each input, you should call your board clearing method, your board update method, clear the terminal window, and output the board to the console like so:

```cs
            board.Update();
            Console.Clear();
            Console.Write(board);
```