---
sidebar_position: 11
---

# Skills and States Core

[Skills and States Core VisuStella MZ - Yanfly.moe Wiki](http://www.yanfly.moe/wiki/Skills_and_States_Core_VisuStella_MZ)



## 简介

“技能与状态核心”插件扩展并增强了 RPG Maker MZ 固有的技能、状态和增益功能，并允许游戏开发者自定义其各个方面。

功能包括（但不限于）以下所有方面：

- 为技能分配多种技能类型。
- 创建自定义技能消耗类型（例如生命值、金币和物品）。
- 允许技能消耗基于百分比或动态变化，可以直接通过技能本身或类似特性的注释标签进行设置。
- 替换不同职业的计量条，以显示不同类型的技能消耗资源。
- 根据开关、已习得技能和代码隐藏/显示和启用/禁用技能。
- 设置状态规则，包括死亡时是否清除状态、重新应用状态如何影响其回合数等等。
- 允许对状态进行分类，并使其受到类别的影响。
- 在窗口或精灵中绘制的状态上显示回合数。
- 通过技能和物品效果的注释标签来操控状态、增益和减益效果的回合数。
- 通过注释标签创建自定义的持续伤害状态计算。
- 允许数据库对象对其用户应用被动状态。
- 被动状态也可以设置激活条件。
- 更新了技能菜单场景布局，使其更符合现代审美。
- 如果安装了“物品与装备核心”，则可以利用商店状态窗口在技能菜单中显示技能数据。
- 控制技能菜单场景的各个方面。



## 主要变更

此插件为 RPG Maker MZ 的功能添加了一些新的硬编码特性。以下是这些特性的列表。

---

### 移除状态动作结束效果

[![SkillsStatesCore ActionEndStun.png](http://www.yanfly.moe/wiki/images/3/35/SkillsStatesCore_ActionEndStun.png)](http://www.yanfly.moe/wiki/File:SkillsStatesCore_ActionEndStun.png)

如果您的插件参数设置中启用了“动作结束更新”，则“动作结束”效果已更新，现在它会应用于每个已使用的动作，而不仅仅是在战斗角色动作集开始时生效。

然而，这样做也会带来一些副作用：如果一个状态同时具有“无法移动”的限制和“行动结束”的移除时间，那么不出所料，该状态将永远不会消失，因为它现在是基于实际行动结束而触发的。为了弥补这一点并避免混淆，当启用“行动结束更新”时，具有“无法移动”限制的状态的“行动结束”自动移除时间将转换为“回合结束”自动移除时间。

这种自动更改不会使其行为与“行动结束”移除时间完全相同，但总比完全锁定战斗角色要好。

示例：

新状态“烈焰之刃”将允许受影响的战斗角色造成火属性伤害。配合“行动结束”机制，这意味着在接下来的5次行动中，这些攻击将造成火属性伤害。

这意味着，如果由于“睡眠”或“眩晕”等状态效果而没有进行任何行动，则持续时间不会减少。

另一方面，如果战斗者每回合执行多个动作，则持续时间减少得更快，因为消耗的动作次数更多。

然而，如果“烈焰之刃”状态使用的是回合结束效果，则无论处于“睡眠”或“眩晕”状态，也无论每回合执行多少动作，其持续时间每回合都会减少1点。

---

### 增益与减益等级管理

[![SkillsStatesBuffDebuffs.png](http://www.yanfly.moe/wiki/images/e/e8/SkillsStatesBuffDebuffs.png)](http://www.yanfly.moe/wiki/File:SkillsStatesBuffDebuffs.png)

在 RPG Maker MZ 中，增益和减益效果叠加时，增益或减益效果的等级会相应变化。此插件在此机制上进行了改进：当增益或减益效果的等级达到中性值时，增益或减益效果将被完全移除，并且增益和减益效果的持续时间计数器将被重置，以提高计算的准确性。

---

### 技能消耗

[![SkillsStatesSkillCosts.png](http://www.yanfly.moe/wiki/images/thumb/5/50/SkillsStatesSkillCosts.png/600px-SkillsStatesSkillCosts.png)](http://www.yanfly.moe/wiki/File:SkillsStatesSkillCosts.png)

在 RPG Maker MZ 中，技能消耗曾经是硬编码的。现在，所有技能消耗类型（包括 MP 和 TP）都已移至插件参数中。这意味着从支付到检查消耗，所有操作都通过这些选项完成。

在 RPG Maker MZ 中，默认情况下，显示的技能消耗类型只有一种：如果可用则显示 TP，否则显示 MP。如果技能同时消耗 TP 和 MP，则只显示 TP。此插件通过按照插件参数“技能消耗类型”的顺序显示所有可用的消耗类型，从而改变了这一现状。

在 RPG Maker MZ 中，技能消耗默认仅以颜色区分。此插件改变了这一现状，在消耗值旁边同时显示技能消耗类型的名称。这样做是为了帮助色盲玩家区分技能的不同消耗类型。
\---

### 精灵计量表

[![SkillsStatesSpriteGauges.png](http://www.yanfly.moe/wiki/images/5/50/SkillsStatesSpriteGauges.png)](http://www.yanfly.moe/wiki/File:SkillsStatesSpriteGauges.png)

RPG Maker MZ 中的精灵计量表默认是硬编码的，仅用于显示 HP、MP、TP 和时间（用于 ATB）。此插件允许您通过“技能消耗类型”下的插件参数及其相关的 JavaScript 条目来自定义这些计量表。

---

### 状态显示

状态显示

要为状态赋值并将其与状态回合分开显示，您可以使用以下脚本调用。

```

batterer.getStateDisplay(stateId)

- 此脚本返回指定角色在该特定状态下存储的任何值。
- 如果没有要返回的值，则返回空字符串。

battler.setStateDisplay(stateId, value)

- 此方法将战斗者特定状态的显示设置为您声明的值。
- 该值最好使用数字或字符串。

battler.clearStateDisplay(stateId)

- 此方法清除战斗者特定状态的显示。
- 简而言之，此方法将存储的显示值设置为空字符串。

```

### 窗口函数移动

RPG Maker MZ 默认代码中 Window_StatusBase 和 Window_SkillList 中的一些函数现已移至 Window_Base，以便所有窗口均可使用这些函数。

---

## 滑倒伤害弹出窗口说明

滑倒伤害弹出窗口仅显示 HP、MP 和 TP 各一个，显示的数值是所有状态和效果的总和，无论战斗角色有多少种状态和效果。这与原版 RPG Maker MZ 的设定相同，也是我们希望 VisuStella MZ 库的设定。

这不是 bug！

我们不更改此设定的原因是，它无法准确地向玩家传递信息。当出现多个弹出窗口时，玩家只有大约一秒半的时间来计算并获取所有信息。我们认为，为了玩家的整体便利，展现累积性的变化，并引导玩家体验走向更积极的方向，会更加合适。

## 被动状态说明

[![SkillsStatesCorePassives.png](http://www.yanfly.moe/wiki/images/7/78/SkillsStatesCorePassives.png)](http://www.yanfly.moe/wiki/File:SkillsStatesCorePassives.png)

本节将解释关于被动状态的各种误解。被动状态在代码层面上与状态的工作方式不同。虽然它们在机制上使用了与状态相同的效果，但两者之间存在差异。

---

对于使用代码“a.isStateAffected(10)”来检查目标是否受到状态影响的用户，请注意，此代码不会检查被动状态。它只会检查直接应用于目标的状态。

这不是一个错误。

正确的做法是使用“a.states().includes($dataStates[10])”来检查被动状态。这段代码会同时搜索直接应用的状态和被动状态。

---

由于被动状态不被视为直接应用，因此它们也不符合条件分支的状态检查。条件分支的效果检查的是受影响的状态。

---

因为被动状态并非直接应用于战斗者，所以“addNewState”、“addState”、“eraseState”和“removeState”等函数也不适用于被动状态。这意味着与这些函数关联的任何相关的JS注释标签都不会被执行。

---

为什么被动状态不被视为受影响状态？让我们换个角度来看。赋予角色技能有两种方式：他们可以通过等级/物品/事件获得技能，或者他们可以装备暂时赋予该技能的装备。

学习技能是直接的。暂时赋予技能是间接的。这两个因素在机制上很重要，需要加以区分。

普通状态和被动状态也是如此。常规状态是直接生效的，因此需要加以区分，状态轮次、状态步骤、移除条件等机制才能发挥作用。被动状态是间接生效的，因此不受状态轮次、状态步骤和移除条件的影响。这些机制上的差异对于RPG Maker的运行方式至关重要。

---

再次强调，使用“a.isStateAffected(10)”检查目标是否处于被动状态时返回false并非bug。

---