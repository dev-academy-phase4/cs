# Things to bump into

So far the player exists in a featureless landscape of dots. Let's change that with some objects the player must navigate around. We can use obstacles to construct walls and rooms.

Creating obstacles should be very similar to the way we created the player. The only real difference is that they don't move around, so it should be even easier! Create a new class file, `Obstacle.cs`, and a corresponding test class. You first test should just make sure that the obstacle's `Row` and `Col` properties are set correctly in the constructor. You probably shouldn't make a constructor that takes no arguments: unlike the player, we always want to specify where our obstacles are.

That simple beginning out of the way, we have to teach the board to store the obstacles. Write a test that expects `Board` to allow a constructor that passes a `List<Obstacle>` and stores the obstacles internally as an `IEnumerable<Obstacle>`: a _generic collection_. We don't much care about how many obstacles there are, only that there can be some and we can grab them all from a collection when we need them.

We'll start with a rather obvious test just to get the `Obstacles` property set up on the board:

```cs
// LINQ needed for .Count()
using System.Linq;

[Fact]
public void BoardCanHaveObstacles ()
{
        // Arrange
        var obstacles = new List<Obstacle> { new Obstacle(0, 0) };

        // Act
        var board = new Board(1, 1, obstacles);

        // Assert
        Assert.Equal(1, board.Obstacles.Count());
}
```

This is the kind of test that we don't always need to write in C# because it's fairly self-evident that if a class has a property, we can set that property. Still, it doesn't hurt to practice and it might help if you're not used to the syntax for collections yet. To make it pass, you'll need to add a constructor for `Board` that accepts integers for row, col, and a collection of obstacles.

The next step is to make sure that your player can't move into a location that contains an obstacle... otherwise they'd be pretty ineffectual obstacles. Write a test in `BoardTests` that attempts to move your player onto an obstacle, and make sure that the player's location doesn't change. You'll want to modify `Board.MoveIsValid` to accomplish this.

Finally, make sure that the obstacles appear on the screen. Use a '#' character. Every time `Board.Update` is called, it should check every obstacle and change the corresponding cell in `Board.Cells` to a hash. Don't forget to write the test first! For example, a 2x2 board with obstacles on `0,1`, `1,0`, and `1,1` should look like `@#\n##\n` after a call to `Board.Update`.


### Exceptional obstacles

Let's try some exception handling. Because obstacles can be created anywhere, we need to make sure that some developer (probably us!) doesn't try to create one outside the confines of the board. If they do, we want to throw an exception and handle it appropriately. We can test for that too, using `Assert.Throws()`:

```cs
[Fact]
public void ThrowsIfObstaclesOutsideBoard ()
{
        // Arrange
        var o = new Obstacle(2, 0);

        // Act & Assert
        Assert.Throws<System.ArgumentOutOfRangeException>(() =>
                new Board(1, 1, new List<Obstacle> { o }));
}
```

`Assert.Throws` returns the exception so if you want to do futher assertions, you can with `var ex = Assert.Throws<...`. Make the test pass by throwing an `ArgumentOutOfRangeException` if `Board` is passed a list of obstacles containing at least one that is outside the boundaries.

Once that's passing, we know an exception is thrown but we still have to handle it sensibly. As an experiment, try modifying the code in `Program.cs`, deliberately passing `Board` a list with an invalid obstacle in it.

```cs
static void Main(string[] args)
{
        var obstacles = new List<Obstacle> { new Obstacle(21, 21) };
        var board = new Board(10, 10, obstacles);
```

What happens?

That's right: badness. Badness happens. When a user plays our game, they're not going to expect to have to deal with an exception. Exceptions are for us to handle, like so:

```cs
Board board;
try
{
        board = new Board(10, 10, obstacles);
}
catch(System.ArgumentOutOfRangeException)
{
        Console.WriteLine("An error prevented the game board from being created.");
        Console.ReadLine();
        return;
}
```

Note that the `return;` prevents any further code from being executed if the board cannot be created safely. This is fairly blunt exception handling, but it does reduce the chance that a rogue obstacle will cause issues later in the program.
