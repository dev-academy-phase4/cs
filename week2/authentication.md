# Authentication

If you've created any of the default MVC sites by now with "Authentication: Individual User Accounts" enabled, you've already gotten the idea that Visual Studio takes care of quite a bit of the authentication boilerplate for you! In general, this is a good thing: remember, don't roll your own security if you can possibly avoid it.

Plugging in third-party OAuth-based security is fairly straightforward. Try going through [Code! MVC 5 App with Facebook, Twitter, LinkedIn and Google OAuth2 Sign-on](http://www.asp.net/mvc/overview/security/create-an-aspnet-mvc-5-app-with-facebook-and-google-oauth2-and-openid-sign-on). Note that some of the screenshots describing how to sign up for the various services are a bit dated (Facebook and Google's processes have changed) but still possible to navigate.


## Portfolio: authentication

Let's hook up Google, Twitter and Facebook as sign-in options with a bit of [third-party auth goodness](portfolio/auth.md).


## Resources

 - [ASP.NET MVC: Keep Private Settings Out of Source Control](http://www.codeproject.com/Articles/755682/ASP-NET-MVC-Keep-Private-Settings-Out-of-Source-Co)
 - [Best practices for deploying passwords and other sensitive data to ASP.NET and Azure App Service](http://www.asp.net/identity/overview/features-api/best-practices-for-deploying-passwords-and-other-sensitive-data-to-aspnet-and-azure)
