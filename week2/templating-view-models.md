# Templating

Server-side templates in ASP.NET are most commonly implemented using Razor templates. These are similar in role (though quite different in syntax) to Handlebars, which you will have encountered during your bootcamp.

To begin with, work through [Introduction to ASP.NET Web Programming Using the Razor Syntax (C#)](http://www.asp.net/web-pages/overview/getting-started/introducing-razor-syntax-c). If you haven't already done much with Razor in the MVA tutorials, make sure you can use each of the examples in a simple view (use `Views.Home` - `Index.cshtml` from any stock MVC application).

You might also want to look at [An Absolute Beginner's Tutorial on HTML Helpers and Creating Custom HTML Helpers in ASP.NET MVC](http://www.codeproject.com/Articles/787320/An-Absolute-Beginners-Tutorial-on-HTML-Helpers-and), which will get you a lot closer to understanding what all those `@Html.` bits in your templates are doing!


## Bootstrap

Once upon a time, Twitter invented a framework for internal use at the company. They called it _Twitter Blueprint_, and it was designed to encourage consistency of user interface across their various tools. It became wildly popular following its release as an open source project in 2011. Nowadays it's hard to find sites that don't use it (or are inspired by it in some way). ASP.NET MVC projects come with it by default, and it's good to be familiar with the overall patterns (grids, breakpoints, etc.) regardless. Review the section on Bootstrap in [Introduction to ASP.NET MVC](https://mva.microsoft.com/en-us/training-courses/introduction-to-asp-net-mvc-8322).


# View models

You might recall that in calls to `res.render()` in Express.js, we pass the name of a Handlebars template and an optional data object containing the information we use to build the view. This is an informal version of the _view model_ concept. In C# a view model is a class that exists only to provide data to the view. It is often made up of several different sets of data, and is not normally stored directly in the database. For example, we might get various kinds of data from the database that we need to build the 'Available Wombats' page:

 - the user's name and id
 - a list of all available wombats, including only their names and ids
 - a single photo of each wombat
 - a list of the latest blog posts to load in a sidebar panel

It's highly unlikely that we are storing this all in one database table. We assemble all the information we need into a view model, then pass it to the view via the controller.


## A note on MVC

[Model-view-controller](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) is a way of thinking about and building software that became very popular in web development, although it has somewhat fallen out of favour due to the emergence of other architectural patterns such as [MVVM](http://www.codeproject.com/Articles/100175/Model-View-ViewModel-MVVM-Explained).

Got capital letter confusion? It's not surprising. [This](http://www.tomdalling.com/blog/software-design/model-view-controller-explained/) is a rather dated (2009) but still good explanation in simple terms. [Can it be explained in simple terms?](http://stackoverflow.com/questions/2626803/mvc-model-view-controller-can-it-be-explained-in-simple-terms) is a popular Stack Overflow answer from 2010. [Here's](http://stackoverflow.com/a/16010705) another good SO answer.


## Tutorials

[Use ViewModels to manage data & organize code in ASP.NET MVC applications](http://rachelappel.com/use-viewmodels-to-manage-data-amp-organize-code-in-asp.net-mvc-applications/) is a pretty good starting point. 


## The 'Getting Started' series

Continue with this tutorial series by completing [Adding a controller](http://www.asp.net/mvc/overview/getting-started/introduction/adding-a-controller) and [Adding a view](http://www.asp.net/mvc/overview/getting-started/introduction/adding-a-view).


## Portfolio: Views and View Models

Even though we haven't covered the database yet, we can still do a lot with the views. We'll start by adding [the work history page](portfolio/work-history.md).
