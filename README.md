This is a simple event system. Ready to use from the start.

To use it, just add using wizards.eventSystem at the top of code.

If you don't need send data with event - in case you only need to know that event was fired:
1. Add necessary event type into EventsWithoutData's enum EventTypes. 
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
```EventsWithoutData.Sub(EventsWithoutData.EventTypes.myEventWithoutData, eventName);```
4. When you need to call eventName method, just call ```EventsWithoutData.FireEvent(EventsWithoutData.EventTypes.myEventWithoutData);```