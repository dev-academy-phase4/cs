# Collections, LINQ, and Other Goodness

1. Watch sections 18 - 25 of [C# Fundamentals for Absolute Beginners](https://mva.microsoft.com/en-US/training-courses/c-fundamentals-for-absolute-beginners-16169).


## Exercises

Remember that record collection catalogue? Refactor it to use a generic collection properties instead of arrays.
  1. Choose an appropriate collection (`List` is a pretty useful default if you're not sure).
  2. Replace your current logic with LINQ statements wherever possible. Try [both styles](http://programmers.stackexchange.com/a/83268) (query and method). We suggest you prefer method syntax as it's probably closer to what you're used to in JavaScript functional programming (the standard `Array` prototype, for example).
  3. Try changing your property to an `IEnumerable` or `IQueryable`. How does that change the behaviour of your class? Can you assign a `List<Album>` to an `IEnumerable<Album>`?

Collections and interfaces are both tremendously important in C#: it's really quite rare that you would want to use an array, although we started you off with them because they're familiar. In actual fact, arrays in JavaScript are much closer to `List`s in C# in terms of what they can do and how they can be worked with. Spend as much time as you can working with collections: it will pay dividends in the long run.


## Spiral: the Player

Now that we have a board established, it's time to [add a player](spiral/player.md).
