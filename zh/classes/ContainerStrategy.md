## `ContainerStrategy` Class



Module: [_decorator](../modules/_decorator.md)
Parent Module: [cc](../modules/cc.md)




<p>cc.ContainerStrategy class is the root strategy class of container's scale strategy,
it controls the behavior of how to scale the cc.container and cc.game.canvas object</p>

### Index



##### Methods

  - [`preApply`](#preapply) Manipulation before appling the strategy
  - [`apply`](#apply) Function to apply this strategy
  - [`postApply`](#postapply) Manipulation after applying the strategy



### Details




<!-- Method Block -->
#### Methods


##### preApply

Manipulation before appling the strategy

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCView.js:1021](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCView.js#L1021) |

###### Parameters
- view <a href="../classes/View.html" class="crosslink">View</a> The target view


##### apply

Function to apply this strategy

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCView.js:1029](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCView.js#L1029) |

###### Parameters
- view <a href="../classes/View.html" class="crosslink">View</a> 
- designedResolution <a href="../classes/Size.html" class="crosslink">Size</a> 


##### postApply

Manipulation after applying the strategy

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCView.js:1038](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCView.js#L1038) |

###### Parameters
- view <a href="../classes/View.html" class="crosslink">View</a> The target view


