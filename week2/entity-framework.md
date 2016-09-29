# Entity Framework

Remember [Knex.js](https://knexjs.org)? It's the SQL builder we used with databases when writing Express.js servers. It let us work with the database in a predictable way from code without writing raw SQL.

In ASP.NET, there is a lot of legacy code that still uses raw SQL, but most modern applications use an Object Relational Mapper (ORM). Although there are various alternatives, Microsoft's [Entity Framework](http://www.entityframeworktutorial.net/what-is-entityframework.aspx) is the most widely used and it's what we'll introduce you to. We're going to focus on a workflow called "Code First", which basically means we write C# code and it shows up in the database as entities (tables) and records (rows).

To begin with, watch Julie Lerman's [Getting Started with Entity Framework 6](https://app.pluralsight.com/player?course=entity-framework-6-getting-started&author=julie-lerman&name=entity-framework-6-getting-started-m1&clip=0&mode=live) on PluralSight.

## Wait, what's an ORM again?

Here's [a pretty good non-C# specific answer on Stack Overflow](http://stackoverflow.com/a/1279678). It's a high-level approach to databases that attempts to describe the kinds of relationships that exist at the database level using objects and methods that may be more familiar to the programmer. There is some criticism of ORMs (see [Do you need an ORM?](http://enterprisecraftsmanship.com/2015/11/30/do-you-need-an-orm/) for a reasonable summary). Allow me to quote from that article just in case it isn't abundantly clear:

> First of all, I have to point out that writing your own ORM is almost always _a bad idea_.

The italics are ours: don't 'roll your own'! If you're using an ORM, you should definitely use something that's well-tested and proven.


## The Getting Started Series

Try working through [Getting Started with Entity Framework 6 Code First using MVC 5](https://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application). The same warning applies as for the others in this tutorial applies: there will be a link at the top to a newer version of the tutorial, but don't use it for now (that's .NET Core).


## Portfolio: storing jobs

Up till now we've been just populating the view model with hard-coded data. Let's try [hooking up the database](portfolio/storing-jobs.md).


## Resources

 - [Entity Framework Code First to a New Database](https://msdn.microsoft.com/en-us/data/jj572366): this is getting pretty old, but helps introduce some of the EF concepts using a console project.
