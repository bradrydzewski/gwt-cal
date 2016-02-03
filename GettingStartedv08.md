# Setup #

  1. Add the gwt-cal jar file to your project's build path. Right-click on the project node in the Package Explorer and select 'Build Path > Add External Archives...'. Specify the downloaded `gwt-cal-<version>.jar`
  1. Modify `<Your Application>.gwt.xml` to inherit the gwt-cal module and theme:

```
  <inherits name='com.bradrydzewski.gwt.calendar.Calendar' />
  <inherits name='com.bradrydzewski.gwt.calendar.theme.google.Google' />
```


# Simple Example #

Adding the calendar widget to a `Panel` just like any standard gwt widget.
```
DayView dayView = new DayView();
dayView.setDate(new Date()); //calendar date, not required
dayView.setDays(3); //number of days displayed at a time, not required
dayView.setWidth("500px");
dayView.setHeight("400px");
add(dayView);
```

You can then hook up an event listener to capture when an appointment is selected:
```
dayView.addValueChangeHandler(new ValueChangeHandler<Appointment>(){
	@Override
	public void onValueChange(ValueChangeEvent<Appointment> event) {
		// TODO Auto-generated method stub			
	}		
});
```

# Adding Appointment #

The following code snippet demonstrates how to create and add an appointment to the calendar widget. Every time an appointment is added to the calendar widget the layout is re-calculated and performed.

```
Appointment appt = new Appointment();
appt.setStart(...);
appt.setEnd(...);
appt.setTitle(...);
appt.addStyleName("gwt-appointment-blue");
dayView.addAppointment(appt);
```

## appointment style ##

When adding appointments you provide it with a style that defines its color palette. Use the `addStyleName` method. Examples are: `gwt-appointment-blue`, `gwt-appointment-green`

**Update**: Support for all Google Calendar colors As of build [r58](https://code.google.com/p/gwt-cal/source/detail?r=58) (thanks to [SpaceRoosters](http://code.google.com/u/SpaceRoosters/))<br />
Support for all iCal colors as of build [r68](https://code.google.com/p/gwt-cal/source/detail?r=68) (thanks to me)

Here is a table of appointment styles and the themes that support them:
| Style Name                  | Google Calendar | iCal |
|:----------------------------|:----------------|:-----|
| gwt-appointment-red         | X               | X    |
| gwt-appointment-green       | X               | X    |
| gwt-appointment-blue        | X               | X    |
| gwt-appointment-pink        | X               | -    |
| gwt-appointment-purple      | X               | X    |
| gwt-appointment-fushia      | -               | X    |
| gwt-appointment-darkpurple  | X               | X    |
| gwt-appointment-steelblue   | X               | -    |
| gwt-appointment-lightblue   | X               | -    |
| gwt-appointment-teal        | X               | -    |
| gwt-appointment-lightgreen  | X               | -    |
| gwt-appointment-yellowgreen | X               | -    |
| gwt-appointment-yellow      | X               | -    |
| gwt-appointment-orange      | X               | X    |
| gwt-appointment-redorange   | X               | -    |
| gwt-appointment-lightbrown  | X               | -    |
| gwt-appointment-lightpurple | X               | -    |
| gwt-appointment-grey        | X               | -    |
| gwt-appointment-bluegrey    | X               | -    |
| gwt-appointment-lightteal   | X               | -    |
| gwt-appointment-yellowgrey  | X               | -    |
| gwt-appointment-brown       | X               | -    |

## appointments in batch ##

As stated earlier, every time an appointment is added to the calendar widget the layout is re-calculated. If you plan to add many appointments at once you should suspend the layout and then resume it once you are complete:

```
dayView.suspendLayout();

//load 1,000 appointments into calendar
for(int i=0;i<1000;i++) {
	Appointment appt = new Appointment();
	...
	dayView.addAppointment(appt);
}

dayView.resumeLayout();
```

# Layout #

As discussed, layout is calculated when an appointment is added, or when `resumeLayout` is invoked. Layout is also calculated when `setDays` and `setDate` are added.

There is no need to recalculate layout when the width or height of the calendar changes. The items use %'s to position the appointments on the screen. That being said, you should never set the calendar's height to a % - only use a fixed pixel value. Feel free to set calendar width to a % or fixed pixel value.

# Questions?? #
Please post all questions to the gwt-cal group, [here](http://groups.google.com/group/gwt-cal). Any bugs can be logged on the issue tab.