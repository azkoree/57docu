---
sidebar_position: 6
---

# Items and Equips Core 


## 简介

“物品与装备核心”插件改进了 RPG Maker MZ 的物品和装备专用场景（包括商店）及其处理方式。通过增加物品类别、改进参数控制、规则设置等功能，游戏开发者可以更好地掌控游戏中物品的关键方面。

功能包括（但不限于）以下内容：
- 修改物品场景、装备场景和商店场景的外观。
- 将物品分类为单一类别或多个类别。
- 物品场景和商店场景现在会显示物品的详细信息。
- 新增！标记可以显示在游戏中最近获得的物品上方。
- 装备注释标签，可以调整超出编辑器限制的参数。
- 装备规则，可以调整哪些类型的装备可以卸下和/或优化。
- 装备类型处理，可以更好地控制装备配置。
- 可以根据开关隐藏/显示商店中出售的物品。
- 商店出售的商品价格可能因标签调整而有所不同。



## 主要变更：新增硬编码功能

此插件为 RPG Maker MZ 的功能添加了一些新的硬编码功能。以下是这些功能的列表。

---

### 装备类型处理

[![ItemsEquipsCoreEquipTypes.png](http://www.yanfly.moe/wiki/images/thumb/6/64/ItemsEquipsCoreEquipTypes.png/600px-ItemsEquipsCoreEquipTypes.png)](http://www.yanfly.moe/wiki/File:ItemsEquipsCoreEquipTypes.png)

角色将不再只有一个通用的装备栏位设置。职业可以拥有不同的装备类型配置，这可以通过使用注释标签来实现。此外，名称相同的装备类型将被视为同一类型，而之前它们会被视为不同类型的装备。这意味着，如果您有两个“饰品”栏位（无论是通过笔记标签还是通过“数据库”>“类型”选项卡），它们都可以装备相同类型的饰品。

“更换装备”事件命令现已更新，以反映这一新变化。处理装备更换时，更换的饰品将放置在第一个匹配类型的空栏位中。如果角色所有匹配的栏位类型都已装备，则新装备将替换最后一个可用栏位。

---

### 商店状态窗口

[![ItemsEquipsCoreShopStatus.png](http://www.yanfly.moe/wiki/images/thumb/5/50/ItemsEquipsCoreShopStatus.png/600px-ItemsEquipsCoreShopStatus.png)](http://www.yanfly.moe/wiki/File:ItemsEquipsCoreShopStatus.png)

商店场景中的状态窗口原本非常空洞，几乎不显示任何信息。此插件的新功能改变了这一现状。虽然可以通过插件参数自定义商店状态窗口的内容，但此更改不可逆，而且效果显著，因为它为玩家提供了游戏中物品相关的重要信息。

---

### 核心引擎兼容性：现代操控

[![ItemsEquipsCoreShopEquip.png](http://www.yanfly.moe/wiki/images/thumb/2/25/ItemsEquipsCoreShopEquip.png/600px-ItemsEquipsCoreShopEquip.png)](http://www.yanfly.moe/wiki/File:ItemsEquipsCoreShopEquip.png)

如果将 [VisuStella 核心引擎](http://www.yanfly.moe/wiki/Core_Engine_VisuStella_MZ) 添加到您的游戏中并启用现代操控，则物品菜单场景、装备菜单场景和商店菜单场景的操控方式将略有变化。

物品菜单场景会自动激活物品列表窗口，您可以使用左/右方向键（单列）或上/下翻页键（多列）在物品类别之间导航。在商店菜单场景中出售物品时也会发生类似情况。

装备菜单场景会自动激活装备栏位窗口，只有当您将鼠标移至该窗口时才会激活命令窗口。

[回到顶部](/visustella/1-itemequip#top)

---

## VisuStella MZ 兼容性

虽然此插件与 VisuStella MZ 插件库中的大多数插件兼容，但与某些特定插件或功能并不兼容。本节将重点介绍与此插件不兼容的主要插件/功能，或着重说明如何使某些功能兼容。

---

[战斗核心 VisuStella MZ](/visustella/1-battlecore)

[![ItemsEquipsCore 37 Comp 1.png](http://www.yanfly.moe/wiki/images/2/20/ItemsEquipsCore_37_Comp_1.png)](http://www.yanfly.moe/wiki/File:ItemsEquipsCore_37_Comp_1.png)

如果您已安装战斗核心，则无法通过物品和装备核心的插件参数来更改物品和装备核心商店状态窗口中的“伤害倍率”或“治疗倍率”。

请前往战斗核心的插件参数，选择“伤害设置”，然后选择“伤害样式”，并调整相应样式的“伤害倍率”或“治疗倍率”文本。

为什么需要这样做呢？因为并非所有伤害样式都使用“倍率”来计算，为了向玩家传达正确的信息，每种伤害样式都有其独特的描述方式，以更加准确。

[![ItemsEquipsCore 37 Comp 2.png](http://www.yanfly.moe/wiki/images/9/90/ItemsEquipsCore_37_Comp_2.png)](http://www.yanfly.moe/wiki/File:ItemsEquipsCore_37_Comp_2.png)

如果您忘记了这一点，当您访问物品和装备核心的插件参数时，参数描述中应该也会提醒您在哪里进行更改。

---

[VisuStella MZ武器切换系统](http://www.yanfly.moe/wiki/Weapon_Swap_System_VisuStella_MZ)

VisuStella MZ道具装备核心中的自定义装备栏功能允许玩家添加额外的武器栏位。现在，每个角色最多只能拥有一个武器栏位。此调整旨在确保武器切换系统的实用性。

[回到顶部](/visustella/1-itemequip#top)