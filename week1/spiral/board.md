# The Board

In [setup](setup.md) we wrote an initial xUnit test. Let's write one that does something a bit more useful.

In C#, many of the tests we might write in JavaScript are not quite as useful because the static typing takes care of quite a bit of checking for us at compile time. For example, we don't need to check that a method returns a string: we _know_ it does, because it has return type string:

```cs
public string GetDescription ()
{
	  return "I'm a description."
}
```

Still, there are plenty of things to test. How about this?

```cs
[Fact]
public void BoardGeneratedWithCorrectDimensions ()
{
    // Arrange & Act
    var board = new Board(5, 5);

    // Assert
    Assert.Equal(5, board.Cells.Length);
    Assert.Equal(5, board.Cells[0].Length);
}
```

This will cause lots of red lines to show up underneath some of the names! Visual Studio can tell ahead of time many of the compile errors that will be caused, and tries to warn you about them. Remember _RED_, _GREEN_, _REFACTOR_? You can think of this as the 'RED' part! We are effectively making the test fail first, because the class we're trying to test doesn't exist yet. You can certainly run the test anyway, but the build will fail with a couple of errors. Visual Studio will probably also try to correct your typing to classes it knows about, trying to be helpful. This can actually be very annoying, so be sure it doesn't change what you're typing without you checking it!

To make the test pass, do the _minimum amount_ necessary to get the test to pass. This will mean:
 - creating a new _class_,  `Board`, in the `Spiral` project
 - creating a new _property_, `Cells`, in the `Board` class. The property should be a [_jagged array_](https://www.dotnetperls.com/jagged-array)
 - creating a _constructor_ for the `Board` class that accepts two integers as parameters
 - returning a jagged array with five rows, the first of which (at least) has five columns

After you get that passing, you'll obviously need to handle different dimensions at some point so write another test that forces you to code a more complete constructor, if you haven't already:

```
[Fact]
public void BoardGeneratedSixByTwo ()
{
    // Arrange
    string expected = "..\n..\n..\n..\n..\n..\n";

    // Act
    var board = new Board(6, 2);
    var actual = board.ToString();

    // Assert
    Assert.Equal(expected, actual);
}
```
We can assume that our board should print out as a series of characters with `\n` newlines after each row.

Notice the `.ToString()` method? That won't do what we'd hope it would do: it'll just return 'Spiral.Board', which isn't very helpful! However, we can _override_ it to do what we're looking for (print a string representation of the board):

```cs
public override string ToString()
{
    return "A board.";
}
```

Put this in your `Board` class and define it to return a string representation of your board so the test passes. There are a few different ways you could make the string you're going to return: a `for` loop would be simplest, but if you're feeling adventurous try playing with LINQ (don't forget to add a `using System.Linq;` statement at the top of the file if you do it this way).
