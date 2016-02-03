Version **0.9** of **gwt-cal** is a major release that required some big changes to it's underlying structure in order to accommodate the following features:
  1. Displaying appointments in multiple views (i.e. `DayView` and `MonthView`) and seamlessly switch between them
  1. Allowing a developer to create their own custom `CalendarView`
  1. Displaying an appointment as multiple panels on the screen. This was required for the `MonthView`, where an appointment can span the 1st week and 2nd week of the month. This means an appointment must be displayed as two panels. Previously there was a one-to-one relationship between an appointment and a panel. Now this is a one-to-many relationship.

We also laid the ground work for **Drag and Drop** support, one of the most requested features. Right now Drag and Drop is supported in the `MonthView`, with plans to support the `DayView` in the 0.9.1 release.

**[Download version 0.9 beta2 now](http://code.google.com/p/gwt-cal/downloads/detail?name=gwt-cal-0.9.0-beta2.jar)**

# 0.9.0 Beta Summary #

  * Added support for multiple views (`MonthView`, `DayView`, etc)
    * `Calendar` facade class to easily switch between views
    * Ability to create and set custom views

  * `MonthView` includes `DragDrop` support using gwt-dnd
    * Added new `UpdateEvent` to notify when an appointment is dragged and updated
    * Ability to 'undo' the update

  * Appointment class is now a plain java object. No longer extends a gwt Widget
  * Appointments in the `DayView` can now display custom HTML in the description and header area
  * Multi-day is now calculated, as opposed to setting `Appointment.setMultiDay(true)`
  * Added unit tests to a number of classes (finally)
  * Upgraded project to use gwt 1.7
  * Added improved i18n including EN, ES, IT, FR, and NO
  * Appointment style improvements
    * Used inline styles for color themes to simplify css files
    * Fixed style inconsistencies in IE7/IE8

In addition, over 30 bugs and enhancements were closed out