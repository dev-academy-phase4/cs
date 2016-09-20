# Output stylin'

The console output of our game is pretty boring as it stands. The `Console` library provides us with the ability to change the output colour:

```cs
Console.ForegroundColor = System.ConsoleColor.Red;
Console.BackgroundColor = System.ConsoleColor.Green;
Console.ResetColor();
```

In theory we could do this in the Board class, but this would mean doing output from that class instead of just having a correctly defined `.ToString` (and breaking most of our tests). Instead, we can create a new static class which provides methods that handle the output for us. Writing a test to check console colour is probably more trouble than it's worth right now. Set up the class like so:

```cs
public static class BoardDisplayer 
{
    public static void Output (string board)
    {
        // ...
    }
}
```

Define the `Output` method so it checks each character and changes the colour depending on whether it sees a player, obstacle, or dot. Then write each character to the console.


## Other display tweaks

Before sending the board characters to the console, we can do a little preprocessing. For example, the board tends to look narrow and tall because console characters are about half as wide as they are high. Write a test that passes a string to a method called `AddSpaces` and checks to see a space has been inserted every second character. Then make it pass!

You could also add one that draws a border around the map, one that adds a key or other accompanying text, and so on.
