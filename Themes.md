# Applying Themes #

The gwt-library includes a set of themes to style the calendar widget. The desired theme must be inherited in the `<your application>.gwt.xml` module file.

```
  <!-- inherit this module for a Google look and feel -->
  <inherits name='com.bradrydzewski.gwt.calendar.theme.google.Google' />

  <!-- inherit this module for an Outlook look and feel -->
  <inherits name='com.bradrydzewski.gwt.calendar.theme.outlook.Outlook' />

  <!-- inherit this module for an iCal look and feel -->
  <inherits name='com.bradrydzewski.gwt.calendar.theme.ical.iCal' />
```

To achieve a more authentic iCal look and feel you should also set the following property in the `CalendarSetting` class.
```
settings.setOffsetHourLabels(true);
calendar.setSettings(settings);
```

**Preview examples of each theme:**
  * [Google theme](http://google.latest.gwt-web-calendar.appspot.com/)
  * [iCal theme](http://ical.latest.gwt-web-calendar.appspot.com/)
  * [Outlook theme](http://outlook.latest.gwt-web-calendar.appspot.com/) `**`

`**`Outlook 2000 theme is no longer supported and will be removed in a future release.