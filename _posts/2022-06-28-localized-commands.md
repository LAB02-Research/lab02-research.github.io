---
layout: post
title: Localized Commands
subtitle: Why, Microsoft?
thumbnail-img: /assets/img/localization_128px.png
tags: [localization,windows,microsoft,hass.agent,home assistant,hass,domotica,automation,csharp]
---

Why make it easy when it can also be needlessly complicated?

For HASS.Agent, an urlacl rule has to be added to be able to reserve the local API's post. Previously, this was done as such:

`netsh http add urlacl url=http://+:5115/ user=%USERDOMAIN%\%USERNAME%`

The downside is: when a user has a different admin account, it won't allow the non-admin user to start HASS.Agent. To circumvent this, the `Everyone` account can be used.

You'd think it'll just be this:

`netsh http add urlacl url=http://+:5115/ user=Everyone`

And you'd be right! Unless the user has a non-English UI language.. And in case you're thinking, can we just use the [SID](https://en.wikipedia.org/wiki/Security_Identifier)? Nope! 

So we have to first determine the language specific variant of the `Everyone` group, which thankfully can be done relatively easy in C#:

```C#
var localizedEveryoneGroupName = Principal.FindByIdentity(new PrincipalContext(ContextType.Machine), IdentityType.Sid, "S-1-1-0")?.Name ?? "Everyone";
```

We're defaulting to `Everyone` if the command fails, but it shouldn't. `S-1-1-0` is the SID of the `Everyone` group.

Note: this requires the `System.DirectoryServices.AccountManagement` nuget.
