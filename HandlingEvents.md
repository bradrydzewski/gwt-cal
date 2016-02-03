# Appointment Selection #

When an appointment is selected, either by click or by using the arrow keys, an Appointment `SelectionEvent` is fired.

Example Code:
```
calendar.addSelectionHandler(new SelectionHandler<Appointment>(){
  @Override
  public void onSelection(SelectionEvent<Appointment> event) {
    ...
  }		
});
```

# Appointment Opened #

When an appointment is double-clicked, it fires an appointment open event. Typically a developer would subscribe to this event to display some type of popup on the screen allowing the user to edit the opened appointment.

Example Code:
```
calendar.addOpenHandler(new OpenHandler<Appointment>(){
  @Override
  public void onOpen(OpenEvent<Appointment> event) {
     ...
  }
});
```

# Appointment Update (`DragDrop`) #

The user can update an appointment by `DragDrop`. When an appointment is moved (`onDrop`), it fires an UpdateEvent. You can subscribe to (and cancel) an appointment's update.

Example code:

```
calendar.addUpdateHandler(new UpdateHandler<Appointment>() {
  @Override
  public void onUpdate(UpdateEvent<Appointment> event) {
    boolean commit = Window.confirm(
                       "Are you sure you want to update the appointment \""
                        + event.getTarget().getTitle() + "\"");
    if (!commit) {
      event.setCancelled(true); //Cancel Appointment update
    }
  }
});
```

# Appointment Deletion #

The user can delete the selected appointment by pressing the delete key. When the delete key is pressed, it fires a `DeleteEvent`. You can subscribe to (and cancel) an appointment deletion.

Example code:
```
calendar.addDeleteHandler(new DeleteHandler<Appointment>(){
  @Override
  public void onDelete(DeleteEvent<Appointment> event) {
    boolean commit = Window.confirm("Are you sure you want to delete?");
    if(commit==false) {
      event.setCancelled(true);
    }
  }			
});
```

# Appointment Mouse Over #

The user can hover over an event with their mouse to trigger a MouseOverEvent. This event can be used to display tooltips, popups, etc.

Example Code:
```

   final DecoratedPopupPanel appointmentPopup = new DecoratedPopupPanel(true);
   appointmentPopup.setAutoHideEnabled(true);

   calendar.addMouseOverHandler(new MouseOverHandler<Appointment>(){
      @Override
      public void onMouseOver(MouseOverEvent<Appointment> event) {
        Element element = (Element)event.getElement();
        appointmentPopup.setWidget(new HTML(event.getTarget().getTitle()));

        int left = element.getAbsoluteLeft() + 10;
        int top = element.getAbsoluteTop() + 10;
        appointmentPopup.setPopupPosition(left, top);
        appointmentPopup.show();
      }
   });
```

# Time-Block Clicked #

A `TimeBlockClickEvent` is fired when an empty section of the body of the `DayView` is clicked. A Date is provide that corresponds to the date time (including hours and minutes, if applicable) that the user clicked. For example, if the user clicks the 8:30am time block, the event will get fired with the date and time equal to 8:30.

This also works with the `MonthView`. When a cell (i.e. day) in the `MonthView` is clicked the event is fired and provided the cell's date.

Typically a developer would subscribe to this event to prompt a user to create a new appointment with the user-selected start time.

Example Code:
```
calendar.addTimeBlockClickHandler(new TimeBlockClickHandler<Date>(){
  @Override
  public void onTimeBlockClick(TimeBlockClickEvent<Date> event) {
    ...
  }		
});
```

# Date Request Event #

A `DateRequestEvent` is fired when the View (i.e. `MonthView`) is requesting to change the date. For example, this event is called when a user clicks the "+n more" label on the `MonthView`. In a sense, the user is requesting to change the date (to a single day view for that date), and the view is publishing this request.

```
calendar.addDateRequestHandler(new DateRequestHandler<Date>(){
  @Override
  public void onDateRequested(DateRequestEvent<Date> event) {
    //in this example we change to the DayView for the given date
    calendar.setView(CalendarViews.DAY, 1);
    calendar.setDate(event.getTarget());
  }
});
```