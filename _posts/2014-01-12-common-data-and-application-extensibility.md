---
layout: post
category : community
tagline: "Common Data and Application Extensibility"
tags : [community]
---
{% include JB/setup %}

[Molajo](https://github.com/molajo) is an application I have been writing for a couple of years now
with a focus on providing frontend devs
total control over Views and the ability to provide data intensive application processing without having
to write (very much) PHP code.

Molajo has two primary areas where developers can extend the application.
The first is [Views](https://github.com/Molajo/Molajo/tree/master/Source/View),
the second is [Plugins](https://github.com/Molajo/Molajo/tree/master/Source/Plugin). (And, of
course, any framework-agnostic PHP package like many listed on Packagist.)

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

"Molajo-specific" is isolated to a couple of packages, the
[Molajo](https://github.com/Molajo/Molajo) application, itself, which is essentially a collection of Views
and Plugins that rest on a common set of controllers and models which guide logic flow defined in the
[Framework](https://github.com/Molajo/Database) package.

My challenge is, I'd love to also make certain `plugins` and `views` are framework-independent and easy to use
in different PHP applications without compromising the goal of ease of use for my target
frontend developer group. Views are pretty easy to share given common Rendering applications like
[Mustache](http://phly-mustache.readthedocs.org/en/1.2.0/syntax.html)
and [Twig](http://twig.sensiolabs.org/) and the Molajo rendering package uses an Adapter approach. So, I am
comfortable with interoperability with Views.

Plugins are a little bit more of a challenge. On one hand, you want to make it easy for developers to
very quickly tweak the application, but it can result in a [silo effect](http://en.wikipedia.org/wiki/Information_silo)
on interoperability.

Additionally, the challenge of application data presents problems for true interoperability. For both Plugins
and Views, I have used standard convention, like `$this->row`, `$this->model_registry`,
and `$this->parameters`, to build in consistency and make data available, when and where needed.
That makes it possible to swap out tokens for smileys,
for example, or to retrieve and store data, like comments, in a data object that automatically
be available to render the comment view.

The data objects are injected as an array and
passed through the Event system to avoid incurring any Molajo-specificness on the Event package.
The plugins then act on the data, which is returned to
 the front controller which updates the IoCC entry, when event processing is complete.

Certain 'common' classes are also instantiated using dependency injection approaches and passed
through the `Event` and `Render` packages for use in translations,
image processing, authorisation, file and resource processing, and so on. Those classes all use
Interfaces to build in flexibility.

All of that works very well and provides an easy to use environment. But, it also restricts the plugins usability
to those specific data objects. It also raises a little uneasiness in me about whether or not this constitutes
'global data' or if in using proper dependency injection approaches the issues of global data are avoided.

My questions relate to how best to handle the little bit of the software that is an application's "special sauce"
 so that it is easy for developers to be productive without sacrificing interoperability and
using poor data approaches?

What are good ways of handling data objects and making the data available throughout the application
that provide flexibility for developers to extend the application without
requiring them to create classes or have excellent programming skill?

Is it a bad thing or a necessary thing
to have extensibility in your application that precludes those objects from ease of use in other applications?

Your ideas and examples are welcome. Thanks!
