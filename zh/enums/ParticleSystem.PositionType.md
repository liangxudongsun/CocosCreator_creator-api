### `ParticleSystem.PositionType` Enum



Module: [cc](../modules/cc.md)




粒子位置类型

### Index

##### Properties

  - `FREE`
  - `RELATIVE`
  - `GROUPED`

### Details

#### Properties


##### FREE

> 自由模式，相对于世界坐标，不会随粒子节点移动而移动。（可产生火焰、蒸汽等效果）

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/particle/CCParticleSystem.js:64](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/particle/CCParticleSystem.js#L64) |



##### RELATIVE

> 相对模式，粒子会随父节点移动而移动，可用于制作移动角色身上的特效等等。（该选项在 Creator 中暂时不支持）

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/particle/CCParticleSystem.js:73](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/particle/CCParticleSystem.js#L73) |



##### GROUPED

> 整组模式，粒子跟随发射器移动。（不会发生拖尾）

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/particle/CCParticleSystem.js:83](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/particle/CCParticleSystem.js#L83) |

