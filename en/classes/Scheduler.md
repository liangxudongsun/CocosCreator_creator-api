## `Scheduler` Class



Module: [cc](../modules/cc.md)




Scheduler is responsible of triggering the scheduled callbacks.<br/>
You should not use NSTimer. Instead use this class.<br/>
<br/>
There are 2 different types of callbacks (selectors):<br/>
    - update callback: the 'update' callback will be called every frame. You can customize the priority.<br/>
    - custom callback: A custom callback will be called every frame, or with a custom interval of time<br/>
<br/>
The 'custom selectors' should be avoided when possible. It is faster,
and consumes less memory to use the 'update callback'. *

### Index

##### Properties

  - [`PRIORITY_SYSTEM`](#prioritysystem) `Number` Priority level reserved for system services.
  - [`PRIORITY_NON_SYSTEM`](#prioritynonsystem) `Number` Minimum priority level for user scheduling.



##### Methods

  - [`setTimeScale`](#settimescale) Modifies the time of all scheduled callbacks.<br/>
You can use this property to create a 'slow motion' or 'fast forward' effect.<br/>
Default is 1.0. To create a 'slow motion' effect, use values below 1.0.<br/>
To create a 'fast forward' effect, use values higher than 1.0.<br/>
Note：It will affect EVERY scheduled selector / action.
  - [`getTimeScale`](#gettimescale) Returns time scale of scheduler.
  - [`update`](#update) 'update' the scheduler. (You should NEVER call this method, unless you know what you are doing.)
  - [`scheduleCallbackForTarget`](#schedulecallbackfortarget) <p>
  The scheduled method will be called every 'interval' seconds.</br>
  If paused is YES, then it won't be called until it is resumed.<br/>
  If 'interval' is 0, it will be called every frame, but if so, it recommended to use 'scheduleUpdateForTarget:' instead.<br/>
  If the callback function is already scheduled, then only the interval parameter will be updated without re-scheduling it again.<br/>
  repeat let the action be repeated repeat + 1 times, use cc.macro.REPEAT_FOREVER to let the action run continuously<br/>
  delay is the amount of time the action will wait before it'll start<br/>
</p>
  - [`schedule`](#schedule) The schedule
  - [`scheduleUpdate`](#scheduleupdate) Schedules the update callback for a given target,
the callback will be invoked every frame after schedule started.
  - [`unschedule`](#unschedule) Unschedules a callback for a callback and a given target.
If you want to unschedule the "update", use `unscheduleUpdate()`
  - [`unscheduleUpdate`](#unscheduleupdate) Unschedules the update callback for a given target.
  - [`unscheduleAllForTarget`](#unscheduleallfortarget) Unschedules all scheduled callbacks for a given target.
This also includes the "update" callback.
  - [`unscheduleAll`](#unscheduleall) Unschedules all scheduled callbacks from all targets including the system callbacks.<br/>
You should NEVER call this method, unless you know what you are doing.
  - [`unscheduleAllWithMinPriority`](#unscheduleallwithminpriority) Unschedules all callbacks from all targets with a minimum priority.<br/>
You should only call this with `PRIORITY_NON_SYSTEM_MIN` or higher.
  - [`isScheduled`](#isscheduled) Checks whether a callback for a given target is scheduled.
  - [`pauseAllTargets`](#pausealltargets) Pause all selectors from all targets.<br/>
You should NEVER call this method, unless you know what you are doing.
  - [`pauseAllTargetsWithMinPriority`](#pausealltargetswithminpriority) Pause all selectors from all targets with a minimum priority. <br/>
You should only call this with kCCPriorityNonSystemMin or higher.
  - [`resumeTargets`](#resumetargets) Resume selectors on a set of targets.<br/>
This can be useful for undoing a call to pauseAllCallbacks.
  - [`pauseTarget`](#pausetarget) Pauses the target.<br/>
All scheduled selectors/update for a given target won't be 'ticked' until the target is resumed.<br/>
If the target is not present, nothing happens.
  - [`resumeTarget`](#resumetarget) Resumes the target.<br/>
The 'target' will be unpaused, so all schedule selectors/update will be 'ticked' again.<br/>
If the target is not present, nothing happens.
  - [`isTargetPaused`](#istargetpaused) Returns whether or not the target is paused.
  - [`scheduleUpdateForTarget`](#scheduleupdatefortarget) Schedules the 'update' callback_fn for a given target with a given priority.<br/>
The 'update' callback_fn will be called every frame.<br/>
The lower the priority, the earlier it is called.
  - [`unscheduleCallbackForTarget`](#unschedulecallbackfortarget) Unschedule a callback function for a given target.<br/>
If you want to unschedule the "update", use unscheduleUpdateForTarget.
  - [`unscheduleUpdateForTarget`](#unscheduleupdatefortarget) Unschedules the update callback function for a given target.
  - [`unscheduleAllCallbacksForTarget`](#unscheduleallcallbacksfortarget) Unschedules all function callbacks for a given target.<br/>
This also includes the "update" callback function.
  - [`unscheduleAllCallbacks`](#unscheduleallcallbacks) Unschedules all function callbacks from all targets. <br/>
You should NEVER call this method, unless you know what you are doing.
  - [`unscheduleAllCallbacksWithMinPriority`](#unscheduleallcallbackswithminpriority) Unschedules all function callbacks from all targets with a minimum priority.<br/>
You should only call this with kCCPriorityNonSystemMin or higher.



### Details


#### Properties


##### PRIORITY_SYSTEM

> Priority level reserved for system services.

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:1128](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L1128) |



##### PRIORITY_NON_SYSTEM

> Minimum priority level for user scheduling.

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:1137](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L1137) |






<!-- Method Block -->
#### Methods


##### setTimeScale

Modifies the time of all scheduled callbacks.<br/>
You can use this property to create a 'slow motion' or 'fast forward' effect.<br/>
Default is 1.0. To create a 'slow motion' effect, use values below 1.0.<br/>
To create a 'fast forward' effect, use values higher than 1.0.<br/>
Note：It will affect EVERY scheduled selector / action.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:358](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L358) |

###### Parameters
- timeScale <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 


##### getTimeScale

Returns time scale of scheduler.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:378](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L378) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 



##### update

'update' the scheduler. (You should NEVER call this method, unless you know what you are doing.)

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:388](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L388) |

###### Parameters
- dt <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> delta time


##### scheduleCallbackForTarget

<p>
  The scheduled method will be called every 'interval' seconds.</br>
  If paused is YES, then it won't be called until it is resumed.<br/>
  If 'interval' is 0, it will be called every frame, but if so, it recommended to use 'scheduleUpdateForTarget:' instead.<br/>
  If the callback function is already scheduled, then only the interval parameter will be updated without re-scheduling it again.<br/>
  repeat let the action be repeated repeat + 1 times, use cc.macro.REPEAT_FOREVER to let the action run continuously<br/>
  delay is the amount of time the action will wait before it'll start<br/>
</p>

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:478](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L478) |
| Deprecated | since v3.4 please use .schedule |

###### Parameters
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 
- callback_fn <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> 
- interval <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 
- repeat <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 
- delay <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 
- paused <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 

##### Example

```js
//register a schedule to scheduler
var scheduler = cc.director.getScheduler();
scheduler.scheduleCallbackForTarget(this, function, interval, repeat, delay, !this._isRunning);

```

##### schedule

The schedule

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:516](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L516) |

###### Parameters
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> 
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 
- interval <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 
- repeat <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 
- delay <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 
- paused <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 

##### Example

```js
//register a schedule to scheduler
cc.director.getScheduler().schedule(callback, this, interval, !this._isRunning);

```

##### scheduleUpdate

Schedules the update callback for a given target,
the callback will be invoked every frame after schedule started.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:580](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L580) |

###### Parameters
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 
- priority <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 
- paused <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 
- updateFunc <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> 


##### unschedule

Unschedules a callback for a callback and a given target.
If you want to unschedule the "update", use `unscheduleUpdate()`

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:634](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L634) |

###### Parameters
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> The callback to be unscheduled
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> The target bound to the callback.


##### unscheduleUpdate

Unschedules the update callback for a given target.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:683](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L683) |

###### Parameters
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> The target to be unscheduled.


##### unscheduleAllForTarget

Unschedules all scheduled callbacks for a given target.
This also includes the "update" callback.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:705](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L705) |

###### Parameters
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> The target to be unscheduled.


##### unscheduleAll

Unschedules all scheduled callbacks from all targets including the system callbacks.<br/>
You should NEVER call this method, unless you know what you are doing.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:745](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L745) |



##### unscheduleAllWithMinPriority

Unschedules all callbacks from all targets with a minimum priority.<br/>
You should only call this with `PRIORITY_NON_SYSTEM_MIN` or higher.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:758](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L758) |

###### Parameters
- minPriority <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> The minimum priority of selector to be unscheduled. Which means, all selectors which
       priority is higher than minPriority will be unscheduled.


##### isScheduled

Checks whether a callback for a given target is scheduled.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:812](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L812) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 

###### Parameters
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> The callback to check.
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> The target of the callback.


##### pauseAllTargets

Pause all selectors from all targets.<br/>
You should NEVER call this method, unless you know what you are doing.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:850](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L850) |



##### pauseAllTargetsWithMinPriority

Pause all selectors from all targets with a minimum priority. <br/>
You should only call this with kCCPriorityNonSystemMin or higher.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:863](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L863) |

###### Parameters
- minPriority <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 


##### resumeTargets

Resume selectors on a set of targets.<br/>
This can be useful for undoing a call to pauseAllCallbacks.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:923](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L923) |

###### Parameters
- targetsToResume <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array" class="crosslink external" target="_blank">Array</a> 


##### pauseTarget

Pauses the target.<br/>
All scheduled selectors/update for a given target won't be 'ticked' until the target is resumed.<br/>
If the target is not present, nothing happens.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:942](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L942) |

###### Parameters
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 


##### resumeTarget

Resumes the target.<br/>
The 'target' will be unpaused, so all schedule selectors/update will be 'ticked' again.<br/>
If the target is not present, nothing happens.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:973](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L973) |

###### Parameters
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 


##### isTargetPaused

Returns whether or not the target is paused.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:1006](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L1006) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 

###### Parameters
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 


##### scheduleUpdateForTarget

Schedules the 'update' callback_fn for a given target with a given priority.<br/>
The 'update' callback_fn will be called every frame.<br/>
The lower the priority, the earlier it is called.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:1030](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L1030) |
| Deprecated | since v3.4 please use .scheduleUpdate |

###### Parameters
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 
- priority <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 
- paused <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 

##### Example

```js
//register this object to scheduler
var scheduler = cc.director.getScheduler();
scheduler.scheduleUpdateForTarget(this, priority, !this._isRunning );

```

##### unscheduleCallbackForTarget

Unschedule a callback function for a given target.<br/>
If you want to unschedule the "update", use unscheduleUpdateForTarget.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:1051](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L1051) |
| Deprecated | since v3.4 please use .unschedule |

###### Parameters
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> callback[Function] or key[String]

##### Example

```js
//unschedule a callback of target
var scheduler = cc.director.getScheduler();
scheduler.unscheduleCallbackForTarget(this, callback);

```

##### unscheduleUpdateForTarget

Unschedules the update callback function for a given target.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:1069](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L1069) |
| Deprecated | since v3.4 please use .unschedule |

###### Parameters
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 

##### Example

```js
//unschedules the "update" method.
var scheduler = cc.director.getScheduler();
scheduler.unscheduleUpdateForTarget(this);

```

##### unscheduleAllCallbacksForTarget

Unschedules all function callbacks for a given target.<br/>
This also includes the "update" callback function.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:1082](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L1082) |
| Deprecated | since v3.4 please use unscheduleAllForTarget |

###### Parameters
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 


##### unscheduleAllCallbacks

Unschedules all function callbacks from all targets. <br/>
You should NEVER call this method, unless you know what you are doing.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:1096](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L1096) |
| Deprecated | since v3.4 please use .unscheduleAllWithMinPriority |



##### unscheduleAllCallbacksWithMinPriority

Unschedules all function callbacks from all targets with a minimum priority.<br/>
You should only call this with kCCPriorityNonSystemMin or higher.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js:1111](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/CCScheduler.js#L1111) |
| Deprecated | since v3.4 please use .unscheduleAllWithMinPriority |

###### Parameters
- minPriority <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 


