---
layout: post
title: Accessibility
subtitle: Making HASS.Agent screenreader friendly.
tags: [accessibility,hass.agent,home assistant,hass,domotica,automation,csharp]
---

When you're a single developer working on a project in your spare time, next to a full-time job, you're going to have to make choices on where to invest your efforts. You can't work out every feature at once, and some bugs get ignored.

Earlier this month, GitHub user [@blindndangerous](https://github.com/blindndangerous) pointed me to the fact that HASS.Agent [doesn't play well with screenreaders](https://github.com/LAB02-Research/HASS.Agent/issues/65) *at all*. And he was of course absolutely right; none of the components were properly named and labeled (don't mistake this for the object's reference name like `LblCommands`, that's just internal). And even though it wouldn't really lead to new fancy features, this would be well worth focussing on - so I more or less dropped all other tickets.

Since I didn't have any prior experience, I started reading up on some documentation. Microsoft's actually been [doing pretty well](https://blogs.microsoft.com/blog/2021/04/28/doubling-down-on-accessibility-microsofts-next-steps-to-expand-accessibility-in-technology-the-workforce-and-workplace/) in this area thankfully. Some links that helped me:

[General Info](https://docs.microsoft.com/en-us/dotnet/desktop/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form?view=netframeworkdesktop-4.8&viewFallbackFrom=netdesktop-6.0)<br/>
[Best Practices](https://docs.microsoft.com/en-us/dotnet/framework/ui-automation/accessibility-best-practices)

[Accessible Role](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.accessiblerole?view=windowsdesktop-6.0)<br/>
[Accessible Name](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.control.accessiblename?view=windowsdesktop-6.0)<br/>
[Accessible Description](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.control.accessibledescription?view=windowsdesktop-6.0#system-windows-forms-control-accessibledescription)<br/>
[Accessible Events](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.accessibleevents?view=windowsdesktop-6.0)<br/>

They've even released a (free) tool which greatly helped me analyse HASS.Agent's interface:

[Accessibility Insights](https://accessibilityinsights.io)

For instance, this is an analysis of the `commands` label on the main window:

![image](https://user-images.githubusercontent.com/81011038/170864654-05c9c66c-7c41-4d84-ad35-a423415c1aad.png)

![image](https://user-images.githubusercontent.com/81011038/170864668-ed15a3f8-05a6-43dc-91bc-a477073e2c18.png)

You can see that while it's grouped properly, and has name and controltype set, it doesn't yet have a access- or acceleratorkey set (optional, but recommended). When I run the automation test, I get the 'all clear' (which means that it can be properly used by accessibility tools as-is):

![image](https://user-images.githubusercontent.com/81011038/170864740-f70caf9b-be60-4ff0-80c5-a53f91d8cc47.png)

It doesn't catch everything, for instance: you still have to make sure the tab indexes are set correctly so the user can easily tab through the controls, and you have to make sure there are logical keybindings for every form/control.

----

Practically, you have to go through every single control, and think about primarily these three values:

![image](https://user-images.githubusercontent.com/81011038/170864857-151d3fb2-24b3-46c7-8648-f5337ae6e39a.png)

It's a lot of manual labor with trial-and-error on what works. You also have to keep consistency in mind, and some basic rules (for instance, don't add the control type to `AccessibleName`). Afterwards, you need to check the tab index and keybinding, and lastly run the [Accessibility Insights](https://accessibilityinsights.io) automation-test.

As always, the best way to go is to implement this from day one!
