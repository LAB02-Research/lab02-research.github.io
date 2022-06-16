---
layout: post
title: New release - 2022.12.0
subtitle: MediaPlayer integration, webview component and screenreader support.
thumbnail-img: /assets/img/new_128px.png
tags: [new,release,2022.12.0,hass.agent,home assistant,hass,domotica,automation,csharp]
---

This release contains two major new features: the mediaplayer integration, and the webview component. I'll give them both a short introduction:

---

You can now control your device as if it were a regular mediaplayer, regardless of what application's actually playing. It has support for 'currently playing' info, but only if the application uses it (e.g. Spotify does, VLC doesn't). And: you can also now use your PC as a text-to-speech device! The implementation's still basic and will be improved in the coming releases. Make sure to check the new docs for info on how to configure and use (listed in the release notes).

The new webview component uses Edge's core to display webpages, without having to launch a full fledged browser. You need Microsoft's webview runtime, but the installer will take care of that for you - or, if you install manually, you'll get the option to download on first use.

It's of course implemented in a new command: WebView. You can easily configure what url to show, its location, size and some other settings. Use the new `configure command parameters` button when adding a webview command.

The second webview implementation is that you can now configure the tray icon's right mouseclick-button to show a webview instead of the menu. Use this to for instance easily show a dashboard! Check out the new Configuration -> Tray Icon page for all options.

---

Apart from the new features, the quickactions received some love: the creation page has its layout refreshed, and you can now directly bind your own commands to a quickaction. This means that either through the quickactions popup, or a hotkey, you can trigger any command you've configured. Because it doesn't go by Home Assistant, it's really fast :) 

This release also adds initial support for screenreaders (thanks for pointing it out to me @blindndangerous). It was a lot of work (which is why this release took longer than usual), but I'm glad the basics are done. It's not completely covered, so let me know what can be improved. For those interested, I wrote a short blogpost about it: https://lab02-research.org/2022-05-29-accessibility.

Not all items on the 'planned for next release' list are done, but it's been nearly two months since the last release so I thought I'd roll this one out for everyone to use. The next release will be bugfixes, enhancements and new commands/sensors (so no large new features). 

A 'heads up': because of the summer months, I'll be either busy at work filling in for coworkers on vacation, or on vacation myself, so the next release might take some time. But I'll still try to answer questions/tickets as soon as I can, as always :)

---

### Features & improvements

* Add media_player capabilities to HASS.Agent [#31] (thanks @DeftNerd)
  * This requires the new MediaPlayer integration, available through HACS
  * For configuration info, check the new docs:
    * https://hassagent.readthedocs.io/en/latest/mediaplayer/mediaplayer-usage-and-examples/

* New command: WebView
  * Can be used to show any webpage, without having to launch a full-fledged browser
  * Use the new `configure command parameters` button to easily configure what where and how to show
  * Also usable through an Action (so you can set what url to show dynamically in HA)
  
* HASS.Agent now supports screenreaders, based on Microsoft's recommendations [#65] (thanks @blindndangerous)
  * Forms and controls have been assigned roles, names and descriptions
  * Controls have been assigned a tab-order value
  * Buttons and textboxes have been assigned a keycode
  
* The tray icon's right mouseclick can be configured [#59] (thanks @paccerdk)
  * By default, it shows an options menu
  * You can now configure it to show a webview page
    * For instance, a HA dashboard (your HA url is set by default)
	* Enable `keep page loaded in the background` to make sure it shows up instantly
	* If you resize the webview, it'll store the new size as its default
  * Configurable through the new Configuration -> Tray Icon page
  
* New documentation: https://hassagent.readthedocs.io
  * GitHub's wiki pages won't be updated anymore and will be removed soon
  * Missing docs, or have additions yourself? Let me know :)
  
* The QuickAction add/modify window has been updated

* You can now bind your own commands to a QuickAction
  * Choose the new `HASS.Agent Commands` domain to show your entities
  
* The tray icon's default theme has been aligned with the rest of HASS.Agent
	
* The 'Notification API' has been renamed to 'Local API'
  * This is to reflect the fact that the API now has multiple uses
  * Onboarding and configuration have been changed accordingly
  
* New command: SendWindowToFront (thanks **ChrisRosenkreuz23**)
  * Can be used to force a specified process to the foreground
  * Usable as a regular command, or through an action

* Translations:
  * New translation: Dutch
  * New translation: German (thanks **Gerd**, **JbbDE**, **r100gspd**, **Sebastian Tobias Koch** and **Syntox**)
    * Note: this translation is only 68% done
  * New translation: Spanish (thanks **Carlos Cordero**)
    * Note: this translation has mostly automated translations, results may vary  
  * If you're proficient in German or Spanish, please improve!
  * There are a bunch of languages waiting to get some more love, like French and Polish
  * You can dive right in (it's online, easy, and no coding required): https://poeditor.com/join/project/R7HIVG0wie

* The devicename is now validated and sanitized [#53] (thanks @mdrichardson)
  * Home Assistant rejects your device if it contains certain special characters
  * The check is done during onboarding and when saving configuration changes
    * So you might get a notification saying `you've changed your device name`, that's actually the sanitation being applied
	* Your sensors and commands will keep working

### Bugfixes

* Satellite Service: unable to create non-switch command types (thanks **jello**)

* The MultipleKeysCommand now correctly escapes a bracket (thanks **ChrisRosenkreuz23**)
  * Escaping can be done by using a backslash, so `[` is `[\[]` and `]` is `[\]`]
  
* QuickAction: add/mod window crashes when no entity is found (thanks **jello**)

* Username is now put between quotes when registering the local API's port to support spaces (thanks **beecho01**)

---

Click [here to download](https://github.com/LAB02-Research/HASS.Agent/releases/download/2022.12.0/HASS.Agent.Installer.exe) the installer, or [here to go](https://github.com/LAB02-Research/HASS.Agent/releases/tag/2022.12.0) to the release notes.
