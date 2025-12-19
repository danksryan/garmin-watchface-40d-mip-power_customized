# Custom Updates
Just a personal fork to start playing with watch faces. ONLY tested for Enduro 3, may work for others but I havent tried...

Primary changes from the base version are:
* replaced HR with Body Battery 
* added days of battery remaining
* reduced frequency of heart rate polling

Original readme is below.

![](docs/cover.png?raw=true "Title")

# 40D MIP Power
is a minimalist Watch Face that maximizes battery life (40-50 days on Enduro 3 instead of ~20 days), and optimized for MIP displays. Smart features for health tracking:
* Colored heart rate zones
* Contextural ring light for high HR, high stress and move bar

Submitted to Garmin store: https://apps.garmin.com/apps/9db8afa7-631a-46f0-988a-8efab4f5fc3a

# The story

Garmin Enduro 3 is a great watch but unfortunately doesn't deliver on the promised 36 days of battery. Similarly to many other people on Garmin forums and reddit, my watch was consuming about 4-5% per day which translates to 20ish days without using any activities.

So I decided to investigate, and the result is this watch face that consumes about 2-2.5% per day, giving you 40-50 days of MIP power!

This battery consumption could be achieved on Enduro 3 on following settings:
* minimum backlight level with 4s time out
* Touch disabled
* Gesture disabled
* sound & alerts disabled
* phone connection enabled
* notifications disabled
* Sleep watch face disabled

The watch face has a built-in power saving mode and can last more than 12h for 1% during night. This is much more power efficient than the built in sleep watch face which only lasts around 10h for me.

You can further reduce battery by disabling the ring light features and disabling active HR update in watch face settings.

# Feature list

* White background by default (configurable)
* Configurable setting for showing seconds
* The watch face and HR data updates once per minute by default to save power
* HR update once per second once in zone 2 or above (configurable)
* Colored heart rate zones - standard Garmin heart zone colors
* Contextural ring light  (configurable)
  * Blue - reminder to move after inactive for 2h, based on Garmin move bar
  * Orange - stress level high during last 3min (one sample per min)
  * Red - current heart rate in zone 5 or higher
* Automatically switch to power saving mode (show time only) when inactive for 10 min (configurable)

[!WARNING]
Designed for MIP display only. There is not built-in burn-in protection needed for AMOLED displays

# Design Priorities

* Prioritize Battery life over esthetic
* Heart rate tracking
* Smart ring light - reminder to reduce stress and HR

# How it works

Without knowing enough details how the Garmin hardware consume battery through CPU, graphics, memory and display, this project tries to 
* minimize the code and resources
* minimize the graphics operations
* minimize the display update

Following strategies have been applied
* Don't use View Layout as resource but rely on manual layout
* Minimize number graphics calls, e.g., don't paint minutes in different color
* Keep only minimum data fields during low power / always on mode
* All data fields update once per minute
* Minimize the icons used (no battery icon)
* No custom fonts
* Minimize class hierachy and no use of advanced data structure
* power saving mode when watch is inactive for some time


Follow strategies didn't work and was abandoned
* Don't paint data fields that have overlap with each out to avoid layered rendering
* Don't clear background on each display update
* Update data field and re-render only when data field has changed, e.g., hour should be refreshed only every 60min


### Attributions

* The project was initially forked from https://github.com/blotspot/garmin-watchface-protomolecule by blotspot
