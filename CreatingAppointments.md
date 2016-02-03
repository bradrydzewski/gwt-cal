# Create an Appointment #

The following code snippet demonstrates how to create and add an appointment to the calendar widget. Every time an appointment is added to the calendar widget the layout is re-calculated and performed.

```
Appointment appt = new Appointment();
appt.setStart(...);
appt.setEnd(...);
appt.setTitle(...);
appt.setStyle(AppointmentStyle.RED);
calendar.addAppointment(appt);
```

## appointments in batch ##

As stated earlier, every time an appointment is added to the calendar widget the layout is re-calculated. If you plan to add many appointments at once you should suspend the layout and then resume it once you are complete:

```
calendar.suspendLayout();

//load 1,000 appointments into calendar
for(int i=0;i<1000;i++) {
	Appointment appt = new Appointment();
	...
	calendar.addAppointment(appt);
}

calendar.resumeLayout();
```

Or you can add an entire list of appointments with a single method call:
```
List<Appointment> appointmentList ...
calendar.suspendLayout();
calendar.addAppointments(appointmentList);
calendar.resumeLayout();
```

## appointment style ##

When adding appointments you provide it with a style that defines its color palette. Use the `setStyle` method to set the `AppointmentStyle`. Options are: `AppointmentStyle.GREEN`, `AppointmentStyle.BLUE`

You can also add a custom style with the following code
```
appt.setStyle(AppointmentStyle.CUSTOM);
appt.setCustomStyle("my-custom-style");
```

Note: this functionality is not hooked up yet, but it will override the default gwt-cal styles and you will have to create your own. It is a huge pain to define your appointment styles in css, so consider yourself forewarned.