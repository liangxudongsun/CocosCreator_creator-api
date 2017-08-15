## `ActionManager` Class



Module: [cc](../modules/cc.md)




cc.ActionManager 是可以管理动作的单例类。<br/>
通常你并不需要直接使用这个类，99%的情况您将使用 CCNode 的接口。<br/>
但也有一些情况下，您可能需要使用这个类。 <br/>
例如：
 - 当你想要运行一个动作，但目标不是 CCNode 类型时。 <br/>
 - 当你想要暂停/恢复动作时。 <br/>

### Index



##### Methods

  - [`addAction`](#addaction) 增加一个动作，同时还需要提供动作的目标对象，目标对象是否暂停作为参数。<br/>
如果目标已存在，动作将会被直接添加到现有的节点中。<br/>
如果目标不存在，将为这一目标创建一个新的实例，并将动作添加进去。<br/>
当目标状态的 paused 为 true，动作将不会被执行
  - [`removeAllActions`](#removeallactions) 移除所有对象的所有动作。
  - [`removeAllActionsFromTarget`](#removeallactionsfromtarget) 移除指定对象上的所有动作。<br/>
属于该目标的所有的动作将被删除。
  - [`removeAction`](#removeaction) 移除指定的动作。
  - [`removeActionByTag`](#removeactionbytag) 删除指定对象下特定标签的一个动作，将删除首个匹配到的动作。
  - [`getActionByTag`](#getactionbytag) 通过目标对象和标签获取一个动作。
  - [`getNumberOfRunningActionsInTarget`](#getnumberofrunningactionsintarget) 返回指定对象下所有正在运行的动作数量。 <br/>
组合动作被算作一个动作。<br/>
例如：<br/>
 - 如果您正在运行 7 个动作组成的序列动作（Sequence），这个函数将返回 1。<br/>
 - 如果你正在运行 2 个序列动作（Sequence）和 5 个普通动作，这个函数将返回 7。<br/>
  - [`pauseTarget`](#pausetarget) 暂停指定对象：所有正在运行的动作和新添加的动作都将会暂停。
  - [`resumeTarget`](#resumetarget) 让指定目标恢复运行。在执行序列中所有被暂停的动作将重新恢复运行。
  - [`pauseAllRunningActions`](#pauseallrunningactions) 暂停所有正在运行的动作，返回一个包含了那些动作被暂停了的目标对象的列表。
  - [`resumeTargets`](#resumetargets) 让一组指定对象恢复运行（用来逆转 pauseAllRunningActions 效果的便捷函数）。
  - [`pauseTargets`](#pausetargets) 暂停一组指定对象。
  - [`purgeSharedManager`](#purgesharedmanager) 清除共用的动作管理器。它释放了持有的实例。 <br/>
因为它使用 this，因此它不能是静态的。
  - [`update`](#update) ActionManager 主循环。



### Details




<!-- Method Block -->
#### Methods


##### addAction

增加一个动作，同时还需要提供动作的目标对象，目标对象是否暂停作为参数。<br/>
如果目标已存在，动作将会被直接添加到现有的节点中。<br/>
如果目标不存在，将为这一目标创建一个新的实例，并将动作添加进去。<br/>
当目标状态的 paused 为 true，动作将不会被执行

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:101](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L101) |

###### Parameters
- action <a href="../classes/Action.html" class="crosslink">Action</a> 
- target <a href="../classes/Node.html" class="crosslink">Node</a> 
- paused <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 


##### removeAllActions

移除所有对象的所有动作。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:140](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L140) |



##### removeAllActionsFromTarget

移除指定对象上的所有动作。<br/>
属于该目标的所有的动作将被删除。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:153](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L153) |

###### Parameters
- target <a href="../classes/Node.html" class="crosslink">Node</a> 
- forceDelete <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 


##### removeAction

移除指定的动作。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:174](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L174) |

###### Parameters
- action <a href="../classes/Action.html" class="crosslink">Action</a> 


##### removeActionByTag

删除指定对象下特定标签的一个动作，将删除首个匹配到的动作。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:202](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L202) |

###### Parameters
- tag <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 
- target <a href="../classes/Node.html" class="crosslink">Node</a> 


##### getActionByTag

通过目标对象和标签获取一个动作。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:229](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L229) |
| Return 		 | <a href="../classes/Action.html" class="crosslink">Action</a> &#124; Null 

###### Parameters
- tag <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 
- target <a href="../classes/Node.html" class="crosslink">Node</a> 


##### getNumberOfRunningActionsInTarget

返回指定对象下所有正在运行的动作数量。 <br/>
组合动作被算作一个动作。<br/>
例如：<br/>
 - 如果您正在运行 7 个动作组成的序列动作（Sequence），这个函数将返回 1。<br/>
 - 如果你正在运行 2 个序列动作（Sequence）和 5 个普通动作，这个函数将返回 7。<br/>

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:256](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L256) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 

###### Parameters
- target <a href="../classes/Node.html" class="crosslink">Node</a> 


##### pauseTarget

暂停指定对象：所有正在运行的动作和新添加的动作都将会暂停。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:281](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L281) |

###### Parameters
- target <a href="../classes/Node.html" class="crosslink">Node</a> 


##### resumeTarget

让指定目标恢复运行。在执行序列中所有被暂停的动作将重新恢复运行。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:292](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L292) |

###### Parameters
- target <a href="../classes/Node.html" class="crosslink">Node</a> 


##### pauseAllRunningActions

暂停所有正在运行的动作，返回一个包含了那些动作被暂停了的目标对象的列表。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:304](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L304) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array" class="crosslink external" target="_blank">Array</a> 



##### resumeTargets

让一组指定对象恢复运行（用来逆转 pauseAllRunningActions 效果的便捷函数）。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:323](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L323) |

###### Parameters
- targetsToResume <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array" class="crosslink external" target="_blank">Array</a> 


##### pauseTargets

暂停一组指定对象。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:339](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L339) |

###### Parameters
- targetsToPause <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array" class="crosslink external" target="_blank">Array</a> 


##### purgeSharedManager

清除共用的动作管理器。它释放了持有的实例。 <br/>
因为它使用 this，因此它不能是静态的。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:355](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L355) |



##### update

ActionManager 主循环。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js:402](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/actions/CCActionManager.js#L402) |

###### Parameters
- dt <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> delta time in seconds


