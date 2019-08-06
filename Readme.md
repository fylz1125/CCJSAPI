Cocos2dx-3.15 JS API

使用Cocos2dx-3.15.1 JS 开发小游戏的一些技术笔记

## 使用图集

图集就是合图，可以使用 **TexturePacker**制作，制作好之后是一个 png 大图和对应的 `plist` 描述文件。

### 加载 `plist` 文件到 `spriteFrameCache`，将图集缓存

```js
var spriteFrameCache = cc.spriteFrameCache;
// 加载 plist文件
spriteFrameCache.addSpriteFrames(res.s_heros_plist);
// 或者同时加载plist和大图png spriteFrameCache.addSpriteFrames(res.s_heros_plist,res.s_heros_png);
// 用小图名称取小图
var frame = spriteFrameCache.getSpriteFrame("216.png");
this.sprite = new cc.Sprite(frame);
```


## 使用自定义TTF字体

- 在 `resource.js` 文件中声明字体路径
- 使用字体文件名称加载

```js
// 字体资源
var g_fonts = [
    {
        type:"font",
        name:"FZYHJW",
        srcs:["res/fonts/FZYHJW.ttf"]
    },
];
```
```js
// 使用字体
var label = new cc.LabelTTF("全民水浒 林冲传", "FZYHJW", 80);
```

## 弹出层屏蔽触摸点击事件
添加一个事件，吞噬调触摸事件即可
```js
// 防止点击事件穿透
cc.eventManager.addListener({
    event: cc.EventListener.TOUCH_ONE_BY_ONE,
    swallowTouches: true,//吞噬
    onTouchBegan:function(){
        return true;// 返回true表示处理掉了事件
    }
}, this);
```

## 按钮采用自定义 `size`
**Button** 默认使用精灵大小，并且使用 `setContentSize()` 进行设置没有卵用，需要忽略精灵大小，才能使用自定义尺寸

```js
// 按钮
var trainBt = new ccui.Button(res.s_ui_training);
// false，使用自定义size
trainBt.ignoreContentAdaptWithSize(false);
trainBt.setContentSize(cc.size(400,80));
```