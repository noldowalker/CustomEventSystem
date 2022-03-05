This is a simple event system. Ready to use from the start.

To use it, just add using wizards.eventSystem at the top of code.

If you don't need send data with event - in case you only need to know that event was fired:
1. Add necessary event type into any enum. 
```
public enum EventTypes
{
    myEventWithoutData
}
```
2. Create a method with signature like 
```void eventName()```
 in listening Actor.
3. Subscribe that event on event type that you need where you need. Start() of Monobehaviour is good plase:
```EventsWithoutData.Sub(EventTypes.myEventWithoutData, eventName);```
4. When you need to call eventName method, just call ```EventsWithoutData.FireEvent(EventTypes.myEventWithoutData);```

If you need send data with event - in case you need send some data with event. But using EventsWithData
class and declare a struct with EventDataTransferObject as ancestor.
1. Add necessary event type into any enum.
```
public enum EventTypes
{
    myEventWithData
}
```
2. Add DTO struct
```
public class EventWithString: EventDataTransferObject
{
    public string someText;
}
```
3. Create a method with signature like
```void eventName(EventWithString eventData)```
   in listening Actor.
4. Subscribe that event on event type that you need where you need. Start() of Monobehaviour is good plase:
```EventsWithoutData.Sub(EventTypes.myEventWithData, eventName);```
5. When you need to call eventName method, just call 
```
 var stringDto = new EventWithString()
        {
            someText = "hi",
        };
EventsWithData.FireEvent(EventTypes.myEventWithData, stringDto);
```
