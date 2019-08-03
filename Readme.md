Cocos2dx-3.15 JS API

使用Cocos2dx-3.15.1 JS 开发小游戏的一些技术笔记

## 使用图集

图集就是合图，可以使用 **TexturePacker**制作，制作好之后是一个 png 大图和对应的 `plist` 描述文件。

### 加载 `plist` 文件到 `spriteFrameCache`，将图集缓存

```js
var spriteFrameCache = cc.spriteFrameCache;
// 加载 plist文件
spriteFrameCache.addSpriteFrames(res.s_heros_plist);
// 或者同时加载plist和大图png
// spriteFrameCache.addSpriteFrames(res.s_heros_plist,res.s_heros_png);

// 用小图名称取小图
var frame = spriteFrameCache.getSpriteFrame("216.png");
this.sprite = new cc.Sprite(frame);
```
