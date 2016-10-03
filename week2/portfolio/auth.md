# Authentication

ASP.NET MVC does a pretty good job of scaffolding simple username/password authentication. Let's see about adding to that with some third-party auth.


## Don't commit secrets!

First things first: create a separate secrets config. We should never be committing API keys and secrets to source control (see <a href="https://rosspenman.com/api-key-exposure">Accidental API Key Exposure is a Major Problem</a>). Instead, we can take advantage of the `file` feature in `Web.config` to grab runtime variables from a file that never touches GitHub.

Open the `Web.config` for the solution (note that there's also one inside the `Views` folder, but you want the main one). You'll see a bunch of [XML](https://developer.mozilla.org/en-US/docs/Glossary/XML) defining how the application behaves. If there's any configuration to be done, it's usually in this file. It's divided into major sections: look for the one labelled `appSettings` (it should be near the top).

```cs
  <appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
  </appSettings>
```

Modify this slightly by adding an attribute to the `appSettings` element so it looks like this:

```cs
  <appSettings file="Secrets.config">
```

This means, "check inside the element, but _also_ check this file for more configuration." Now, create the file. Right click the Portfolio project and select _Add_ / _New Item..._. Make sure _Web_ is selected on the left hand side, then choose _Web Configuration File_ as the template. Name the file `Secrets.config`.

Immediately put it in `.gitignore`! You can either use Team Explorer and right-click / ignore, or edit the file directly. It's really important that this file go nowhere near version control.

Next, open `Secrets.config` and discard everything you find there! No, really. The only thing you want in there right now is this:

```cs
  <appSettings>
  </appSettings>
```

Later, this is where we'll go to put the app IDs and secrets from the various third-party services. [Here's](SampleSecrets.config) an example. As you can see, it's really just a series of key/value pairs.


## HTTPS please

Every web app should be HTTPS by default. Google will [penalise](http://motherboard.vice.com/read/google-will-soon-shame-all-websites-that-are-unencrypted-chrome-https) those that aren't secure by flagging them in the browser and ranking them lower in search results. Fortunately it's extremely easy to set up. First, find the `FilterConfig` class in `App_Start` and add the following line to the static method `RegisterGlobalFilters`:

```cs
  filters.Add(new RequireHttpsAttribute());
```

This adds the `RequireHttps` attribute to every controller in your application. Next, select `Portfolio` in Solution Explorer and hit F4 to open the properties paneif it's not already open. Change `SSL Enabled` to `True` and copy the SSL URL. Open the Property Pages by right clicking on `Portfolio` in Solution Explorer and choosing `Properties`. Yep, it's pretty confusing that they're both almost the same! Select _Web_ on the left hand side, and paste your new HTTPS URL into _Project URL_. Fire up the site in debug mode to check that the default URL is working correctly.


## Create some accounts

Wander off to one of the various providers (Google, Facebook etc) and make some apps to login with. The redirect URL will be `https://localhost:44300/signin-google` (or whatever port/service name combination you have).


## Store the IDs and secrets

In your `Secrets.config` file, add key/value pairs for each of your secrets. Use [the example](SampleSecrets.config) file as a guide.


## Enable the authentication methods

In `Startup.Auth.cs`, uncomment each service that you're planning to use and add your configuration values. You load each value from the config file like so:

```cs
app.UseFacebookAuthentication(
  AppId: ConfigurationManager.AppSettings["FacebookAppId"],
  AppSecret: ConfigurationManager.AppSettings["FacebookAppSecret"]
);
```

More detail can be provided using the relevant `AuthenticationOptions` object. Here's a Twitter example:

```cs
app.UseTwitterAuthentication(new TwitterAuthenticationOptions()
{
    ConsumerKey = ConfigurationManager.AppSettings["TwitterConsumerKey"],
    ConsumerSecret = ConfigurationManager.AppSettings["TwitterConsumerSecret"],
    CallbackPath = new PathString(ConfigurationManager.AppSettings["TwitterRedirectUri"]),
    BackchannelCertificateValidator = null
});
```

(Note that for Twitter, setting the cert validator to null seems to be required to avoid errors.) Run your site again in debug mode and there should be new buttons on the login page corresponding to the third-party providers you've added.
