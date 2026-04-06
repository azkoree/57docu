---
sidebar_position: 2
---



# RMMZ的脚本应用

那么在前一篇[RPG Maker MZ 脚本使用方法基础](./script-basic)中，我想大家已经能做到将脚本复制粘贴到【脚本】事件命令中，并进行一些简单的修改了（做到了吧！）

大致上，我们将假设大家已经阅读了上次的内容，并通过复制粘贴和改造，用rmmz进行游戏制作大约半年左右。

因此，本次我们将更进一步，目标是能够掌握更具应用性的使用方法。

用脚本能实现的事情千差万别，但也存在一些经典的格式模式。

记住这些模式并加以复用，进一步增加改造的多样性吧！

虽然主要设想是在【脚本】事件命令中使用，但也会时不时提到在其他命令中的使用方法。

和往常一样，我会适时链接到[RPG Maker MZ 非官方 JavaScript 参考手册](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/index.md)



## 术语

…虽然完全不觉得靠这个说明能让人看懂，但因为无论如何都会用到这些术语，所以希望大家至少能到了突然出现时不会吓一跳的程度。

因为已经（假设）使用了半年的脚本，所以我想大家应该已经大致理解了。

粗略扫一眼跳过去也没问题。如果在意某个术语可以回来确认。估计还是不太明白吧（过分）。

**数组**…给值编号并排列而成的值。示例：`[ 10, 4, 6 ]`（这里作为值排列了数字，但也可以排列其他类型的值）

**下标**…从数组（或保存数组的变量）中取出值时使用的数字。示例：`array[ 0 ]`（JavaScript 数组的下标从 0 开始）

**字符串**…将字符排列而成的值。在js中就是 `String`。也可以看作是值被固定为单个字符的数组。示例：`"我是字符串"`

**布尔值**…取真（正・ON）和假（负・OFF）两种状态的值。在 JavaScript 中称为 `Boolean`，两个值分别用 `true` 和 `false` 表示。

**逻辑运算**…计算结果返回布尔值的运算。包括判断数值大小等的条件表达式。

**变量**…用于保存值。js的变量与rmmz的变量大致相同。定义示例：`let variable;` 以前定义变量时不用 `let` 而用 `var`，但存在很多问题，现在（2022 年）已经不太使用了。反过来，如果看到使用了 `var`，连外行都能轻易看出是旧代码。另外，到了《RPG Maker MZ》，核心脚本已经废止了 `var`。

**常量**…与变量大致相同，但一旦设定值后就不能更改。乍一看觉得不便，但实际上比变量更方便，在实际编程中几乎不需要使用变量。定义示例：`const constant = 1;`

**函数**…将处理归纳在一起的东西。与rmmz的【公共事件】大致相同，但由于有参数和返回值，使用起来方便得多。另外，【脚本】事件命令也能写多个处理，所以也可以说是一种函数，【变量操作】中的【脚本】等就有返回值。js由于历史原因，函数的定义方法有很多种，这比较麻烦。定义示例：`function addOne( arg ) { return arg +1; };`、`const addOne = arg => arg + 1;`

**参数**…执行函数时写在 `()` 内并传递的值。函数可能没有参数，也可能有多个参数。

**返回值**…函数返回的值。有的函数有返回值，有的没有。

**对象**…将相关的值（属性）和功能（方法）归纳在一起的东西。js的程序就是通过组合这些对象构成的。

**属性**…附着于对象的变量。但与变量不同的是，有些属性会根据对象的状态而改变值。反过来，通过设置属性也可能改变对象其他属性等的状态。在对象后面加上 `.` 然后指定。示例：`object.property`

**只读属性**…附着于对象的只读值。但与常量不同的是，有些只读属性会根据对象的状态而改变值。read only 常缩写为 ro 或 r/o。

**方法**…附着于对象的函数。通常用于加工属性。在对象后面加上 `.` 后指定，并在 `()` 中指定参数。示例：`object.method()`

## 值的操作

在通常的事件命令中给变量或开关设定值，然后在【脚本】命令中使用该值，就可以模拟出类似函数的参数。

而通过将值设定给变量或开关，则可以模拟出返回值。

