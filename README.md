## Simple event handler
- Event handler that allows you to add listeners and fire events in simple manner. 
- You can register as many functions to one event as you want.
- Any given event can be suspended from firing and also can be reactivate. 
- Also you can remove any given event no matter if it's suspended or active. 
- This library is environment agnostic so it can be used in nodeJS and browser environment.

### Developed with:
- Vanilla js
- Common js

<br/>

### How to install:
```bash
npm install mayuska/event-handler
```

### How to use it:
```javascript
var eventHandler = require('event-handler');
var event = new eventHandler();


    /**
     * @param {string|array} eventName
     * @param {function} callback
     */
event.on(eventName, callback);  // create event

 /**
     * @param {string|array} eventName
     * @param {object|array|string|int|float} data
     */
event.fire(eventName, data); // dispatch event
```

<br/>

### Methods:

Method | Description 
--- | ---  
**.on**(eventName, callback)    | Creates and adds events. Adds callback to event, you can provide multiple event names as array of strings. It returns events object.
**.fire**(eventName, data)		|Runs all registered callbacks for provided eventName if that event name is not suspended. Every callback will get data as parameters. It returns events object.
**.suspend**(eventName)         | Suspends event from being fired. Returns true for successful suspend, false otherwise.
**.unsuspend**(eventName)       | Unsuspend previously suspended event. Returns true on success, false otherwise.
**.remove**(eventName)          | Removes previously added event, no matter if it's suspended or not. Returns true on success, false otherwise.
**.isActive**(eventName)        | Checks is event exists and is active event. Returns true on success, false otherwise.
**.isSuspended**(eventName)     | Checks if event is suspended event. Returns true on success, false otherwise.
**.isRegistered**(eventName)    | Checks if event exists, no matter if it's active or suspended. Returns true on success, false otherwise.


 <br/>

### Examples:

```javascript
//import event-handler
var eventHandler = require('event-handler');
var event = new eventHandler();
```

Create event:
```javascript
event.on('test', function(){
    console.log('event test is added to active events');
});

event.fire('test');
console.log('(created) isActive: ', event.isActive('test'));
```

Suspend event:
```javascript
event.suspend('test');
event.fire('test');

console.log('(suspended) isActive ', event.isActive('test'));
console.log('(suspended) isSuspended ', event.isSuspended('test'));
console.log('(suspended) isRegistered ', event.isRegistered('test'));
```

Unsuspend event:
```javascript
event.unsuspend('test');
event.fire('test');

console.log('(unSuspended) isSuspended ', event.isSuspended('test'));
console.log('(unSuspended) isActive ', event.isActive('test'));
```

Remove event:
```javascript
event.remove('test');
event.fire('test');
console.log('(removed) isActive ', event.isActive('test'));
console.log('(removed) isSuspended ', event.isSuspended('test'));
console.log('(removed) isRegistered ', event.isRegistered('test'));
```

firing multiple events at the same time



