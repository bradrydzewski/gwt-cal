# Setup #

  1. Add the gwt-cal jar file to your project's build path. Right-click on the project node in the Package Explorer and select 'Build Path > Add External Archives...'. Specify the downloaded `gwt-cal-<version>.jar`
  1. Modify `<Your Application>.gwt.xml` to inherit the gwt-cal module and theme:

```
  <inherits name='com.bradrydzewski.gwt.calendar.Calendar' />
  <inherits name='com.bradrydzewski.gwt.calendar.theme.google.Google' />
```

You will also need to download and add gwt-dnd (Drag Drop library). We used version 3.0.0, but it may also work with newer versions.
```
  <inherits name='com.allen_sauer.gwt.dnd.gwt-dnd'/>
```


# Creating a Calendar #

Adding the calendar widget to a `Panel` just like any standard gwt widget.
```
Calendar calendar = new Calendar();
calendar.setDate(new Date()); //calendar date, not required
calendar.setDays(3); //number of days displayed at a time, not required
calendar.setWidth("500px");
calendar.setHeight("400px");
add(calendar);
```

# Changing Views #

gwt-cal version 0.9 now supports multiple view. You can switch

```
//Displays the Day View
calendar.setView(CalendarViews.DAY);
//Displays the Day View with 3 days
calendar.setView(CalendarViews.DAY, 3);

//Displays the month View
calendar.setView(CalendarViews.MONTH);
```

# Adding Appointments #

The following code snippet demonstrates how to create and add an appointment to the calendar widget. Every time an appointment is added to the calendar widget the layout is re-calculated and performed.

```
Appointment appt = new Appointment();
appt.setStart(...);
appt.setEnd(...);
appt.setTitle(...);
appt.setStyle(AppointmentStyle.BLUE);
calendar.addAppointment(appt);
```