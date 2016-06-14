# year-clock

What is a year clock?

A year clock is a device which looks very much like a 12-hour analog clock, but instead of telling the time, it shows you *approximately* the current day of the 12-month calendar year.

Why build a year clock?

I wanted to build a physical representation of how I have always visualized the passing year in my mind (this obviously differs from a traditional wall calendar). It provides a quick view of how much time is left in the month, the year, a quarter, a season, etc...

This was a fun, simple, quick and inexpensive project.

Project Overview

The way this project works is simple: instead of allowing the hour hand of the clock to make a full rotation every 12 hours, we slow it down such that it takes an entire year to complete one cycle.

The core of this project is made up of three main parts:

a battery-powered clock movement (available from most craft stores)
a simple microcontroller (externally powered)
a transistor
The clock movement advances the minute and hour hands with each tick of the second hand. The transistor is inserted between the battery and the clock movement. The microcontroller is connected to the transistor and only allows the clock movement to tick after a certain amount of time has passed. To determine how often the second hand should tick, we need to do some math* ...

We first need to figure out how many ticks of the second hand it takes to complete a 12-hour cycle.

60 seconds x 60 minutes x 12 hours = 43,200 seconds

We then need to figure out how many actual seconds there are in a year:

60 seconds x 60 minutes x 24 hours x 365 days = 31,536,000 seconds

We finally divide our total number of seconds in a year by the number of available ticks (or seconds) on our 12-hour clock:

31,536,000 / 43,200 seconds = 730seconds

This tells us that our microcontroller needs to allow the clock movement to advance the second hand by one tick every 730 seconds (roughly 12 minutes) in order for it to take a year for the hour hand to make once around the clock face.

Limitations*

This project is very much a proof of concept and prototype for a much more refined version in the future and therefore I feel the math above is "good enough".

The biggest limitation of this project is its accuracy. Most simple microcontrollers do not keep good time on their own and can vary greatly based upon CPU load as well as environmental factors such as temperature and humidity. This project also doesn't take leap-years or Daylight Savings Time into account.

Over time, this project will suffer from clock skew and will need to be manually adjusted. This is easy to do using the dial on the back of the clock movement. I used this Year Clock in my cubicle at work for over a year and only had to adjust it a few times.
