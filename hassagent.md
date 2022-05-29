---
layout: page
title: HASS.Agent
cover-img: https://raw.githubusercontent.com/LAB02-Research/HASS.Agent/main/images/logo_128.png
thumbnail-img: https://raw.githubusercontent.com/LAB02-Research/HASS.Agent/main/images/logo_128.png
share-img: https://raw.githubusercontent.com/LAB02-Research/HASS.Agent/main/images/logo_128.png
subtitle: Home Assistant companion app for Windows
tags: [Home Assistant,HASS,HASS.Agent,companion,app,domotica,automation,Windows]
---

HASS.Agent is a Windows-based client (*companion*) application for [Home Assistant](https://www.home-assistant.io), developed in .NET 6.

### Contents

 * [Functionality](#functionality)
 * [Screenshots](#screenshots)
 * [Help and Documentation](#help-and-documentation)
 * [Articles](#articles)

----

### Functionality

Summary of the core functions:

* **Notifications**: receive notifications, show them using Windows builtin toast popups, and optionally attach images. 
  - *This requires the installation of the [HASS.Agent Notifier integration](https://github.com/LAB02-Research/HASS.Agent-Notifier)*.

* **Quick Actions**: use a keyboard shortcut to quickly pull up a command interface, through which you can control Home Assistant entities - or, assign a keyboard shortcut to individual Quick Actions for even faster triggering.

* **Commands** (currently **20**): control your PC (or other Windows based device) through Home Assistant using custom- or built-in commands.

* **Sensors** (currently **29**): send your PC's sensors to Home Assistant to monitor every aspect of your device.

* **Satellite Service**: use the service to collect sensordata and execute commands, even when you're not logged in. 

* All entities are dynamically acquired from your Home Assistant instance.

* Commands and sensors are automatically added to your Home Assistant instance.

----

### Screenshots

Notification examples:

![Image-based toast notification](https://raw.githubusercontent.com/LAB02-Research/HASS.Agent/main/images/hass_agent_toast_image.png)  ![Text-based toast notification](https://raw.githubusercontent.com/LAB02-Research/HASS.Agent/main/images/hass_agent_toast_text.png)

This is the Quick Action window you'll see when using the hotkey. This window automatically resizes to the amount of buttons you've added:

![Quick Actions](https://raw.githubusercontent.com/LAB02-Research/HASS.Agent/main/images/hass_agent_quickactions.png)

You can easily configure a new Quick Action, HASS.Agent will fetch your entities for you:

![New Quick Actions](https://raw.githubusercontent.com/LAB02-Research/HASS.Agent/main/images/hass_agent_new_quickaction.png)

The sensors configuration screen:

![Sensors](https://raw.githubusercontent.com/LAB02-Research/HASS.Agent/main/images/hass_agent_sensors.png)
    
Adding a new sensor is just as easy:

![Sensors](https://raw.githubusercontent.com/LAB02-Research/HASS.Agent/main/images/hass_agent_new_sensor.png)

Easily manage the satellite service through HASS.Agent:

![Service](https://raw.githubusercontent.com/LAB02-Research/HASS.Agent/main/images/hass_agent_satellite_service.png)

You'll be guided through the configuration options during onboarding:

![Onboarding Task](https://raw.githubusercontent.com/LAB02-Research/HASS.Agent/main/images/hass_agent_onboarding_startup.png)
    
----

### Help and Documentation

Stuck while installing or using HASS.Agent, need some help integrating the sensors/commands or have a great idea for the next version? There are a few channels through which you can reach out:

* [Github Tickets](https://github.com/LAB02-Research/HASS.Agent): Report bugs, feature requests, ideas, tips, ..

* [Documentation](https://hassagent.readthedocs.io/): Installation, configuration and usage documentation, as well as examples.

* [Discord](https://discord.gg/nMvqzwrVBU): Get help with setting up and using HASS.Agent, report bugs or just talk about whatever.

* [Home Assistant forum](https://community.home-assistant.io/t/hass-agent-a-new-windows-based-client-to-receive-notifications-perform-quick-actions-and-much-more/369094): Bit of everything, with the addition that other HA users can help as well.

Starting from zero, and want to learn what HASS.Agent's about and how to start? Be sure to check the [introduction article](https://hassagent.readthedocs.io/en/latest/introduction/), and optionally the [command basics](https://hassagent.readthedocs.io/en/latest/commands/command-basics/).

If you want to help with the development of HASS.Agent, check out the [Helping Out](#helping-out) section for (translating) info.

----

### Articles

Liam Alexander Colman from [Home Assistant Guide](https://home-assistant-guide.com) was kind enough to write an article about HASS.Agent: [Integrate Home Assistant with Windows using HASS.Agent](https://home-assistant-guide.com/2022/04/20/integrate-home-assistant-with-windows-using-hass-agent/). The website's full of useful articles, worth having a look :)

----
