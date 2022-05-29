---
layout: post
title: Accessibility
subtitle: Making HASS.Agent screenreader friendly.
tags: [accessibility,hass.agent,home assistant,hass,domotica,automation,csharp]
---

When you're a single developer working on a project in your spare time, next to a full-time job, you're going to have to make choices on where to invest your efforts. You can't work out every feature at once, and some bugs get ignored.

Earlier this month, GitHub user [@blindndangerous](https://github.com/blindndangerous) pointed me to the fact that HASS.Agent [doesn't play well with screenreaders](https://github.com/LAB02-Research/HASS.Agent/issues/65) at all. And he was of course absolutely right; none of the components were properly named and labeled.

Since I didn't have any experience, I started reading up on some documentation. 