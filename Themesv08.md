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

**Preview examples of each theme:**
  * [Google theme](http://google.latest.gwt-web-calendar.appspot.com/)
  * [Outlook theme](http://outlook.latest.gwt-web-calendar.appspot.com/)
  * [iCal theme](http://ical.latest.gwt-web-calendar.appspot.com/)

### iCal Hour Labels ###

To achieve a more authentic iCal style we also need to change how the Hour labels are displayed. Google Calendar and Outlook hour labels are centered in-between major hour intervals as demonstrated below:
<pre>
---------<br>
|<br>
1am |<br>
|<br>
---------<br>
|<br>
2am |<br>
|<br>
---------<br>
</pre>

iCal hour labels, however, are aligned on the same x-axis as major hour intervals:
<pre>
1am -----<br>
|<br>
|<br>
|<br>
2am -----<br>
</pre>

By default, all labels are centered between major hour intervals. To change this default behavior we need to create a `CalendarSettings` object and set the hour labels offset to true.
```
CalendarSettings settings = new CalendarSettings();
settings.setOffsetHourLabels(true);
```
The `CalendarSettings` can be provided to the `DayView` either through the constructor or a setter. The hour labels will then align to the major hour interval's x-axis.