## `PhysicsContact` Class



Module: [cc](../modules/cc.md)




物理接触会在开始和结束碰撞之间生成，并作为参数传入到碰撞回调函数中。
注意：传入的物理接触会被系统进行重用，所以不要在使用中缓存里面的任何信息。

### Index

##### Properties

  - [`colliderA`](#collidera) `Collider` 
  - [`colliderB`](#colliderb) `Collider` 
  - [`disabled`](#disabled) `Boolean` 如果 disabled 被设置为 true，那么直到接触结束此接触都将被忽略。
如果只是希望在当前时间步或子步中忽略此接触，请使用 disabledOnce 。
  - [`disabledOnce`](#disabledonce) `Boolean` 在当前时间步或子步中忽略此接触。



##### Methods

  - [`getWorldManifold`](#getworldmanifold) 获取世界坐标系下的碰撞信息。
  - [`getManifold`](#getmanifold) 获取世界坐标系下的碰撞信息。
  - [`getImpulse`](#getimpulse) 获取冲量信息
注意：这个信息只有在 onPostSolve 回调中才能获取到
  - [`isTouching`](#istouching) 返回碰撞体是否已经接触到。
  - [`setTangentSpeed`](#settangentspeed) 为传送带设置期望的切线速度
  - [`getTangentSpeed`](#gettangentspeed) 获取切线速度
  - [`setFriction`](#setfriction) 覆盖默认的摩擦力系数。你可以在 onPreSolve 回调中调用此函数。
  - [`getFriction`](#getfriction) 获取当前摩擦力系数
  - [`resetFriction`](#resetfriction) 重置摩擦力系数到默认值
  - [`setRestitution`](#setrestitution) 覆盖默认的恢复系数。你可以在 onPreSolve 回调中调用此函数。
  - [`getRestitution`](#getrestitution) 获取当前恢复系数
  - [`resetRestitution`](#resetrestitution) 重置恢复系数到默认值



### Details


#### Properties


##### colliderA

> 

| meta | description |
|------|-------------|
| Type | <a href="../classes/Collider.html" class="crosslink">Collider</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:453](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L453) |



##### colliderB

> 

| meta | description |
|------|-------------|
| Type | <a href="../classes/Collider.html" class="crosslink">Collider</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:456](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L456) |



##### disabled

> 如果 disabled 被设置为 true，那么直到接触结束此接触都将被忽略。
如果只是希望在当前时间步或子步中忽略此接触，请使用 disabledOnce 。

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:459](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L459) |



##### disabledOnce

> 在当前时间步或子步中忽略此接触。

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:468](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L468) |






<!-- Method Block -->
#### Methods


##### getWorldManifold

获取世界坐标系下的碰撞信息。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:213](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L213) |
| Return 		 | <a href="../classes/WorldManifold.html" class="crosslink">WorldManifold</a> 



##### getManifold

获取世界坐标系下的碰撞信息。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:273](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L273) |
| Return 		 | <a href="../classes/Manifold.html" class="crosslink">Manifold</a> 



##### getImpulse

获取冲量信息
注意：这个信息只有在 onPostSolve 回调中才能获取到

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:337](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L337) |
| Return 		 | <a href="../classes/PhysicsImpulse.html" class="crosslink">PhysicsImpulse</a> 



##### isTouching

返回碰撞体是否已经接触到。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:479](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L479) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 



##### setTangentSpeed

为传送带设置期望的切线速度

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:491](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L491) |

###### Parameters
- tangentSpeed <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 


##### getTangentSpeed

获取切线速度

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:502](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L502) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 



##### setFriction

覆盖默认的摩擦力系数。你可以在 onPreSolve 回调中调用此函数。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:515](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L515) |

###### Parameters
- friction <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 


##### getFriction

获取当前摩擦力系数

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:526](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L526) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 



##### resetFriction

重置摩擦力系数到默认值

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:537](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L537) |



##### setRestitution

覆盖默认的恢复系数。你可以在 onPreSolve 回调中调用此函数。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:547](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L547) |

###### Parameters
- restitution <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 


##### getRestitution

获取当前恢复系数

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:558](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L558) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 



##### resetRestitution

重置恢复系数到默认值

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js:569](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/physics/CCPhysicsContact.js#L569) |



