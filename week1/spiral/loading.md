We can now set up a board with some obstacles, and move a player around them. However, it's pretty tricky to define maps for each board one obstacle at a time. It'd be way easier if we could read the board from a file.

Create a new _static_ class in `Spiral`: `MapLoader` and a corresponding test class in the tests project. Start with a test (big surprise there). Your test should call `MapLoader.GetObstaclesFromRow` with a test string. To begin with, test it on something extremely simple like ".#". `GetObstaclesFromRow(".#", 0)` should return a collection of `Obstacle` with a single obstacle at coordinates 0,1. Notice that we're providing the row index (which row it is) as the second argument.

Next, write a test that calls `MapLoader.GetObstacles`, passing it an array of `string` simulating the array you'd get from reading all lines in a file. To make this test pass, call `GetObstaclesFromRow` on each string in the array, passing it the row index as the second parameter.

Finally, write a test that calls a new `Board` constructor that takes only an array of `string`. Check that its `.ToString` output is the same as the input, with the addition of the player symbol and some newlines.

When this test is passing, you're ready to read the file. You don't really need to write a test for this right now (it'd be part of integration testing). Just call C#'s `ReadAllLines()` on the file, and pass the array it returns to the `Board` constructor.