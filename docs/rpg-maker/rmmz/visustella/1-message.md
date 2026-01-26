---
sidebar_position: 8
---

# Message Core 

[Message Core VisuStella MZ - Yanfly.moe Wiki](http://www.yanfly.moe/wiki/Message_Core_VisuStella_MZ#Introduction)



## 简介

Message Core 插件扩展并增强了 RPG Maker MZ 的信息功能，使游戏开发者能够自定义游戏信息系统的工作流程。
功能包括（但不限于）以下所有方面：

- 控制常规信息设置。
- 自动为关键词和/或数据库条目着色。
- 增加可用于执行新功能/效果的文本代码。
- 允许您实现自定义文本代码操作。
- 允许您实现自定义文本代码字符串替换。
- 调用宏系统以加快开发流程。
- 在“选项”菜单中添加“文本速度”选项。
- 为您的信息系统添加非常实用的自动换行功能。
- 根据您的喜好扩展选择流程。
- 启用/禁用以及显示/隐藏特定选项。

## 主要变更

### 暗化背景扩展

之前，当在“显示文本”事件中使用“暗化背景”时，其大小仅与信息窗口本身的宽度相同。这看起来非常难看，因为背景边缘生硬，而其他地方则呈现渐变效果。为了改善视觉效果，我们扩展了暗化背景，使其能够覆盖整个屏幕宽度。

### 扩展信息

[![MessageCore ExtendMessages.png](http://www.yanfly.moe/wiki/images/7/74/MessageCore_ExtendMessages.png)](http://www.yanfly.moe/wiki/File:MessageCore_ExtendMessages.png)

如果您决定扩展信息窗口的大小以显示更多行，可以通过串联“显示文章”事件来输入数据。只要有足够的行数，这些事件就会相互传递数据，并在同一个信息窗口中显示。

### 扩展选择列表

[![MessageCore ExtendChoices.png](http://www.yanfly.moe/wiki/images/f/fa/MessageCore_ExtendChoices.png)](http://www.yanfly.moe/wiki/File:MessageCore_ExtendChoices.png)

只需在同一缩进级别上连续添加多个选择列表事件，即可扩展选择列表。如果在同一缩进级别上，两个事件之间存在除选择列表选项之外的其他事件，则不会扩展选择列表。


## 文本语言切换信息

[![MessageCore LanguageSwitch0.png](http://www.yanfly.moe/wiki/images/thumb/3/3b/MessageCore_LanguageSwitch0.png/600px-MessageCore_LanguageSwitch0.png)](http://www.yanfly.moe/wiki/File:MessageCore_LanguageSwitch0.png)

自 Message Core 1.46 版本起，新增了文本语言切换功能。

“文本语言”功能允许玩家在游戏的不同语言之间切换，让世界各地的玩家都能体验您讲述的故事。
免责声明：这不是自动翻译工具。通过 VisuStella MZ Message Core 的“文本语言”功能进行的翻译需要游戏开发者手动输入。
自 Message Core 1.53 版本起，我们决定添加对 TSV 的支持。
这是因为我们经过研究后认为，CSV 格式默认使用逗号作为分隔符，限制了其使用范围，因此我们决定改用 TSV 格式，其默认分隔符为制表符空格，而制表符空格在 RPG Maker 文本中几乎从不使用。

---

### 如何启用切换功能

[![MessageCore LanguageSwitch1.png](http://www.yanfly.moe/wiki/images/a/ad/MessageCore_LanguageSwitch1.png)](http://www.yanfly.moe/wiki/File:MessageCore_LanguageSwitch1.png)

默认情况下，文本语言切换功能未启用。以下是启用方法：

1. 打开 Message Core 的插件参数设置
2. 插件参数 > 文本语言设置 > 启用切换？
3. 将“启用切换？”参数设置为“true”。
4. 根据需要调整其他设置。
5. 保存插件参数更改。
6. 保存游戏。

[![MessageCore LanguageSwitch2.png](http://www.yanfly.moe/wiki/images/2/26/MessageCore_LanguageSwitch2.png)](http://www.yanfly.moe/wiki/File:MessageCore_LanguageSwitch2.png)

现在，需要获取包含所有用于翻译游戏脚本文本的 CSV/TSV 文件。

1. 运行测试你的游戏。确保测试模式未被禁用。
2. 此时会弹出一个窗口，提示你创建语言 CSV/TSV 文件。
3. 点击“确定”，让插件自动完成操作。
4. 项目目录下的 /data/ 文件夹中将出现已生成的 Language.csv/tsv 文件。
5. 然后，插件会提示你重启游戏。

**重要提示！** CSV 文件分隔符必须使用分号` (;) `而不是逗号 (,)，以减少标点符号冲突。请记住这一点，因为大多数 CSV 编辑器默认使用逗号 (,) 而不是分号` (;) `作为分隔符。


---

### 如何编辑语言 CSV/TSV 文件

语言 CSV/TSV 文件的结构与普通的 CSV/TSV 文件相同，这意味着您可以使用 Microsoft Excel 或 Google Sheets 等程序对其进行修改。我们建议您使用其中任何一个程序来修改文本。

我们不建议您直接在记事本等程序中修改 CSV/TSV 文件，因为这些程序对逗号 (,) 等字符的处理方式存在问题，容易出错。

表格最初看起来会像这样：

```
    Key        English    Chinese    Japanese     Korean
    Greeting   Hello      你好       こんにちは    안녕하세요
    Farewell   Good-bye   再见       さようなら    안녕히
    Wow        Wow        哇         ワオ          와우
```

“Key”列指的是用于确定哪些行将插入到文本中的参考键。包含语言的列将使用该语言对应的短语。
您可以删除包含您不打算翻译到游戏中的语言的列。

---

### 注意事项

通过电子表格编辑器（[Microsoft Excel](https://www.microsoft.com/en-us/microsoft-365/excel) 或 [Google Sheets](https://www.google.com/sheets/about/)）向 CSV/TSV 文件添加文本时，需要注意以下几点。

---

#### 如何在 Google 表格中加载 CSV/TSV 文件

如果您正在使用 Google 表格，并且希望编辑 CSV 文件而不将所有分隔符转换为逗号，请按以下步骤操作：

1. 访问 ["sheets.google.com"](https://sheets.google.com/)
2. 创建一个“空白电子表格”
3. 选择“文件”>“导入”>“上传”> 选择在游戏项目 /data/ 文件夹中创建的 CSV/TSV 文件。
4. 对于“分隔符类型”，如果您使用的是 CSV 文件，请将其更改为“自定义”，并插入分号“;”。否则，如果您使用的是 TSV 文件，请选择“制表符”作为分隔符类型。
5.取消勾选“将文本转换为数字、日期和公式”

[![MessageCore CSV GoogleSheets.png](http://www.yanfly.moe/wiki/images/f/ff/MessageCore_CSV_GoogleSheets.png)](http://www.yanfly.moe/wiki/File:MessageCore_CSV_GoogleSheets.png)

### = 如何在 VS Code 中加载 CSV/TSV 文件

1. 访问 ["https://code.visualstudio.com/"](https://code.visualstudio.com/)
2. 下载并安装 VS Code
3. 打开 VS Code，然后转到“视图”>“扩展”
4. 搜索名为“Edit CSV”的扩展
5. 将 CSV/TSV 文件加载到 VS Code 中，并使用 CSV 编辑器查看
6. 点击右上角的“Edit CSV”按钮


#### 换行符

如果您想在翻译后的短语中插入换行符，请使用 `<br>` 文本代码。此代码最适合用于要传输到信息窗口或帮助窗口的文本。

#### 文本代码

您可以像往常一样插入文本代码，例如 `\C[2]`。但是，它们仅在支持文本代码的窗口中有效，例如信息窗口或帮助窗口。否则，文本代码将无法正确传输。

#### 分号（仅限 CSV 文件）

由于 CSV 文件的特性，我们使用分号` (;) `作为分隔符。因此，文本条目中不应使用分号。虽然有些句子可以使用分号，但并非所有句子都适用。如果您确实需要使用分号，请改用文本代码 `<semicolon>`。
```
例如：
“煎饼真好吃，<semicolon>蓬松又香甜。”
```

分号文本代码的其他变体包括 `<semi>` 和 `<semi-colon>`。`<semicolon>` 文本代码及其变体仅适用于语言 CSV 文件，在常规信息框中输入时会被忽略。

---

#### 宏和语言切换

对于同时使用文本宏和文本语言切换的用户，宏会在语言切换之前转换为文本，这样可以实现更好的文本过渡效果。

---

### 如何使用引用键

还记得“key”列和引用key吗？它们用于确定哪些行将插入到信息窗口以及几乎任何其他窗口的文本中。但是，这些键必须以特定的方式使用才能正常工作。

“文本代码”格式的工作方式如下。使用以下任一方式：

```
  \tl{keyName}
  \translate{keyName}
  \loc{keyName}
  \locale{keyName}
  \localize{keyName}
```

或者对于那些使用其他翻译插件但想要切换到 VisuStella MZ Message Core 翻译系统的用户：

```
  ${keyName}
```

例如，要使用语言 CSV 文件中创建的默认键之一：
```
  \tl{Greeting}
```

这将生成英文的“Hello”、中文的“你好”、日文的“こんにちは”和韩文的“안녕하세요”。
key名不区分大小写，并且会移除所有尾随空格，以确保 CSV/TSV 表格稳定，可以引用任何翻译后的文本。
您可以将这些语言“文本代码”插入到物品名称、技能名称等，以及攻击、防御等系统条目中。

---

### 武器类型、防具类型、装备类型、物品类别命名

您可能已经注意到，如果您决定使用` \tl{keyName} `来命名武器或其他数据库类型，游戏的其他部分会出现错误。不用担心，对于这些情况，您无需更改当前使用的数据库名称。直接打开 CSV/TSV 文件，并为该特定数据库名称插入一个新键即可。例如，装备类型“配件”将使用“配件”作为自动键来查找已翻译的短语。如果 CSV/TSV 文件中没有找到匹配项，则将使用数据库中的默认文本条目。

### 控制符

这一篇的大头是这个文本控制符，以后再回来写