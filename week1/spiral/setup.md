### Setup

To begin with, create a new solution. You can call it what you like: in keeping with the Enspiral theme, we'll call ours `Spiral`. You may as well follow the uppercase convention for .NET solution/project names, most everyone else does.

 - For the project type, remember to choose _Console Application_.

In the solution explorer, right-click the solution name and choose _Add_, then _New Project_. Choose _Class Library_ for the project type, and name it `SpiralTests`.

Right click `SpiralTests` in the solution explorer. Choose _Add_, then _Reference_. You should see a popup with a checkbox labelled `Spiral` (if you don't, click _Projects_ / _Solution_ on the side). Check the box, then click _OK_. This lets `SpiralTests` _reference_ namespaces, classes and methods in the `Spiral` project.

We need to add the [xUnit](https://xunit.github.io/) package to do our testing with. Right click on the `SpiralTests` project and choose _Manage NuGet packages_. Click _Browse_ on the left side, then type 'xunit' in the search box. Select the xUnit package and click _Install_. While you're at it, do the same thing for _xunit.runner.visualstudio_.

So, let's write our first test! In `SpiralTests`, rename `Class1.cs` to `ProgramTests`. If it offers to rename other things for you, choose _Yes_. Make `ProgramTests` look like this:

```cs
using Xunit;

namespace SpiralTests
{
    public class ProgramTests
    {
        [Fact]
        public void Working ()
        {
			Assert.True(true);
        }
    }
}
```

Go to the test explorer and choose _Run All_. The test you've just written will be discovered and run after the project builds. Hopefully you should see a little green tick.

So there's a bit going on here. Tests are normally given the _decorator_ `[Fact]`. They have accessibility `public` and don't return anything. If you're familiar with tape testing in JavaScript, the above test is equivalent to:

```js
test('Working', t => {
  t.ok(true)
})
```
