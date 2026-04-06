---
sidebar_position: 5
---



# RMMZ的状态显示相关

原文：[『RPGツクールMZ』のステータス表示周り](https://zenn.dev/tonbi/articles/7b3a8c58812b48#window_statusbase)

最近研究了一下RMMZ的状态显示。此处所指的是HUD，也就是显示各种数据（例如生命值）的区域。

个人而言，除非是战斗机驾驶舱里的那种HUD，我觉得HUD的违和感太强了。但既然在游戏开发圈子已经成为通用术语，那我也就随大流了。

相关文章：

- [『RPGツクールMZ』のウィンドウ内容を調べてみた](https://zenn.dev/tonbi/articles/ad2f9c3350da85)
- [『RPGツクールMZ』のウィンドウ文字表示を調べてみた](https://zenn.dev/tonbi/articles/248bc9d7bf974a)
- [『RPGツクールMZ』文字表示関連のメソッド一覧](https://zenn.dev/tonbi/articles/e24e575aa0aa5e)

（以上都是日文原文）

依照惯例，我会提供[RMMZ非官方js参考页面](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/index.md)的链接，其中包含类和其他链接。（这是作者自己写的笔记，照样是日语原文）

## 前言

rmmv的时代，[Window_Base](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md)类就已经备齐了HUD相关的方法，在[试着绘制窗口内容](http://tonbi.jp/Game/RPGMakerMV/010/)这篇文章中已经有所叙述。

到了rmmz，这些相关的类已经被整理，HUD相关的方法被迁移到了 [Window_StatusBase](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md) 这里。

多亏了这一改动，窗口相关类的可读性得到了极大的改善。不过我觉得，或许将功能稍微再分担一些会更好。

以下是类的树状图。

- Window
  - Window_Base
    - Window_Scrollable
      - Window_Selectable
        - Window_StatusBase
          - Window_BattleStatus
            - [Window_BattleActor](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_BattleActor.md)
          - [Window_EquipSlot](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_EquipSlot.md)
          - [Window_EquipStatus](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_EquipStatus.md)
          - Window_MenuStatus
            - [Window_MenuActor](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_MenuActor.md)
          - [Window_NameEdit](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_NameEdit.md)
          - [Window_ShopStatus](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_ShopStatus.md)
          - [Window_SkillStatus](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_SkillStatus.md)
          - [Window_Status](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Status.md)
          - [Window_StatusParams](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusParams.md)
          - [Window_StatusEquip](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusEquip.md)

虽然`Window_StatusBase`下面挂载了大量的类，但在MV，HUD相关功能是放在`WindowBase`中，因此涉及到此处未列出的所有窗口。

MV大概是想着“把功能放在最根部的类里的话，需要的时候不就能直接用了吗”，但这样果然还是过于粗糙了。

尤其是颜色相关的功能被移动到了[ColorManager](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/ColorManager.md)中，更为清爽。

`ColorManager`的使用方法非常简单，只需调用与想要获取的颜色相对应的方法即可。

```
ColorManager.crisisColor(); //获取危险色（颜色编号：17）
```

有关这些窗口内容的绘制方面，在“[有关自定义菜单创建插件的研究](https://zenn.dev/tonbi/articles/33589b38be27a7)”中，也是无法回避的部分。

反过来，即使是想要进行完全的自定义的人，由于最为常用的的绘制命令已经在自定义菜单制作插件（以下简称scm）的参数中准备好了，因此可以作为练习。

最终，很可能会得出“既然有了这个插件，就不需要自己重新写插件了吧”这样的结论。

因此，这篇文章实质上就是“有关自定义菜单创建插件的研究2”。

## Window_Base

虽然已经有了不少变化，但仍然是相当重要的类。`Window_Base`包括了许多有关显示内容的方法。

### Window_Base：获取文本信息

这里是为\n[n]`和`\p[n]`这两个控制符所准备的，不过是用在类内部。

- [actorName (actorIndex)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#actorname-actorindex--string)
- [partyMemberName (partyMemberIndex)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#partymembername-partymemberindex--string)

由于控制符有时会被指定不存在的编号，因此上述方法中包含了在这种情况下返回空字符串的处理。不过直接使用以下方法也可以。

```
$gameActors.actor( actorIndex );	// actorName (actorIndex) 同理
$gameParty.members()[ partyMemberIndex - 1 ] ;	// partyMemberName (partyMemberIndex) 同理
```

另外，数据库-用语由[TextManager](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/TextManager.md)管理。

```
TextManager.currencyUnit;	// 获取[货币单位]设定的文本
```

大概这样就能简单地获取设定的文本。

如果不用这个方法，而是直接用字符串指定“HP”，那么在数据库中设置为“体力”时，就无法正确传达意思了，请注意。

尤其在编写插件时也需要注意这一点。

### Window_Base：显示设定

这里也大多是与控制符相关的内容，但其中也有无法用控制符更改的项目。

| 方法                                                         | 说明                     |
| ------------------------------------------------------------ | ------------------------ |
| [changeOutlineColor (color)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#changeoutlinecolor-color) | 设定文字轮廓颜色         |
| [changePaintOpacity (enabled)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#changepaintopacity-enabled) | 设置是否可用             |
| [changeTextColor (color)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#changetextcolor-color) | 设置文字颜色             |
| [systemColor ()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#systemcolor---mvcsscolor) | 返回系统颜色             |
| [makeFontBigger ()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#makefontbigger-) | 将文字变大（`\{`）       |
| [makeFontSmaller ()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#makefontsmaller-) | 将文字变小（`\}`）       |
| [resetFontSettings ()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#resetfontsettings-) | 字体恢复默认（包括颜色） |
| [resetTextColor ()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#resettextcolor-) | 文字颜色恢复默认         |

除了这些之外，还有像`processColorChange()`这样以process开头的方法，同样用于控制字符，有时会处理范围外的值，有时完全不做处理。

因此，应该也没有特意使用的必要。

可能会想，怎么没有`\FS[n]`的方法，这个是通过直接设置属性来实现的。

```
this.contents.fontSize = 32;	// 文字大小设定为32px
```

更改字体就是这样。

```
this.contents.fontFace = $gameSystem.mainFontFace();// [系统2]-[进阶设定]-[主字体文件名]
this.contents.fontFace = $gameSystem.numberFontFace();//  [系统2]-[进阶设定]-[数字字体文件名]
```

这是假定在目标类内部进行读取的（继承了某类的）类。`Window` `this` `Window`

关于控制符，虽然没有准备直接的指定方式，但由于后文的`drawText()`或`drawTextEx()`的参数中有x和y，因此可以在此调整配置。

在`drawTextEx()`显示字符串中可以直接使用控制符。

### Window_Base：获取尺寸和显示坐标

这里是在布局时使用的，用于获取各种UI部件尺寸的方法。

与颜色与字符串同样，如果直接通过字面量指定，会破坏一致性，因此尽可能使用通过这些方法获取的值来进行布局。

| 方法                                                         | 说明                                  |
| ------------------------------------------------------------ | ------------------------------------- |
| [baseTextRect (actorIndex)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#basetextrect---rectangle) | 返回用于显示文字的矩形范围            |
| [calcTextHeight (textState)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#calctextheight-textstate--number) | 返回指定文本显示时的高度              |
| [contentsHeight()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#contentsheight---number) | 返回内容高度                          |
| [contentsWidth()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#contentswidth---number) | 返回内容高度                          |
| [fittingHeight (numLines)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#fittingheight-numlines--number) | 返回指定行数所需的高度                |
| [itemHeight()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#itemheight---number) | 返回项目的高度（默认值：36）          |
| [itemPadding()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#itempadding---number) | 返回项目的内边距宽度（默认值：8像素） |
| [itemWidth()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#itemwidth---number) | 返回项目的宽度                        |
| [lineHeight()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#lineheight---number) | 返回行的高度（默认值：36像素）        |
| [maxFontSizeInLine (line)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#maxfontsizeinline-line--number) | 返回指定行中的最大字体尺寸            |
| [textSizeEx (text)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#textsizeex-text--mvsize) | 返回经过控制字符变更后的文字尺寸      |
| [textWidth (text)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#textwidth-text--number) | 返回绘制指定字符串时的宽度            |

※此处的“内容”指的是“除去窗口边框后的显示部分”。

※数值的单位为像素。

※所谓“行”，指的是显示文字时的行。

※所谓“项目”，指的是命令、物品等用于选择的UI的一个单位。本文基本不会对此进行解说（或许会在别的文章中解说）。

### Window_Base：内容的显示

此处是用于绘制图标、文字等窗口内信息的方法。

在自定义窗口内容时，如同主角般的存在。

基本用法是，在核心脚本中找到使用这些方法的地方，然后用插件进行覆盖。

若要应对复杂的游戏系统，也许创建一个新的窗口类并整体更改布局会更好。

| 方法                                                         | 说明                       |
| ------------------------------------------------------------ | -------------------------- |
| [drawCharacter (characterName, characterIndex, x, y)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#drawcharacter-charactername-characterindex-x-y) | 绘制行走图                 |
| [drawCurrencyValue (value, unit, x, y, width)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#drawcurrencyvalue-value-unit-x-y-width) | 绘制带有货币单位的持有金钱 |
| [drawFace (faceName, faceIndex, x, y, width opt, height opt)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#drawface-facename-faceindex-x-y-width-opt-height-opt) | 绘制脸图                   |
| [drawIcon (iconIndex, x, y)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#drawicon-iconindex-x-y) | 绘制图标                   |
| [drawItemName (item, x, y, width)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#drawitemname-item-x-y-width) | 绘制[item]的[名称]         |
| [drawRect ( x, y, width, height )](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#drawrect--x-y-width-height-) | 绘制矩形                   |
| [drawText (text, x, y, maxWidth, align)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#drawtext-text-x-y-maxwidth-align) | 绘制字符串                 |
| [drawTextEx (text, x, y, width)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_Base.md#drawtextex-text-x-y-width--number) | 绘制包含控制符的字符串     |

我认为`drawTextEx`的使用频率很高。

以上就是`Window_Base`类中包含的与内容显示相关的方法。

※译者：这个[item]指的应该是SceneCustomMenu.js的变量

## Window_StatusBase

接下来是`Window_StatusBase`类的方法

若摘录之前展示的类树的一部分，则如下所示：从 `Window_Base` 类到 `Window_StatusBase` 之间，继承了 `Window_Scrollable` 和 `Window_Selectable` 这两个类。

不过，这一部分正如其名，是“与滚动相关的功能追加”和“与命令等选择相关的功能追加”，因此并未添加单纯与内容绘制相关的新功能。

Window_Scrollable、Window_Selectable — 不过这方面正如其名，只是“关于滚动的功能追加”以及“关于命令等选择的功能追加”，因此并未添加单纯与绘制内容相关的新功能。

此外，对于进一步继承了 `Window_StatusBase` 类的子类而言，几乎没有添加绘制类的新功能。

译者：不知道为什么，行内代码块都被挤到最后一行了，乱七八糟的，可能有些理解错误

- Window
  - Window_Base
    - Window_Scrollable
      - Window_Selectable
        - [Window_StatusBase](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md)

因此，我们将详细查看 `Window_StatusBase` 类。

作为参数传递的 `actor` 是拥有角色信息的 [Game_Actor](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_Actor.md) 类。

### Window_StatusBase: 获取文本信息

| メソッド                                                     | 説明                         |
| ------------------------------------------------------------ | ---------------------------- |
| [actorSlotName (actor, index)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#actorslotname-actor-index--string) | 返回角色的[装备类型]的显示名 |

### Window_StatusBase: 获取显示坐标/尺寸

| メソッド                                                     | 説明                         |
| ------------------------------------------------------------ | ---------------------------- |
| [gaugeLineHeight](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#gaugelineheight---number) | 返回计量条高度（默认为24px） |

### Window_StatusBase: 显示内容

| メソッド                                                     | 説明               |
| ------------------------------------------------------------ | ------------------ |
| [drawActorCharacter (actor, x, y)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#drawactorcharacter-actor-x-y) | 绘制角色的[行走图] |
| [drawActorClass (actor, x, y, width)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#drawactorclass-actor-x-y-width) | 绘制角色的[职业]   |
| [drawActorFace (actor, x, y, width, height)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#drawactorface-actor-x-y-width-height) | 绘制角色的[脸图]   |
| [drawActorIcons (actor, x, y, width)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#drawactoricons-actor-x-y-width) | 绘制角色的[图标]   |
| [drawActorLevel (actor, x, y)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#drawactorlevel-actor-x-y) | 绘制角色的[等级]   |
| [drawActorName (actor, x, y, width)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#drawactorname-actor-x-y-width) | 绘制角色的[名称]   |
| [drawActorNickname (actor, x, y, width)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#drawactornickname-actor-x-y-width) | 绘制角色的[别称]   |
| [drawActorSimpleStatus (actor, x, y)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#drawactorsimplestatus-actor-x-y) | 绘制角色的简易状态 |

### Window_StatusBase: 内容の配置

这是rmmz中，实现了将状态显示作为类来进行配置的部分。

相对于draw系列的方法直接在纸上绘制，`sprite`可能更接近于贴贴纸的感觉。

| メソッド                                                     | 説明                       |
| ------------------------------------------------------------ | -------------------------- |
| [placeActorName (actor, x, y)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#placeactorname-actor-x-y) | 配置角色名                 |
| [placeBasicGauges (actor, x, y)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#placebasicgauges-actor-x-y) | HP・MP・TP的基本计量条配置 |
| [placeGauge (actor, type, x, y)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#placebasicgauges-actor-x-y) | 计量条配置                 |
| [placeStateIcon (actor, x, y)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#placestateicon-actor-x-y) | 状态图标配置               |
| [placeTimeGauge (actor, x, y)](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Window_StatusBase.md#placetimegauge-actor-x-y) | 时间条配置                 |

## 总结

关于这些绘制方法，我认为在[有关自定义菜单创建插件的研究](https://zenn.dev/tonbi/articles/33589b38be27a7)中所写的功能当中，经常需要写在脚本里，因此如果能将其作为辅助读物来使用，我将不胜感激。
