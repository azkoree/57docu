---
sidebar_position: 5
---

# Events and Movement Core 

[Events and Movement Core VisuStella MZ - Yanfly.moe Wiki](http://www.yanfly.moe/wiki/Events_and_Movement_Core_VisuStella_MZ)



## 简介

Events & Movement Core 插件为 RPG Maker MZ 增添了许多新功能，显著提升了事件的灵活性和移动选项。这些功能涵盖了从 RPG Maker 早期版本中的旧功能到其他游戏引擎中更主流的技术。移动选项也得到了扩展，支持八方向移动以及使用 VisuStella 8 格式的精灵图。

功能包括（但不限于）以下内容：

- 扩展的事件命令，包含新旧函数。
- 用于复制事件、变形事件和生成事件的事件模板。
- 支持八方向移动和精灵图。
- 冲刺时精灵倾斜和添加阴影的视觉效果。
- 通过自定义移动路径命令实现事件移动的寻路功能。
- 高级开关和变量支持，可自动运行代码。
- 将普通开关和变量转换为独立开关和独立变量。
- 在事件上添加标签和图标。
- 允许通过多种方式触发事件，例如点击、接近或使用区域。
- 增大事件的碰撞箱大小（可任意方向）。
- 同步事件移动选项，使其随玩家或其他事件移动而移动。
- 允许玩家原地转身。



## 页面备注和事件注释标签是什么？

![image.png](https://img.57hmpg.top/file/1768623482714_image.png)



## 特点

### 高级开关和变量

![EventsMoveCoreAdvSwitchesVariables.png](http://www.yanfly.moe/wiki/images/thumb/d/de/EventsMoveCoreAdvSwitchesVariables.png/600px-EventsMoveCoreAdvSwitchesVariables.png)

开关和变量现在可以运行 JavaScript 代码并立即返回值。乍一看，这似乎与使用“控制变量”事件命令的“脚本”选项没有区别，但实际上，它可以用来立即设置并行公共事件、事件页面条件、敌方技能条件和敌群页面条件的开关和/或变量条件，而无需创建事件命令。

---

```

<JS> 代码 </JS>

- 用于：开关和变量名
- 将 'code' 替换为 JavaScript 代码，用于指定要返回的值。

```

---

注意：带标签的 Switch 开关/变量是互斥的。您不能同时使用` <JS>`、`<Self>` 或 `<Global>` 标签来标记它们。

### 独立开关和变量

[![EventsMoveCoreSelfSwitchesVariables.png](http://www.yanfly.moe/wiki/images/thumb/0/01/EventsMoveCoreSelfSwitchesVariables.png/600px-EventsMoveCoreSelfSwitchesVariables.png)](http://www.yanfly.moe/wiki/File:EventsMoveCoreSelfSwitchesVariables.png)

RPG Maker MZ 默认有 4 个独立开关：A、B、C、D。对于某些类型的游戏来说，这远远不够。此插件允许您将普通开关转换为独立开关，从而拥有更多开关。

RPG Maker MZ 默认也不支持独立变量。与开关一样，您可以将普通变量转换为独立变量。

---

```

<Self>

- 用于：开关和变量名称
- 将开关/变量转换为自身类型的开关/变量。

```

---

之后，只需像在事件页面条件中使用普通的开关和变量一样使用它们即可。如果开关或变量名称中包含 `<Self> `标签，则它将使用仅对该事件有效的数据。

注意：带标签的开关/变量彼此互斥。您不能同时使用·`<JS>`、`<Self>` 或 `<Global>` 标签。

---

如果您需要使用脚本调用来获取独立开关或独立变量的值，可以使用以下脚本调用。

```

获取独立开关值：
getSelfSwitchValue(mapID, eventID, switchID)
- 将 'mapID' 替换为目标事件所在的地图 ID。
- 将 'eventID' 替换为目标事件的 ID。
- 如果是独立开关，则将 'switchID' 替换为 ID 号（使用 <Self> 标记）；如果是 A、B、C 或 D，则替换为用引号括起来的大写字母。
- 这将返回自开关的 true/false 值。
- 示例：getSelfSwitchValue(12, 34, 56)
- 示例：getSelfSwitchValue(12, 34, 'B')

获取独立变量值：
getSelfVariableValue(mapID, eventID, variableID)
- 将 'mapID' 替换为目标事件所在的地图 ID。
- 将 'eventID' 替换为目标事件的 ID。
- 将 'variableID' 替换为自身变量的 ID。
- 这将返回自身变量中存储的任何值。
- 示例：getSelfVariableValue(12, 34, 56)

设置独立开关值：
setSelfSwitchValue(mapID, eventID, switchID, value)
- 将 'mapID' 替换为目标事件所在的地图 ID。
- 将 'eventID' 替换为目标事件的 ID。
- 如果是独立开关，请将“switchID”替换为 ID 号。
如果是 A、B、C 或 D，请用引号括起来的大写字母代替“switchID”。
- 将“value”分别替换为“true”或“false”以表示开启/关闭状态。
请勿使用引号。
- 这将把独立开关的值更改为 true/false。
- 例如：setSelfSwitchValue(12, 34, 56, false)
- 例如：setSelfSwitchValue(12, 34, 'B', true)

设置独立变量值：
setSelfVariableValue(mapID, eventID, variableID, value)
- 将“mapID”替换为目标事件所在的地图 ID。
- 将“eventID”替换为目标事件的 ID。
- 将“variableID”替换为独立变量的 ID 号。
- 将“value”替换为您想要设置的独立变量值。
- 例如：setSelfVariableValue(12, 34, 56, 88888)

```

---

### 地图开关和变量

[![EventsMovementCore MapSwitches.png](http://www.yanfly.moe/wiki/images/thumb/7/71/EventsMovementCore_MapSwitches.png/600px-EventsMovementCore_MapSwitches.png)](http://www.yanfly.moe/wiki/File:EventsMovementCore_MapSwitches.png)

与独立开关和独立变量类似，地图切换和地图变量是根据玩家当前所在地图保存数据的切换和变量。换句话说，它们是针对地图的独立开关和变量！

RPG Maker MZ 默认情况下不包含这些功能。与独立开关和独立变量类似，您可以使用以下名称标签将普通开关或变量转换为地图开关和地图变量：

---

```
<Map>
- 用于：开关和变量名称
- 将开关/变量转换为地图开关/变量。

```

---

之后，只需像在事件页面条件中使用普通开关和变量一样使用它们即可。如果开关或变量名称中包含 `<Map>` 标签，则它将使用仅该地图特有的数据。

注意：带标签的开关/变量彼此互斥。您不能同时使用 `<JS>`、`<Self>`、`<Map>` 或 `<Global>` 标签。

---

如果您需要使用脚本调用来获取地图开关或地图变量的值，可以使用以下脚本调用：

```

---

获取地图开关值：
getMapSwitchValue(mapID, switchID)
- 将“mapID”替换为开关所在的地图 ID。
- 将“switchID”替换为要获取数据的开关的 ID 号。
- 例如：getMapSwitchValue(4, 20)

---

获取变量开关值：
getMapVariableValue(mapID, variableID)
- 将“mapID”替换为开关所在的地图 ID。
- 将“variableID”替换为要获取数据的变量的 ID 号。
- 例如：getMapVariableValue(6, 9)

---

设置地图开关值：
setMapSwitchValue(mapID, switchID, value)
- 将“mapID”替换为开关所在的地图 ID。
- 将“switchID”替换为要获取数据的开关的 ID 号。
- 将“value”分别替换为“true”或“false”以表示开关状态（开/关）。
请勿使用引号。
- 例如：setMapSwitchValue(4, 20, true)
- 例如：setMapSwitchValue(6, 9, false)

---

设置地图变量值：
setMapVariableValue(mapID, variableID, value)
- 将“mapID”替换为开关所在的地图 ID。
- 将“variableID”替换为要获取数据的变量的 ID 号。
- 将“value”替换为要设置的地图变量值。
- 例如：setMapVariableValue(6, 9, 420)
  ---
```

---

### 角色精灵文件名标签

对于位于项目 /img/characters/ 文件夹中的文件，如果文件名本身包含特定的“标签”，则会应用特殊属性。这些标签可以组合使用，但也有一些例外。

其中一些是 VisuStella MZ 的新增功能，而另一些则是 MZ 的默认功能。

---

```

!filename.png
- 标签：!
- 使该角色的精灵与图块网格对齐，而不是向上移动几个像素。
- 这主要用于门、箱子和地板等元素。
- RPG Maker MZ 默认启用。

```

---

```

$filename.png
- 标签：$
- 使该角色的精灵使用“大字符”格式。
- 主要用于大型怪物等只有 3x4 单元格的精灵图，而不是常规精灵图的 12x8 单元格。
- 不能与 [VS8] 标签同时使用。
- 默认使用 RPG Maker MZ。

```

---

```

filename[Invisible].png
- 标签：[Invisible] 或 [Inv]
- 此角色的精灵图在游戏地图界面上将变为不可见，而其他几乎所有元素仍然可见。
- 此功能适用于希望使用精灵标签来表示诸如自动运行和并行事件等情况的用户。

```

---

```

filename[VS8].png
- 标签：[VS8]
- 将此精灵图转换为 VisuStella 风格的 8 方向精灵图。
- 请参阅以下部分。
- 不能与 $ 标签同时使用。

```

---

### VisuStella 风格的八向精灵图

[![EventsMoveCoreVS8.gif](http://www.yanfly.moe/wiki/images/4/40/EventsMoveCoreVS8.gif)](http://www.yanfly.moe/wiki/File:EventsMoveCoreVS8.gif)

此插件支持 VisuStella 风格的八向精灵图，也称为 VS8。VS8 精灵图支持行走帧、冲刺帧、搬运帧和表情动作。

---

要将精灵图指定为 VS8，只需在文件名后添加 [VS8].png。例如，Actor1.png 将变为 `Actor1_[VS8].png`。

---

VS8 精灵图的格式如下。以下每个块包含 3 帧。

```

Walk Down    Walk DL     Dash Down   Dash DL
Walk Left    Walk DR     Dash Left   Dash DR
Walk Right   Walk UL     Dash Right  Dash UL
Walk Up      Walk UR     Dash Up     Dash UR

Carry Down   Carry DL    Ladder      Emotes 3
Carry Left   Carry DR    Rope        Emotes 4
Carry Right  Carry UL    Emotes 1    Emotes 5
Carry Up     Carry UR    Emotes 2    Emotes 6

翻译出来乱七八糟的，还是放原文给你们自己看好了，实在看不懂也可以在范例工程找到示例

```

**注意：**跳跃时，大多数情况下会使用“搬运”帧，这是一个双臂举过头顶的精灵姿势，图标显示“搬运”状态。

---

以下是各个表情组的分组，从左到右。

```

表情 1：物品、哼、胜利
表情 2：受伤、跪下、倒地
表情 3：！、？、音符
表情 4：心形、愤怒、汗水
表情 5：蜘蛛网、……、灯泡
表情 6：睡眠0、睡眠1、睡眠2
```

---

### 加权随机移动

[![EventsMovementCore Update25 WeightedRandom.png](http://www.yanfly.moe/wiki/images/thumb/c/c1/EventsMovementCore_Update25_WeightedRandom.png/600px-EventsMovementCore_Update25_WeightedRandom.png)](http://www.yanfly.moe/wiki/File:EventsMovementCore_Update25_WeightedRandom.png)

创建要放置在地图上的事件时，您可以确定事件的自主移动类型。选择“随机”后，事件将在地图上随机移动。

然而，由于 RPG Maker MZ 默认代码中“随机”移动的运作方式，事件更容易撞墙，然后沿着墙壁绕着地图边缘转圈，这对于在地图上停留足够长时间的玩家来说非常不自然。

这时就需要“加权随机移动”功能了。它改变了随机移动的行为，使得事件距离越远，就越有可能退回到它的“初始”位置（即加载地图时生成的位置）。这样可以避免一个家庭主妇 NPC 突然跑到同一张城镇地图上的军队训练场中央。

事件会根据权重值的大小更靠近它的初始位置。有很多方法可以调整权重值。

---

插件参数 > 移动 > 事件移动 > 随机移动权重

此插件参数设置允许您为所有具有“随机”自主移动的事件设置默认权重。默认值为 0.10，旨在赋予事件一定的自由度。

数值越小，事件的移动自由度越大。数值越大，事件的移动距离就越短。

将此值更改为 0 可禁用此功能。

---

您可以使用事件的注释标签，为每个事件单独自定义此设置。

```

<Random Move Weight: x>

- 用于：事件注释标签和事件页面注释标签
- 如果将此标签用于具有随机自主移动的事件，则事件将更靠近其初始位置（即在地图上生成时的位置）。事件靠近初始位置的程度取决于权重值“x”。
- 将“x”替换为 0 到 1 之间的数字。数字越接近 0，事件在随机移动时就越自由；数字越接近 1，事件就越倾向于停留在其初始位置附近。

<True Random Move>

- 用于：事件注释标签和事件页面注释标签
- 如果此标签用于具有随机类型自主移动的事件，则该事件将忽略加权随机移动的影响。

```

---

[回到顶部](/visustella/1-eventmove#top)

## 注释标签

### 地图注释标签

以下注释标签仅用于地图。虽然其中一些选项也可在插件参数中使用，但部分注释标签的用途也扩展到了标记这些注释标签的特定地图。



### 页面注释标签

以下评论标签必须添加到事件、敌群和公共事件的页面中才能生效！



### 事件和事件页面标签

以下注释标签有对应的事件注释标签（少数例外）。如果标签用于事件备注，它将持续影响该事件。如果使用注释，它只会影响该注释所在的页面。

[回到顶部](/visustella/0-eventmove#top)