在rmmz中，通过改变值来切换【事件】的状态即【事件页面】是一种重要的控制方法，从这个意义上说，改变值也是重要的处理。

另外，在很多情况下【事件命令】无法使用变量来设定值，但可以通过【脚本】执行与【事件命令】同等的处理，并将获取的值赋值给变量。

梦想又扩大了！让我们熟练掌握与值设定相关的js吧！

顺便一提，与脚本之间传递值时，推荐使用ID为1的变量和开关。

这是因为在各种事件命令中，变量和开关ID的初始值都是1，所以无需特别指定就可以直接使用。

另外，我个人习惯把ID1的变量和开关的名字设为 `it`。这是Mac用户都知道的HyperTalk的风格（在AppleScript中则是 `result`）。

### 变量的操作

| 值与操作      | 脚本                               |
| ------------- | ---------------------------------- |
| 给变量1赋值10 | `$gameVariables.setValue( 1, 10 )` |
| 从变量1取出   | `$gameVariables.value( 1 )`        |

[参考链接: Game_Variables.setValue()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_Variables.md#setvalue-variableid-value)

[参考链接: Game_Variables.value()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_Variables.md#value-variableid--)

下面是将事件命令作为文本复制出来的内容，因此如果粘贴到脚本中，请删除 js 开头处从冒号到之前的部分。

```
◆变量操作：#0001 = 12
◆脚本：const arg = $gameVariables.value( 1 );
：　　　　　：const result = Math.random() * arg;
：　　　　　：$gameVariables.setValue( 2, result );
```

这种情况下，刚刚在变量的操作中赋值给变量ID1的 `12` 又被赋值给了变量 `arg`。这就是参数。

然后将随机数 `Math.random()` 乘以 `arg` 的结果赋值给 `result`，并返回给变量ID2。

这个变量ID2就相当于返回值。

顺便一提，脚本也可以写成下面这样。

```
$gameVariables.setValue( 2, Math.random() * $gameVariables.value( 1 ) );
```

这种程度的话倒不算太难读，但如果变得复杂，还是先赋值给常量再用会更易读。

`<Nice!>` 变量在变量的操作中有脚本字段，这种情况下不需要对返回值进行操作。

```
◆变量操作：#0001 = 12
◆变量操作：#0002 = Math.random() * $gameVariables.value( 1 );
```

单看这个，因为先存入变量ID1又立刻取出，似乎没什么意义，但如果脚本部分是一个公共事件，就能明白它的便利之处了。

即使只有一个公共事件，通过事先给变量赋予各种不同的值，就能执行相应的处理，因此不需要制作大量的公共事件。

### 开关操作

| 值与操作    | 脚本                                 |
| :---------- | :----------------------------------- |
| 开关1的ON   | `$gameSwitches.setValue( 1, true )`  |
| 开关1的OFF  | `$gameSwitches.setValue( 1, false )` |
| 从开关1取出 | `$gameSwitches.value( 1 )`           |

| 値と操作              | スクリプト                           |
| --------------------- | ------------------------------------ |
| スイッチ1のON         | `$gameSwitches.setValue( 1, true )`  |
| スイッチ1のOFF        | `$gameSwitches.setValue( 1, false )` |
| スイッチ1から取り出し | `$gameSwitches.value( 1 )`           |

[参考链接: Game_Switches.setValue()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_Switches.md#setvalue-switchid-value)

[参考链接: Game_Switches.value()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_Switches.md#value-switchid)

在参考链接中，如果 **→** 后面写的是 `Boolean`，则可以设定给开关。

[参考链接: Game_Party.inBattle()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_Party.md#inBattle-)

此外，逻辑运算（如数值比较等）的结果也可以设定给开关。

`<Bad!>` 开关的操作中没有脚本字段。

通过使用条件分支中的脚本，并在分支中放置ON和OFF的开关操作，虽然行数较多，但勉强可以将脚本的结果放入开关。

例如，像下面这样，就可以根据是否战斗中分别设置ON和OFF来设定开关。

```
◆条件分支：脚本：$gameParty.inBattle();
  ◆开关的操作：#0001 it = ON
  ◆
：除此之外的情况
  ◆开关的操作：#0001 it = OFF
  ◆
：分支结束
```

不过……好像有些冗长了吧。

我认为使用脚本事件命令，并用 js 直接指定要赋值返回值的开关，会更加简洁。

```
◆脚本：$gameSwitches.setValue( 1, $gameParty.inBattle() );
```



### 独立开关的操作

| 值与操作                          | 脚本                                                 |
| --------------------------------- | ---------------------------------------------------- |
| 地图ID2、事件ID3的独立开关设为ON  | `$gameSelfSwitches.setValue( [ 2, 3, "A" ], true )`  |
| 地图ID2、事件ID3的独立开关设为OFF | `$gameSelfSwitches.setValue( [ 2, 3, "A" ], false )` |
| 从地图ID2、事件ID3的独立开关取出  | `$gameSelfSwitches.value( [ 2, 3, "A" ] )`           |

[参考链接: Game_SelfSwitches.setValue()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_SelfSwitches.md#setvalue-key-value)

[参考链接: Game_SelfSwitches.value()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_SelfSwitches.md#value-key--boolean)

独立开关的 `[ ]` 部分，按顺序写为 [ 地图ID, 事件ID, 类型 ]。类型不要忘记用 `"` 引号括起来！

[参考链接: MV.SelfSwitch](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/MV.SelfSwitch.md)

在事件命令中，独立开关顾名思义只能设置自身的开关，但在脚本中，不仅可以指定其他事件，甚至还能指定其他地图的事件，而且类型没有限制，不仅能使用 "A"、"B"、"C"、"D" 到 "Z"，甚至还能指定像 "wait" 这样的任意字符串。

把类型指定为中文……虽然能运行，但我个人稍微有点不放心。大概没问题吧。

### 整体值的操作

在游戏结束重新尝试时，如果返回标题画面倒是会被初始化，但游戏体验会受损，这很麻烦。

这里介绍在这种情况下很方便的、整体值初始化的方法。

ゲームオーバーからの再トライをする際、タイトルまで戻せば初期化はされるのですが、プレイ感が損なわれるのが困ります。
そういう場合に便利な、値全体を初期化する方法を紹介します。

| 值与操作           | 脚本                                                      |
| ------------------ | --------------------------------------------------------- |
| 开关初始化         | `$gameSwitches.clear();`                                  |
| 变量初始化         | `$gameVariables.clear();`                                 |
| 独立开关初始化     | `$gameSelfSwitches.clear();`                              |
| 全物品初始化       | `$gameParty.initAllItems();`                              |
| 全成员的技能初始化 | `$gameParty.allMembers().forEach( e => e.initSkills() );` |

感觉还有其他需要初始化的东西，但使用全恢复事件命令之类的应该就可以了。

如果不知道初始化方法的话，请在评论里留言。

关于通过范围指定来设定值，我会在后面介绍。



### 事件命令中的变量加法操作

在变量的操作中，指定变量单独:2、操作:加法、操作数:常数:10 时，与之相同的脚本事件命令可以写成下面这样。

```
$gameVariables.setValue( 2, $gameVariables.value( 2 ) + 10 );
```

好麻烦啊…直接用变量的操作事件命令不就好了吗？——话虽如此，但考虑到今后的应用，我觉得最好还是知道与事件命令相同的脚本该怎么写。

除了加法，当然也可以使用变量的操作中有的减法 `-`、乘法 `*`、除法 `/`、取余（除法的余数）`%`，而且使用 js 还能写更复杂的计算公式。

当处理变得更加复杂时，用脚本写会比用事件命令写要简洁得多的情况会越来越多。

除了四则运算，js 的 `Math` 对象中还有之前介绍过的 `random()` 等许多方法，在 rmmz 中也可以活用。

参考:[Math - JavaScript| MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Math)

### 变量的操作中的加法操作

在变量的操作中，选择变量单独:2、操作:代入、操作数:脚本时，与刚才的脚本动作相同的脚本可以写成下面这样。

```
$gameVariables.value( 2 ) + 10
```

因为没有代入操作，所以变得相当短。

正如最初所写，这本来就是变量的操作的基本功能就能完成的操作，所以不需要使用脚本，但由于有很多值无法通过变量的操作直接获取，所以这种写法具有应用性。

我想大家通过复制粘贴脚本，应该已经习惯了这种用法，但还是简单复习了一下。

### 变量的操作中的加法

在变量操作中，选择变量单独:2、操作:加法、操作数:脚本时，与刚才相同的动作的脚本可以写成下面这样。

```
10
```

如果只是 10 的话当然没有使用脚本的意义，但这个例子想说明的是：只要使用变量的操作并适当选择操作，就能写得相当简短。

有时候明明在命令侧设置一下就能写得很短，却非要用脚本强行实现导致复杂化，这种情况出乎意料地多，所以请尽量活用标准功能！



### 通过 js 常量进行拆分

话说回来，我们刚才一直在翻来覆去讲的这个脚本，正如所见，变量的操作相对于想做的事情来说，描述往往较长且容易变得难读。

```
$gameVariables.setValue( 2, $gameVariables.value( 2 ) + 10 );
```

正如之前所写，最好先将值赋给（用 const 定义的）常量，将脚本拆分。

```
const id = 2;
const prev = $gameVariables.value( id );
$gameVariables.setValue( id, prev + 10 );
```

我想很多人会觉得“这不反而更长了吗！”，但只看实际处理所在的第3行，就相当简洁了。

比起一次性处理需要9分理解力的东西，人类奇怪地反而更擅长分三次处理各需4分理解力的事情，这样整体理解成本会降低。

这种“要素分解”是编程中的基本思想。请勤于拆分。

另外，使用常量的话，在后续修改或脚本变长等情况下，各方面都会很方便。

事件命令的【脚本】能写的行数并不多，所以“脚本变长”实际上意味着将其插件化的时候。

### 用 js 进行区间判定

经常想在条件判定中判断是否在 A 到 B 之间……但做不到。至少单独做不到。

你是这么想的吧！能做到！用 js 的话！！

在条件判定 - 脚本中这样写：

```
3 <= $gameVariables.value( 5 ) && $gameVariables.value( 5 ) <= 10;
```

这样就表示“变量 ID5 在 3 到 10 之间”的意思。

```
( v => 3 <= v && v <= 10 )( $gameVariables.value( 5 ) );
```

虽然进行的是相同的判断，但这种写法在需要修改变量 ID 时只需改一处，所以稍微方便一点。

虽然 `=>` 和 `<=` 等类似的符号很多，详细说明会变得复杂，但请抱着“能写短不挺好的嘛！”这样的感觉去用。

## 关于标识符

常量、变量、函数等的名称（标识符）请避免使用像 `a`、`b`、`c` 这样单个字母或者过度省略、让人无法理解内容的名称。

`<Bad!>` 老实说，我根本记不住 rmmz 的计算式中使用的 `a` 和 `b` 哪个是哪个，话说那种东西根本不可能记住吧？

另外，虽然也可以用 `target` 来代替 `b`（虽然是非官方），使用 `target` 会让代码在可读性上压倒性地好很多……但计算式的输入栏很窄，结果还是不好看……。

[参考链接: RPG.Damage#计算式](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/RPG.Damage.md#計算式)

如果不是要给别人看的东西，做起来方便就是最好的。

话虽如此，至少像用 `element` 的缩写 `e` 这种程度的意义还是必要的。

`temporary` 的缩写 `tmp`，以及 `index` 的缩写 `i`、`height` 的 `h`、`width` 的 `w` 等，都是编程中经常使用的缩写变量，所以最好不要偏离这些常见的含义去使用它们。

另外，对于作为参数写出但不使用的东西，惯例是用 `_` 作为标识符。

结论：给我猛查英语词典！！（然后复制粘贴来用）

## 范围指定

不仅限于变量的操作，经常会有想对从某个编号到某个编号的全部内容进行操作的情况。

在开关的操作和变量的操作等事件命令中也准备了范围指定。

要设定1到4的开关时，单纯地考虑会写成下面这样吧。

```
$gameSwitches.setValue( 1, true );
$gameSwitches.setValue( 2, true );
$gameSwitches.setValue( 3, true );
$gameSwitches.setValue( 4, true );
```

嗯…这样写也行，但在这种情况下，js 中准备了用于循环的功能。

下面我一边想着“看了这个例子能改造吗？如果能改造的话反而很厉害吧？”一边写。哈哈哈。

以“复制粘贴然后改写像那么回事的数值”为基本姿势！

另外，下面的例子可以在 js 控制台中执行，所以可以通过改造、执行，然后在 [F9] 的调试画面中确认结果，这样去习惯会比较好。

在显示调试画面的状态下执行脚本，然后操作调试画面改变显示，画面会重新绘制，所以可以轻松确认结果。

啊，要改写的开关请事先在 rmmz 的编辑器那边创建好。

### 开关1到4设为ON

在开关的操作中指定开关范围:1～4、操作:ON 时，与之相同的脚本可以写成下面这样。

```
for( let i = 1; i < 5; i++ ) $gameSwitches.setValue( i, true );
```

for 后面的括号中的 `;` 不可省略。

要设定的数值只到 4，但脚本里写的数值却是 5，这可能会让你觉得有点不舒服，但就是这么回事。

详细请阅读 [for - JavaScript | MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Statements/for)（完全甩锅）

```
for( let i = 1; i <= 4; i++ ) $gameSwitches.setValue( i, true );
```

像这样加上 `=` 写成 `<=` 的方法也是有的。这方面随你喜欢。

顺便一提，不能反过来写成 `=<`，必须是 `=` 在后面。

### 1～4中除了3以外设为ON

```
for( let i = 1; i < 5; i++ ) if( i !== 3 ) $gameSwitches.setValue( i, true );
```



这是在刚才的脚本中插入了 `if( i !== 3 )` 的形式。

### 1～4中把2设为OFF，其他设为ON

```
for( let i = 1; i < 5; i++ ) $gameSwitches.setValue( i, i !== 2 );
```

在原本写 `true` 的位置写了逻辑运算（条件表达式）。

如前所述，逻辑运算的结果是布尔值，所以可以赋值给开关。

### 将非连续编号的指定开关设为ON

如果不是连续编号的情况该怎么办呢？难道只能放弃然后老老实实地一个个列出来吗？

这样做：

```
[ 2, 9, 14, 21 ].forEach( i => $gameSwitches.setValue( i, true ) );
```

这样，就会对开头列出的那些编号的开关执行 ON。

这个叫 `forEach` 的东西，和刚才的 `for` 有什么区别之类的话题会相当复杂……所以请抱着“细节别在意”的精神来对待。

光是写关于使用这个数组（行首的 `[]` 部分）的处理，就肯定会远远超过本页的篇幅。

详细请阅读以下链接（完全甩锅）

[Array - JavaScript | MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array)

## 画面上角色的指定

继变量、开关、独立开关之后，我们来看看画面上显示的角色的指定方法。

### 任何时候

以下的内容使用的是以 `$` 开头的全局变量，因此在任何地方都可以用同样的写法。

| 角色      | 脚本                                    |
| :-------- | :-------------------------------------- |
| 玩家      | `$gamePlayer`                           |
| 队列成员0 | `$gamePlayer.followers().follower( 0 )` |
| 队列成员1 | `$gamePlayer.followers().follower( 1 )` |
| 队列成员2 | `$gamePlayer.followers().follower( 2 )` |
| 小型船    | `$gameMap.boat()`                       |
| 大型船    | `$gameMap.ship()`                       |
| 飞空艇    | `$gameMap.airship()`                    |
| 事件      | `$gameMap.event( 1 )`                   |

:::info

关于队列成员和交通工具，不知为何无法在通常的设置移动路线事件命令中指定。

因此要处理这些细微的动作，只能灵活运用脚本事件命令（仅靠这个相当吃力）或插件。

设定给事件的数值是 1 以上的整数，即事件 ID。

`$gameMap` 是当前的地图，不能像独立开关那样指定其他地图。

:::

### 事件命令

在脚本事件命令中，可以使用 [character()](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_Interpreter.md#character-param--game_character) 方法来指定角色。

| 角色     | 脚本                   |
| -------- | ---------------------- |
| 玩家     | `this.character( -1 )` |
| 本事件   | `this.character( 0 )`  |
| 其他事件 | `this.character( 1 )`  |

:::info

关于玩家的指定有 `$gamePlayer`，事件的指定也有 `$gameMap.event( 1 )`，所以实际上除了 `this.character( 0 )` 之外，基本上没有使用其他参数的机会。

`character()` 的存在是为了根据事件命令中指定的数值进行分支处理。

因此，除了“本事件”以外没有必要使用它，但只要能掌握 `character()` 的用法，就无需记住其他写法并区分使用，这一点非常方便。

:::



### 移动路线

在移动路线的脚本移动命令中，可以用 `this` 来指定目标角色。

| 角色     | 脚本   |
| -------- | ------ |
| 目标角色 | `this` |

:::info

如果目标角色改变，`this` 所指向的对象也会改变。

保持脚本不变，只要指定不同的目标角色，或者将脚本复制到其他事件中，就可以控制其他角色或事件。

:::

## 角色的指定

即使想指定画面上的角色并调查其能力值等参数，但拥有参数的实际上是角色，因此无法从画面上的角色直接获取。

因此，这里介绍角色的指定方法。

### 角色对象与角色数据

虽说都是“角色”，但 rmmz 处理的有以下两种。

角色对象，具有便于在游戏内处理数据的功能。

它拥有装备、HP 等可变值的当前值，以及与角色相关的功能。

[参考链接: Game_Actor](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_Actor.md)

角色数据库，用于保存在数据库 - 角色中输入的值。

可以说它就是 "data/" 文件夹下的 "Actors.json" 文件本身。

数据库中只存在属性，没有方法。

[参考链接: RPG.Actor](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/RPG.Actor.md)

### 通过 ID 指定角色

如果知道角色 ID，例如 ID 为 1 时，可以写成下面这样。

```
$gameActors.actor( 1 )
```

`$gameActors` 是用于统一处理角色的对象。


[参考链接:Game_Actors](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_Actors.md)

### 通过成员指定角色

当你需要的不是角色 ID，而是当前玩家或队伍成员的角色数据时。

使用 `$gameParty` 这个全局变量。

[参考链接:Game_Party](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_Party.md)

| 角色         | 脚本                           |
| ------------ | ------------------------------ |
| 领队（玩家） | `$gameParty.leader()`          |
| 成员0        | `$gameParty.allMembers()[ 0 ]` |

成员0 和领队是同一个。

此外还有只取出死亡成员的 `deadMembers()`、只取出战斗成员的 `battleMembers()` 等各种方法。

当指定的成员不存在时，会返回 `undefined`。

### 从成员获取角色 ID

在变量的操作 - 游戏数据 - 队伍中，可以指定成员并将角色 ID 设定给变量。

因此，如果只是为了这个目的，倒不需要特意用 js，但有时需要在脚本中从成员获取角色 ID，“然后想在下一行使用它”。

```
const actorId = $gameParty._actors[ 0 ];
```

首个角色的角色 ID 之类的，看起来 `$gamePlayer` 似乎会拥有，但意外地它并没有。

rmmz 的核心脚本中，经常在你猜测“应该在这里吧”的地方却没有目标值，不过参考事件命令的写法，可以在一定程度上预判其存在位置。

### 通过 ID 指定角色的数据库

如果知道角色 ID，例如 ID 为 1 时，可以写成下面这样。

```
$dataActors[ 1 ]
```

关于所获得的数据库对象中存在的属性，请参阅参考链接。


[参考链接:RPG.Actor](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/RPG.Actor.md)

### 从角色对象指定角色数据

大多数情况下从 `$dataActors` 取值应该更快，但在不知道角色 ID 却可以通过成员指定角色本身的时候。

要从角色对象获取角色数据，只需在末尾添加 `.actor()`，如下所示。

```
$gameParty.allMembers()[ 0 ].actor()
```



## 元数据

在数据库等中设置的备注栏也可以从脚本中获取。

大致上，从 `$dataXxxx` 系列的全局变量追溯到的数据都拥有备注（理所当然，有备注栏的东西都拥有数据）。

[参考链接: 全局变量列表](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/global.md)

例如 `$dataEnemies[2].note` 这样，可以轻松获取敌角色 ID2 的备注内容。

如果你经常使用插件，应该曾在备注栏中写入过元数据吧。

```
<元:内容>
```

那个其实并不是插件专用的值，所以可以用 `$dataEnemies[2].meta` 来获取。

每个元标签的值可以像 `$dataEnemies[2].meta.元` 这样来获取。

由于在程序部分使用日文表记稍微有点不安，所以写成 `$dataEnemies[2].meta[ "元" ]` 可能更好。

无论用哪种写法，都能获取到相同的值。

```
const metaList = $dataEnemies.filter( e => e && e.meta[ "メタ" ] );
$gameVariables.setValue( 1, metaList );
```

像这样操作，就能筛选出写有 `<元>` 的敌人，并提取出一个数组。

因为已经放入了 rm 的变量中，之后就可以使用事件命令来进行处理。

<details>
    <summary>小知识</summary>

    虽然不限于元数据，但我觉得这部分写法不太好懂，所以来解说一下。
    
    `e && e.meta[ "元" ]`
    
    首先，`e` 中会依次存入` $dataEnemies `所包含的值之一，但有时该值也可能不存在。
    
    这种情况下，如果加上 `e &&`，那么` && `后面的部分就不会被处理。
    
    这个机制被称为逻辑运算的“短路求值”等。
    
    而在 js 中，作为返回值，写在其中的值会被原样返回。
    
    在这里，如果` e `是 `null` 等被判定为 `false` 的值，则返回 e 的值。
    
    接下来，`e `被判定为 `true `的情况……也就是这里数组中存放的是对象的情况。
    
    就会检查` && `后面的 1e.meta[ "元" ]`。
    
    如果备注栏中有` <元>`，则返回` true`，否则返回 `undefined`，由此筛选数组的值，最终只返回那些写有 `<元> `的值所组成的数组——就是这么回事。
    
    如果不理解这么复杂的机制就无法使用，却仅仅因为“就是想写短一点”而用它——说句实在话，程序员真是个奇怪的物种啊……。
    
    比起刻意追求简短，写得易懂更好哦（对某人说）。
</details>



## 图片

个人来说不太常使用图片，所以不太清楚能有多大用处。

使用图片的人很多，所以我只写下基本内容。首先是图片的指定方法。



| 图片    | 脚本                       |
| ------- | -------------------------- |
| 图片ID1 | `$gameScreen.picture( 1 )` |

### 清除所有图片

```
$gameScreen.clearPictures();
```



### 清除图片5～9范围

```
for( let i = 5; i < 10; i++ ) $gameScreen.erasePicture( i );
```

好像见过呢。没错，通过变量的应用，也能清除图片。

只需要把 `$gameSwitches.setValue( i, true )` 换成 `$gameScreen.erasePicture( i )` 而已。

因此，其他写法就省略了。

其他还能做什么，详情请参阅链接中的参考手册。

[参考链接::Game_Screen](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_Screen.md)

[参考链接:Game_Picture](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/Game_Picture.md)

## 结束语

以上就是对脚本应用的粗略介绍。

再往前深入的话，每个游戏所需的脚本大概会千差万别，所以接下来就只剩下普通的 js 解说了。

不限于角色和图片，全局变量中 `$gameXxxx` 系列是对象，而 `$dataXxxx` 系列则是数据库，这就是它们的区分。

从参考链接“[全局变量列表](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/global.md)”中寻找看起来像的东西并顺着链接查下去，我想应该能在一定程度上用起来

话虽如此，我还是觉得应该写一下“[rmmz 非官方 js 参考手册](https://github.com/tonbijp/RPGMakerMZ/blob/master/Reference/index.md)的阅读方法”之类的内容。

我自己也在想：“不先懂 js 的话，根本没法知道怎么读吧，这东西”。

虽然确实有“别那么随便地介绍这种需要前置知识的东西啊”这回事，但因为没有其他更合适的东西了。

因此我写了一篇名为从[ rmmz 开始的 js 入门](./script-js)的文章。

这样一来，我想大家就能大致了解参考手册的读法。了。希望能如此。

Let's enjoy 游戏制作人生！