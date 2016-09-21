# Monsters

No Roguelike is complete without monsters! Or, if you don't buy the premise, then some kind of roving adversary or competitor. We'll go with the traditional approach here. Of course, 'monster' is open to interpretation...

> "Beware; for I am fearless, and therefore powerful." ~ Mary Shelly, Frankenstein.

Start by adding `Monster` and `MonsterTest` classes. The first test should strongly remind you of the `Player` tests:

```cs
[Fact]
public void MonsterStartsAtCorrectCoordinates ()
{
    // Arrange & Act
    var monster = new Monster(1, 2);

    // Assert
    Assert.Equal(1, monster.Row);
    Assert.Equal(2, monster.Col);
}
```

So... apart from the fact that a `Monster` can start at set coordinates, `Monster`s and `Player`s could end up being quite similar. Later there might be some opportunities to have these classes implement C# _interfaces_. In fact, you could easily say that _every_ entity on the game board should be an object, each understanding how to display itself, what colour it is, whether it can be vanquished, and so on.

Speaking of which: let's add a method to player allowing it to `Vanquish` monsters. Write a test that passes an instance of monster to `Player.Vanquish` and checks that _either_ `player.Vanquished` _or_ `monster.Vanquished` is set to true. Then make it pass (for now, you might want to just auto-vanquish the monster!)

Here's how you do a conditional test with xUnit:

```cs
[Fact]
public void OneOfTheseThingsMustBeTrue ()
{
    bool foo = false;
    bool bar = true;
    Assert.True(foo || bar);
}
```


## Change the icon

Once a monster's been vanquished, you might want to change the way they're drawn on the map. Maybe write a '*' instead of an 'M' to signify their defeat?


## Give them a fighting chance

Once you've gotten the hang of auto-vanquishing monsters, you should probably work out how to decide if the player wins the contest. This becomes a question of how hard you want your game to be! You could give players and monsters a `Health` or `HitPoints` property, for example. This is also another opportunity to define an interface: `IVanquishable` could have `Health` and `Vanquished` properties on it.

You may also want to think about how a player regains health. Perhaps a small amount returns whenever they hit the 'Rest', 'Mindfulness' or 'Do Yoga' key? Or maybe they just pick up instances of the `Sandwich` object ('='). You could come up with a more complex <a href="https://en.wikipedia.org/wiki/Attribute_(role-playing_games)">stats</a> system that determines who wins, or add an element of chance using [`System.Random`](https://msdn.microsoft.com/en-us/library/system.random(v=vs.110).aspx).


## Make them mobile

Monsters are sometimes referred to as "mobs" (or "mobiles") because they can _move_. Maybe every time the player moves, the monsters on the board also have a chance of moving in a random direction. Or worse still, perhaps they always move in the direction of the player!
