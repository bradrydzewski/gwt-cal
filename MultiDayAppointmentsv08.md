# Introduction #

Basic multi-day and all-day appointment support was added as of [r83](https://code.google.com/p/gwt-cal/source/detail?r=83). This mimics the Google Calendar approach, where all-day and multi-day appointments are placed in the "header" section of the calendar.


# Details #

For now, all day appointments must be specifically flagged as "all day", by setting an appointment's `setMultiDay` equal to `true`.

There are a few categories of multi-day and all-day appointments.

First, there are multi-day appointments, which span more than one single day:
```
Appointment appt1 = new Appointment();
appt1.setStart(new Date(new Date().getYear(),11,23,10,0));
appt1.setEnd(new Date(new Date().getYear(),11,24,13,30));
appt1.setTitle("Multi Day event");
appt1.setDescription("From Dec 23 10am to Dec 24 1:30pm");
appt1.addStyleName("gwt-appointment-green");
appt1.setMultiDay(true);
dayView.addAppointment(appt1);
```

Second, there are all-day appointments. these start at 0:00 and last just 24 hours. In these cases, you set the appointment as multi-day, set the start as 0:00 and the end as 23:59.
```
Appointment appt2 = new Appointment();
appt2.setStart(new Date(new Date().getYear(),11,25,0,0));
appt2.setEnd(new Date(new Date().getYear(),11,25,23,59));
appt2.setTitle("All Day");
appt2.setDescription("Dec 25 12am to Midnight (12am Dec 26)");
appt2.addStyleName("gwt-appointment-red");
appt2.setMultiDay(true);
dayView.addAppointment(appt2);
```


Third, there are all-day multi-day appointments. These start at 0:00 and end at 23:59 on a future date. These appointments span all day, many days.
```
Appointment appt3 = new Appointment();
appt3.setStart(new Date(new Date().getYear(),11,25,0,0));
appt3.setEnd(new Date(new Date().getYear(),11,26,23,59));
appt3.setTitle("All Day event");
appt3.setDescription("From Dec 25 to Dec 26");
appt3.addStyleName("gwt-appointment-blue");
appt3.setMultiDay(true);
dayView.addAppointment(appt3);
```

# What's next #

As you can see above, this implementation isn't exactly perfect ...
  * setMultiDay is not exactly descriptive, should maybe be changed to setAllDay
  * it is not desirable to have to set the end date to 23:59

Also, we'd like to explore alternate strategies for visualizing all-day and multi-day appointments. iCal and Microsoft take different approaches to all-day and multi-day appointments. For example, in iCal, multi-day appointments may be displayed in the body of the calendar as opposed to inside the header.

We are working to add this flexibility to gwt-cal in future releases.