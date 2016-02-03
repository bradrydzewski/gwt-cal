### Version 0.9.5 (in progress) ###
  * Tablet/Touch device support
  * Added scrollbar to multi day body
  * See the full list of enhancements and issues [here](http://code.google.com/p/gwt-cal/issues/list?can=1&q=label:Release0.9.5)

### Version 0.9.4 (January 14, 2013) ###

  * Available in public Maven repository
  * Added support for ISO Weeks
  * Added support to specify a list of Holidays
  * Added support to specify the day starting time.
  * Option to hide the multi day view section
  * Option to define if should show the NoonLabel or 12:00
  * Added multiple locales (Thanks to Dennis Foster)
  * Some API improvements
  * See the full list of enhancements and issues [here](http://code.google.com/p/gwt-cal/issues/list?can=1&q=label:Release0.9.4)

### Version 0.9.3 (January 7, 2012) ###

  * Updated project to use gwt 2.4.0
  * Updated project to use gwt-dnd 3.1.2
  * The whole project is now 100% mavenized
  * Added Swedish and Dutch locales
  * Added support to create an Appointment with Drag&Drop
  * See the full list of enhancements and issues [here](http://code.google.com/p/gwt-cal/issues/list?can=1&q=label:Release0.9.3)

### Version 0.9.2 (August 19) ###

  * Added a `MouseOver` event for Appointments
  * Updated project to use gwt 2.0.3
  * Updated project to use gwt-dnd 3.0.0
  * Implemented `RequiresResize` and `ProvidesResize` for compatibility with [LayoutPanels](http://code.google.com/webtoolkit/doc/latest/DevGuideUiPanels.html#LayoutPanels)
  * Added the Polish locale
  * Welcomed [Pierre Vittet](http://www.pvittet.com) as a contributor
  * See the full list of enhancements and issues [here](http://code.google.com/p/gwt-cal/issues/list?can=1&q=label:Release0.9.2)


### Version 0.9.1 (June 27) ###

  * Added drag drop & resize support in the `DayView` for single-day appointments
  * Fixed a layout bug in the `MonthView`, [Issue #60](http://code.google.com/p/gwt-cal/issues/detail?id=60)
  * Enabled HTML markup in the Appointment header, [Issue #48](http://code.google.com/p/gwt-cal/issues/detail?id=48)
  * Added an "id" field to the `Appointment` class
  * Added `HasAppointment` and `HasLayout` classes for use with MVP pattern
  * Added a reference to the clicked "+ n more" label in the `DateRequestEvent`. See [Issue #61](http://code.google.com/p/gwt-cal/issues/detail?id=61#c9)

### Version 0.9.0 (May 25) ###

  * Add support for multiple views, includes `MonthView`
  * Add drag drop support in the `MonthView`, including event handling and ability to cancel
  * Create `Calendar` facade class to easily switch between views
  * Support html in an `Appointment`'s description property
  * Improve `Calendar` and `Appointment` domain model. Remove all gwt dependencies from the `Appointment` class.
  * Unit tests to support the new Views and the new domain Model
  * A ton of small bug fixes and enhancements that I don't feel like typing up ... see the full list [here](http://code.google.com/p/gwt-cal/issues/list?can=1&q=label:Release0.9&colspec=ID+Type+Status+Priority+Reporter+Summary+Opened+Modified+Closed+Stars&cells=tiles)

### Version 0.8.2 (August 10, 2009) ###
  * Basic support for all/multi-day appointments`**`
  * Added full set of color schemes for iCal theme
  * Click time block to create new appointment, [Issue #9](http://code.google.com/p/gwt-cal/issues/detail?id=7)
  * Workaround for error when inserting `DayView` into `DockPanel`, [Issue #8](http://code.google.com/p/gwt-cal/issues/detail?id=8)

`**`This is just a preview of what's to come. There is quite a bit more work to do on all/multi-day appointments. Anders Lundgren has been kind enough to provide a patch for very flexible all/multi-day appointment rendering. We are working to integrate these changes with a number of structural changes required to enable multiple views (i.e. month view, list view) and drag drop functionality.

### Version 0.8.1 (July 21, 2009) ###
  * Delete key removes selected appointment
  * Deletion fires `DeleteEvent`, ability to cancel
  * Arrow keys change selected appointment
  * Appointment double-click fires `OpenEvent`
  * Added all Google colors to Google theme, [Issue #7](http://code.google.com/p/gwt-cal/issues/detail?id=7)
  * Fixed `DayView.scrollToHour()` scrolls too far, [Issue #1](http://code.google.com/p/gwt-cal/issues/detail?id=1)

### Version 0.8.0 (July 7, 2009) ###

_Moved from private repository to Google Code, released under GPLv3 License. Project features include:_
  * Day / multi-Day View
  * Configurable time intervals (15min,30min,1hr)
  * `HasValue` event fires when item selected
  * Add iCal, Google and Outlook themes
  * Fixed ie6 and ie7 opacity issues
  * Added drop shadow for ie6 and ie7