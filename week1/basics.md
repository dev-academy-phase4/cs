# C#: the basics

Watch sections 1 - 10 of [C# Fundamentals for Absolute Beginners](https://mva.microsoft.com/en-US/training-courses/c-fundamentals-for-absolute-beginners-16169).

## Accompanying notes

* Under "Installing Visual Studio" he recommends installing various things you don't actually need. For example, you don't need C++ or Python tools. All you need is the standard Windows and Web development tools, which chances are is the default setting.
* Most of this is _very_ entry-level! However, it does step you through gradually. You may find that you can work through this initial content quite quickly. Pro-tip: you can speed the video up to 1.5x or 2x if this is more comfortable for you (click on 'Normal speed' at the bottom right of the window).
* There are assessment quizzes associated with the content. We don't think these are terribly useful in helping you learn: we'd rather you spent time actually writing C#! Feel free to skip them.

You could take this content at different speeds. If you want to push further through the videos, feel free: but remember, always practice as you go! Just watching the videos will not make you fully understand the language: only actually working with the code yourself will do that. We will be doing more of the Virtual Academy videos in the days ahead.


## Exercises

First, get super-comfortable with simple console operations. `Console.WriteLine` all the things! 
 1. Conditionals should be almost exactly the same as in JavaScript, but just do a little quick practice with them to be sure you're comfortable.
 2. Play with [the default system types](https://msdn.microsoft.com/en-us/library/83fhsxwc.aspx). There's a lot of 'em!
 3. Fill an array with some dummy data and try to perform the CRUD (CREATE, READ, UPDATE, DELETE) operations on the data. Be sure you can easily loop through the array and output the data to the screen.
 4. Get very comfortable with creating a solution and adding projects and class files to it.


## Write a game

One thing I quite like to do with a new language in the console is to write a text-based [Roguelike](https://en.wikipedia.org/wiki/Roguelike) game: a simple game where the player, all the objects terrain are represented as text characters. There's a surprising amount of complexity you can add, but you can also keep it extremely basic. There's a storied history of Roguelikes stretching back to <a href="https://en.wikipedia.org/wiki/Hack_(video_game)">Hack</a>.

Of course, you can write whatever test/demo projects you like! However, each day this week we'll walk you through making a very simple console game using C#. We're taking the TDD approach so you'll get some familiarity with writing xUnit tests and making them pass.

Today, try just doing [the setup](https://github.com/dev-academy-phase4/cs/blob/master/week1/spiral/setup.md).
