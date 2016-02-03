## Setting Timeline Intervals ##

By default, the calendar displays blocks of time in 30 minute intervals. This impacts the layout because each appointments will fill the block(s) of time it overlaps.

For example: time intervals are 30 minutes, 12:00am, 12:30am, 1:00am, 1:30, etc. If an appointment is from 12:45 - 1:15 AM it will fill both the 12:30-1am and 1-1:30am blocks.

The number of minutes per time block interval can be configured in the `CalendarSettings` object by setting the `intervalsPerHour` property. By default this is set to 2 which equals 30 minute intervals (60 minuts per hour / 2 = 30 minute intervals). This could be set to 4 (15 minute intervals).
```
CalendarSettings settings = new CalendarSettings();
settings.setIntervalsPerHour(4);

//you can pass through constructor
Calendar calendar = new Calendar();
calendar.setSettings(settings);
```

## Setting Timeline Intervals Height ##

You can also configure the height (in pixels) of a block of time. By default the 30 minute time blocks are 30px in height. This can be changed by setting the `pixelsPerInterval` property.

```
//set time block height to 50px
settings.setPixelsPerInterval(50);
```

## Configuring Date/Time Formats ##

Date/Time formats are configured in a set of internationalized properties files. For more information see [i18n](i18n.md).


## Single vs. Double Click ##

When a user clicks a timeblock in the `DayView` or day cell in the `MonthView`, it triggers a `TimeBlockClicked` event. You can configure if this event is triggered on Single vs. Double click:

```
settings.setTimeBlockClickNumber(Click.Double);
```

## Default Scroll Position ##

By default, the `DayView`'s scroll bar starts at 00:00. You can force it to automatically scroll to a specified hour (ie your calendar's working hours) using the scrollToHour setting:

```
calendar.scrollToHour(7);
```

## Show ISO Week Numbers ##
By default, the `DayView` doesn't show the ISO week numbers. In some countries it's quite common to work with the week numbers, and this setting allows to show them:

```
calendar.setShowWeekNumbers(true);
```