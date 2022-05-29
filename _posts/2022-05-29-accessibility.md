---
layout: post
title: Accessibility
subtitle: Making HASS.Agent screenreader friendly.
tags: [accessibility,hass.agent,home assistant,hass,domotica,automation,csharp]
---

When you're a single developer working on a project in your spare time, next to a full-time job, you're going to have to make choices on where to invest your efforts. You can't work out every feature at once, and some bugs get ignored.

Earlier this month, GitHub user [@blindndangerous](https://github.com/blindndangerous) pointed me to the fact that HASS.Agent [doesn't play well with screenreaders](https://github.com/LAB02-Research/HASS.Agent/issues/65) *at all*. And he was of course absolutely right; none of the components were properly named and labeled. 

Since I didn't have any experience, I started reading up on some documentation. Microsoft's actually been [doing pretty well](https://blogs.microsoft.com/blog/2021/04/28/doubling-down-on-accessibility-microsofts-next-steps-to-expand-accessibility-in-technology-the-workforce-and-workplace/) in that area thankfully. Some links that helped me (I'll explained their relevance later on):

[General Info](https://docs.microsoft.com/en-us/dotnet/desktop/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form?view=netframeworkdesktop-4.8&viewFallbackFrom=netdesktop-6.0)
[Best Practices](https://docs.microsoft.com/en-us/dotnet/framework/ui-automation/accessibility-best-practices)

[Accessible Role](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.accessiblerole?view=windowsdesktop-6.0)
[Accessible Name](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.control.accessiblename?view=windowsdesktop-6.0)
[Accessible Description](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.control.accessibledescription?view=windowsdesktop-6.0#system-windows-forms-control-accessibledescription)
[Accessible Events](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.accessibleevents?view=windowsdesktop-6.0)

They've even released a (free) tool which greatly helped me analyze HASS.Agent's interface:

[Accessibility Insights](https://accessibilityinsights.io)
