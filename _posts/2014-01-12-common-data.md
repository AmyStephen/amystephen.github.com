---
layout: post
category : community
tagline: "Common Data and Application Extensibility"
tags : [community]
---
{% include JB/setup %}

[Molajo](https://github.com/molajo) is an application I have been writing for a couple of years now
with a focus providing frontend devs
total control over Views and the ability to provide data intensive application processing without having
to write (very much) PHP code.

Beyond adding packages, Molajo has two primary areas where developers can extend the application.
The first is [Views](https://github.com/Molajo/Molajo/tree/master/Source/View),
the second is [Plugins](https://github.com/Molajo/Molajo/tree/master/Source/Plugin).

In the interest of software interoperability, I have worked very hard to ensure all packages (
[Authorisation](https://github.com/Molajo/Authorisation)
[Cache](https://github.com/Molajo/Cache),
[Database](https://github.com/Molajo/Database),
[Email](https://github.com/Molajo/Email),
[Event](https://github.com/Molajo/Event),
[Fieldhandler](https://github.com/Molajo/Fieldhandler),
[Filesystem](https://github.com/Molajo/Filesystem),
[Http](https://github.com/Molajo/Http),
[IoC](https://github.com/Molajo/IoC),
[Language](https://github.com/Molajo/Language),
[Render](https://github.com/Molajo/Render),
[Resource](https://github.com/Molajo/Resource),
[Route](https://github.com/Molajo/Route), and
[User](https://github.com/Molajo/User) are written in a framework-agnostic fashion.
Those packages can be used in any PHP application, there is absolutely no Molajo-specific logic.

"Molajo-specific" is isolated to a couple of packages, the Molajo application and the Framework package. Both are
basically configuration, logic flow, custom Views and Plugins.

I'd love to also make certain `plugins` and `views` are framework-independent and easy to use
in different PHP applications. But, I don't want to compromise the goal of ease of use for my target
frontend developer group.

For both Plugins
and Views, I have used standard convention, like `$this->row`, `$this->model_registry`,
and `$this->parameters`, to build in consistency and make data available, when and where needed.
That makes it possible to swap out tokens for smileys,
for example, or to retrieve and store data, like comments, in a data object that automatically
be available to render the comment view.

The data objects are injected as an array and
passed through the Event system. The plugins act on the data, which is returned to
 the front controller which updates the IoCC entry, when event processing is complete.

Certain classes are also instantiated using dependency injection approaches and passed
through the `Event` and `Render` packages for use in translations,
image processing, authorisation, file and resource processing, and so on.

All of that works very well and provides an easy to use environment. But, it also restricts the plugins usability
to Molajo. It also raises a little uneasiness about whether or not this constitutes 'global data' and if that
is a bad thing.

My question relates to how best to handle the little bit of the software that is your application's "special sauce", as
it were, intended to make it easy for developers to be productive without sacrificing interoperability and
using poor data approaches.

What are good ways of handling data objects and making the data available throughout the application
that provide flexibility for developers to extend the application without
requiring them to create classes or have excellent programming skill? Is it a bad thing or a necessary thing
to have extensibility in your application that precludes those objects from ease of use in other applications?

Ideas and examples are welcome. Thanks!
