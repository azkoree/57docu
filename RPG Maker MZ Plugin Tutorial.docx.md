# **Plugin Tutorial for RPG Maker MZ**



# **1.0 序言**

## **1.1 本教程的面向人群**

　The aim of this tutorial is to assist users in utilizing and developing scripts and plugins. These elements are essential for achieving advanced and efficient game development using RPG Maker MZ (abbreviated hereafter as "MZ").

　It is intended for users with a grasp and understanding of both the general flow of game production and the basic functions of either MZ or a previous PC version of RPG Maker. This tutorial will only provide a minimal level of explanation concerning JavaScript knowledge and syntax.

本教程旨在帮助用户使用和开发脚本及插件。这些要素对于使用 RPG Maker MZ（以下简称“MZ”）进行高级且高效的游戏开发至关重要。

本教程面向已掌握游戏制作流程以及 MZ 或之前 PC 版 RPG Maker 基本功能的用户。本教程仅提供关于 JavaScript 知识和语法的最简略讲解。

# **2.0 插件的使用**

## **2.1 什么是插件？**

　When using MZ, the term "plugin" refers to an additional program file that allows you to change a game's specifications and operations from the most basic level. It uses a JavaScript text file (abbreviated hereafter as "JS file"). 

MZ is composed of a number of JS files collectively called core scripts. By supplementing and changing the contents of these core scripts using plugins, you can change MZ's game specifications in all kinds of ways, such as moving window positions or even adding entirely new menu options.

在使用 MZ 时，“插件”指的是一个额外的程序文件，它允许您从最基本的层面上更改游戏的设置和操作。它使用 JavaScript 文本文件（以下简称“JS 文件”）。

MZ 由多个 JS 文件组成，这些文件统称为核心脚本。通过使用插件来补充和更改这些核心脚本的内容，您可以以各种方式更改 MZ 的游戏设置，例如移动窗口位置，甚至添加全新的菜单选项。

## **2.2 安装插件**

### 事前准备

* An IDE (for example, Visual Studio Code, Atom, Notepad++, etc.)  
* Web browser (Google Chrome or other browser used for viewing the internet)
* 一个IDE（例如vscode，Atom，notepad++等）
* 浏览器（chrome或其他可用的浏览器）

### **下载插件**

　Plugins range from files provided officially to those provided and sold by individuals. First, begin by acquiring the JS file in question.

　When obtaining a JS file over the internet, download it according to the standard methods specific to your browser. Do not change the filename unless provided with specific instructions to do so.

　The specific distribution method will depend on the creator. These various methods include placement on a service such as Dropbox, compression, or distribution through GitHub or as an individual JS file or sample project.

　Try opening the file you downloaded using a text editor. If the text appears in a garbled state, the file may not have downloaded properly.

插件种类繁多，既有官方提供的文件，也有个人提供并出售的文件。首先，你需要获取所需的 JS 文件。

从互联网获取 JS 文件时，请按照浏览器默认的下载方式进行下载。除非有明确的说明，否则请勿更改文件名。

具体的分发方式取决于创建者。这些方式包括上传到 Dropbox 等服务、压缩文件、通过 GitHub 分发，或者以单个 JS 文件或示例项目的形式分发。

尝试使用文本编辑器打开下载的文件。如果文本显示乱码，则说明文件可能未正确下载。

### **查看许可（使用规约）　**

　Before you start to use a plugin, check the license and terms of use. In many cases, this information is written on the distributor's website, within the JS file or an accompanying ReadMe file. Most licenses clarify the actions that are either permitted or forbidden.

在使用插件之前，请务必查看其许可协议和使用条款。通常，这些信息会写在分发商的网站上、JS 文件里或随附的 ReadMe 文件中。大多数许可协议都会明确规定哪些操作是允许的，哪些是禁止的。

### **Viewing the Plugin Manager Screen**

　First, place the JS file under the project's \[js/plugins/\] folder. Next, from MZ's editor, open the Plugin Manager (F10). You can also press the button indicated below.  
![][image1]  
　This will bring up a list of the plugins you have already installed for your project. As a new feature of MZ, we have introduced a checkbox on the left of the list. Now you can simply switch plugins ON/OFF. You can change the state of multiple plugins by shift-clicking a range of them and pressing SPACE.

![][image2]

　Warning messages will also now appear on the bottom of the screen. These are messages that are displayed when there is a strong possibility that a plugin will not function properly if you begin the game in that state.

### **Types of Warnings**

　Warning messages are of the following types, each of which requires the appropriate response:

* The plugin "AAA" may not support RPG Maker MZ.  
  This message will appear if, for example, you try to use a plugin created for the previous version, RPG Maker MV.  
  
* The plugin “AAA” requires the base plugin “BBB”.  
  This message will appear if you have not added the prerequisite base plugin.  
  To resolve this error, refer to Help or other appropriate instructions and install the base plugin.  
  
* The plugin “AAA” must be ordered before plugin "BBB."  
* The plugin "AAA" must be ordered after plugin "BBB."  
  For reasons such as preventing conflicts, the order in which plugins must be added may be specified.  
  To resolve this error, change the order as directed by the message.  
  
* The plugin “AAA” has been registered as a duplicate.  
  This message will appear if you have added and switched ON two or more of the same plugin on the Manager Screen.  
  There is no benefit to adding a plugin multiple times. To resolve this error, delete any extra plugins.  
  
* The plugin “AAA” cannot be loaded.  
  This message will appear if, for example, you deleted the actual file after adding the plugin from the Manager Screen. A load error will occur if you run the game in this state. To resolve this error, delete the plugin from the list or restore the file.

# **3.0 JavaScript快速入门**

## **3.1 引言**

　Scripts in MZ are a means of accessing the fundamental parts of a game's operations and specifications. As all game-related areas in MZ are implemented using the language known as JavaScript, scripts are also specified according to the syntax used by JavaScript.

　By mastering scripting, you can carry out game development at a much more advanced and efficient level than just constructing events through event commands.

在 MZ 中，脚本是访问游戏运行和规范底层机制的一种方式。由于 MZ 中所有与游戏相关的区域都使用 JavaScript 语言实现，因此脚本也遵循 JavaScript 的语法规范。

掌握脚本编写后，您可以进行比仅仅通过事件命令构建事件更高级、更高效的游戏开发。

### **Aim of This Chapter**

　This section is intended for anyone without experience using JavaScript. It provides an explanation that especially pertains to MZ and that concerns the minimal level of JavaScript knowledge and syntax required. Its ultimate aim is to help you master using the Script event command.

　So that you may reach this goal through minimal effort, we have omitted overly detailed explanations and refrained from rigorous descriptions in some areas. Please be sure to keep that in mind.

　Regardless of your level of experience with programming languages, we recommend that you have a grasp of MZ's basic specifications and methods for constructing events.

### **About JavaScript**

　JavaScript is a programming language that was originally intended for web browsers. Due to the introduction of Node.js, it has been applied to a wide range of uses in recent years, such as server-side processing.

　Although, as a result of this, it is now used in an abundance of informational publications and websites, the runtime environment and syntax will differ based on the application in use. If you copy code found at another location, such as a website, and attempt to run it using MZ, it will not work in some cases.

　Please be aware that, if you look at the JavaScript source on general websites with the aim of mastering scripts using MZ, you may be taking a fairly circuitous route.

### **Tip: Java and JavaScript are unrelated.**

　Although Java is primarily a programming language that is widely used for server-side processing, it has no relation to JavaScript.

　As it shares a similar name, be careful not to make a mistake when purchasing a book or searching the internet.

## **3.2 Start off by running a script\!**

　Generally speaking, in order to practically learn a programming language, you first need to build a runtime environment on which to execute code. Such an environment has already been prepared for you when you use MZ. After creating a project on MZ, try a quick test play.

　After the title screen appears, press F8. This should open a window that is separate from the game, which provides developer tools that will be especially helpful when developing or debugging a game using plugins.

### **Log Output**

　Developer tools provide a large number of functions. For now, start by selecting the Console tab. It should appear as shown below.  
![][image3]

　You can enter text on the white screen. First, try inputting the following statement.

console.log('Hello RPG Maker MZ');

![][image4]  
　This should produce the result shown above. Just like that, you have run JavaScript and verified the results\!

　The script you executed is a command that tells the console to display the string *Hello RPG Maker MZ*.

　As its name suggests, console.log is a command that logs a message to the output console, which allows you to check values and states at runtime.

　Perhaps there are users who will think, instead of using this type of tool, that they would rather run various scripts using the Script event command. However, we cannot recommend that method due to the following reasons:

* You cannot verify the runtime results using that window.  
* There is no input completion function (in the console, text suggestions appear automatically after you partially enter a string).  
* If the syntax is incorrect, an error will occur and the game will stop working.

　So, first, learn basic JavaScript syntax while outputting logs using developer tools, before aiming to use scripts in event commands.

### **Comments**

　The event command Comment makes it easy to write remarks about complex processing using an event command. There is also a function that corresponds to Comment in JavaScript.

　This function is itself called a "comment." If you write *//*, the subsequent string will become a comment; it will then be ignored when you run the program.

	// This text will be ignored when the program runs.  
	console.log('This text will be outputted.');

　 If you wish to define a comment spanning multiple lines, you can use a block comment as shown below.

	/\*  
	 \* If you wish to define a comment spanning multiple lines,  
	 \* you can use a block comment.  
	 \*/  
	console.log('This text will be outputted.');

　By making skillful use of comments, you can create a program that is easy to understand.

## **3.3 Variables**

　In MZ, there is a concept called a variable. From the event command Control Variables, it is possible to specify a name and freely assign or change a value. The same type of system is also found in JavaScript.

　In this chapter, this tutorial will explain the differences between variables in JavaScript and MZ and their varying methods of use.

### **Declaring a Variable**

　First, as opposed to variables in MZ, you must declare a variable when using JavaScript.  
　When declaring a variable, you convey to the program that you are defining a variable under a specified name. You cannot use a variable if it is not declared.

let aaa \= 0;

　In the above example, we are declaring that we will use a variable with the name of *aaa* and, at the same time, we are assigning it a value of *0*. Although a value of *0* is assigned automatically to an event command variable, unless an initial value is assigned to a JavaScript variable, it will have no value at all. More precisely, the special value *undefined* is assigned signifying that the variable has no defined value.

　*let* is a syntax-defined word that is required for making a declaration. In addition to *let*, there are a number of words and terms that are syntactically defined by JavaScript. These are collectively known as reserved words.

　For the variable name *aaa*, you can enter a name of your choosing. However, you cannot use certain text including reserved words, which this tutorial just introduced, and some symbols.

Uncaught SyntaxError: Identifier 'aaa' has already been declared

### **Tip: Semicolons at the End of Lines**

　If you take a good look at the scripts appearing so far, you will see that a semicolon (;) has been placed at the very end. Although this is a symbol used to explicitly express the end of the statement, the script will function normally even without the semicolon. Whether or not you use semicolons is entirely your own decision; either choice is perfectly fine. However, it is important to be consistent. It may cause confusion if you add them in some places but not others.

### **Tip: Methods for Declaring Variables Other Than *let***

　If you used scripts with the previous version, RPG Maker MV (abbreviated hereafter as "MV"), you will probably recall the reserved word *var*. Using the same method as with *let*, you can also declare valuables with *var*. Although declarations using *var* are also valid in MZ, it is actually a fairly old word. While using it will not result in any errors or harm to your program, when you reach the stage of creating your own plugins, differences will become evident in precise areas such as disparities in the scope (valid range) of variables.

　Use *let* unless you have a particular reason or point of focus that requires otherwise.

　There is also another reserved word for declarations, *const*. Perhaps you are concerned that, just for declaring variables, there are too many different types. It would be difficult to explain about *const* at this point, so we will save that for later. For now, just be sure to learn about *let*.

### **Calculating Values**

　From the event command Control Variables, in addition to assigning values, it is possible to conduct basic calculations such as addition and multiplication. Naturally, you can do the same for variables within JavaScript.  
　First, define a variable.

let x \= 1;

　Next, write the respective calculation in the manner shown below.

| Type | Script | Result | Shortened Script |
| :---- | :---- | :---- | :---- |
| Addition | x \= x \+ 1; | 2 | x \+= 1; |
| Subtraction | x \= x \- 1; | 0 | x \-= 1; |
| Multiplication | x \= x \* 2; | 2 | x \*= 2; |
| Division | x \= x / 2; | 0.5 | x /= 2; |
| Modulo | x \= x % 2; | 1 | x %= 2; |

　Then the variable *x* will store the result of the calculation. Enter *console.log(x);* in the console to check the value it contains. To execute the calculation, you can use either the script or the shortened script. So you can see that it is possible to control variables in the same way as when using the event command.

　Additionally, when adding or subtracting a value of *1*, you can shorten the statement in the following ways:  
x++;  
x--;  
　These are called the increment operator and decrement operator, statements frequently used in programming.

### **Tip: Two Points of Caution when Using Division**

　When carrying out division using the event command, the remainder would be dropped if the number was not divisible. However, JavaScript will not automatically round off or drop a remainder.  
　Also, when dividing by zero, the special value *Infinity* or *\-Infinity* will be returned, respectively, depending on whether the number being divided has a positive or negative value. This behavior can also be reproduced, in fact, when using the event command.

### **Types of Variables**

　When entering variables using the event command, you can only use a numerical value, unless using the Script operand which allows you to use strings. With JavaScript, you can also store other values in variables besides numbers. The following is a list of the most typical kinds of values:

* boolean value (true/false)  
* string  
* null  
* undefined  
* array  
* object  
* function


　A boolean value functions in the same manner as a switch when using an event command. When a variable is switched ON or OFF, that is expressed as either *true* or *false*, respectively.

let aaa \= true;

　A string is an arrangement of characters such as symbols, English letters, and Japanese letters. The beginning and end of a string are enclosed by either single quotes (',') or double quotes (",").

let aaa \= 'test mzあああ\!"\#$%';

　*null* expresses an empty state. It represents a different concept than the aforementioned *undefined*. It could be said that *undefined* expresses a state in which no value has been defined, while *null* expresses a state in which a value of nothing has been defined.

let aaa \= null;

　Array, object, and function variables are fairly complex, so they will be explained in later sections.

### **Arrays**

　Among the types of variables explained in the previous section, arrays and objects are somewhat complex. Using these variables, you can work with multiple values in an organized way.  
　An array is a variable that manages a group of values as a single entity.

let aaa \= \[1, 2, 3, 4\];

　To reference its contents, write a statement such as the following:

console.log(aaa\[0\]);

　The value *0* specified within the square brackets is called an index. It indicates which part of the array will be referenced. The values in the array itself, such as *1* and *2,* are called elements.

　The index for the leftmost element is the number 0, and increases in order to 1, to 2 and so on. In other words, when running the above script, the element at index *0* (*1\)* will appear.

　Arrays also possess a property called length. By referencing this property, you can acquire the number of elements in an array.

console.log(aaa.length);

Running this code will give us the value *4*.

### **Objects**

　So, when using an array, you could use numerical values as indexes and unify multiple values in one entity. To use strings as indexes, use an object instead. An object is similar to an associative array or structure in other languages. (Strictly speaking, to provide a slightly different explanation, there are formal associative arrays used separately in JavaScript. However, that has not been included in this section.)

```
let aaa \= {bbb: 1, ccc: 2, ddd: 3};
```

　With an array, you can reference values using an index. For an object, strings such as *bbb* and *ccc* are generally called *properties*.

　In a similar manner to an array, to reference an object’s contents, write a statement such as the following. When inputting a string, remember to enter single or double quotes at the beginning and end:

console.log(aaa\['bbb'\]);

　Running the above statement this will return *1*. When using an object, you can also reference properties in the following way:

console.log(aaa.bbb);

　With this method, you do not need to include brackets or quotes, though you cannot use symbols in the property name (with a few exceptions such as underscore).

　Referencing variables through properties using a period like this is a method frequently employed by the core scripts. Make sure you have a strong grasp of these basic points.

　In terms of the meaning of *aaa.bbb*, it references the property *bbb* from the object *aaa*.

### **Practical Application**

　In this section, a tutorial will show you how to run complex programs using the knowledge learned up to this point. Please make sure that you have gained a proper understanding of the material before you begin.

　Try to run the following script, but instead of just copying it, be sure to enter it directly yourself.  
```
let obj \= {prop1:0, prop2:1};  
obj.prop1 \+= obj.prop2;  
let propName \= 'prop3';  
obj\[propName\] \= 5;  
let num \= obj.prop3;  
console.log(obj.prop1 \+ obj.prop2 / num);
```

To explain what is happening in each line.

1. By declaring the variable *obj*, you will store a newly created object.  
2. To *obj*'s property *prop1*, you will add the value of *prop2*. The value *0 \+ 1*, or in other words *1*, is stored within *prop1*.  
3. You will declare the variable *propName* and store the string *prop3*.  
4. You will create a new property for the variable *obj*. The property's name becomes the value of the variable *propName*, or in other words *prop3*.  
5. To the variable *num*, you will assign *obj.prop3*, which was defined in the previous step. *5* is stored in *num* as a result.  
6. Finally, you will output the results of the calculation *prop1 \+ prop2 / num*. In the same manner as actual mathematics, you can combine multiple mathematical operations.

　The first point deserving special notice is step \#4. This is where you assign a variable to the property. In JavaScript, you can reference a property name using the value of a variable. 

　Next, we will discuss step \#6. When using the event command, only a single calculation could be executed per command. On the other hand, with JavaScript, you can conduct multiple calculations in a single operation in the same way as actual mathematics. When it comes to mathematics, you probably know that mathematical calculations are assigned an order of operations. For example, when conducting addition and multiplication, multiplication is calculated first.

　As a result, the calculation *1 \+ 1 / 5* will output *1.2*.

### **Tip: Input Completion**

　When you manually enter the above script, upon entering *obj* in the second line, a list like the one shown below should pop up.

　Known as input completion (or widely recognised as Intellisense to users of development environments like Visual Studio), through this function, the developer tools predict the text you might enter and provide suggestions. Using this functionality you can reduce input and syntax errors, so be sure to take advantage of it.

![][image5]

## **3.4 Control Structures: Conditional Branches**

　When constructing a complex event using MZ, the Conditional Branch command becomes absolutely essential. JavaScript also provides a method of notation that is equivalent to Conditional Branch: the *if* statement.

### **Conditional Branches Using *if***

　An *if* statement is the most basic structure that allows for some type of procedure to execute only when a condition is satisfied. The code enclosed by curly braces will only execute if the condition specified in the parentheses is satisfied:

```
* Structure  
  if (conditional expression) {  
    This procedure will execute if the condition is met.  
  }  
    
* Example  
  let aaa \= 1;  
  if (aaa \<= 1\) {  
    console.log('ok1');  
    console.log('ok2');  
  }
```

　A conditional expression is written within the parentheses. This expression needs to contain either a comparison operator or boolean value. (Be sure to review the variable types if you have forgotten them.) The following types of comparison operator may be used:

| Comparison Operator | Meaning |
| :---- | :---- |
| a \=== b | *a* and *b* are identical |
| a \!== b | *a* and *b* are not identical |
| a \>= b | *a* is greater than or equal to *b* |
| a \<= b | *a* is less than or equal to *b* |
| a \> b | *a* is greater than *b* |
| a \< b | *a* is less than *b* |

　The area encompassed by curly braces is known as a block. A block is a set of statements that will be run in the same scope. In addition to *if* statements, blocks will be used from here onwards, so be sure to learn this concept fully.

　Within the event command Conditional Branch, you will find the checkbox Create Else Branch. This can be reproduced within an *if* statement.

```
let aaa \= 1;  
if (aaa \<= 1\) {  
  console.log('ok1');  
  console.log('ok2');  
} else {  
  console.log('ng1');  
}
```

　Following the block for the *if* statement, you can enter *else* and create another block. The latter block will be executed if the condition is not met.

### **Tip: Block Indentation**

　When writing a block, insert a predetermined number of spaces or tabs as shown below. This is known as an indent. Some development environments will do this for you.  
if (aaa \<= 1\) {  
  console.log(‘This line will be indented.');  
}  
　Using indents will make it easier for humans to read the flow of the program. An indent is typically composed of a single tab, two double-byte spaces, or four single-byte spaces.  
　When creating events in RPG Maker, indents are also used for structures such as conditional branches and loops; if you’re already familiar with that structure it should be easy to apply that knowledge to these concepts.

### **Tip: Inexact Equality Operator**

　In other programming languages, *a \== b* is frequently used as the equality operator; this operator can in fact also be found in JavaScript. However, it can be problematic because if the types of the operands differ, the statement will still return *true* even if different things are being compared (like the number *1* and the string *'1'*).  
　For this reason, during MZ development, only *\===* (which is called the exact equality operator) is used in most cases. Don’t worry about remembering \== as you’ll likely never need it.

### **Logical Operators**

　We will now explain about more complex kinds of *if* statements. When using the event command, for procedures that could only be branched to if both *A* and *B* were satisfied, you may have placed nested conditional branches. You may also have written two conditional branches for procedures that could be branched to if either *A* or *B* were satisfied.

　With JavaScript, you can combine these branches in one statement. *A and B* is expressed as *A && B*, and *A or B* is expressed as *A || B*.

let a \= true;  
let b \= false;  
if (a && b) {  
  console.log('The conditions are not satisfied because, although a is true, b is false.');  
}  
if (a || b) {  
  console.log('The conditions are satisfied because, although b is false, a is true.');  
}

　Another type of logical operator, *\!*, expresses negation (often referred to as “not”). This returns a result that inverts a boolean value.

let a \= true;  
if (\!a) {  
  console.log('The condition is not satisfied because a is true and the result inverts that value.');  
}　

### **Tip: What about specifying variables other than booleans within conditions?**

　If you specify variables other than booleans or comparison operators within the conditional expression of an *if* statement, this will return the following types of results. Although this would be useful when checking for *null* within an array or object, it is not recommended when judging numbers or strings.

| Type | Example if false | Example if true |
| :---- | :---- | :---- |
| number | 0, NaN | variables other than that shown on the left (including negative values) |
| string | empty string ('') | variables other than that shown on the left (including the string *'0'*) |
| array, object | n/a | all variables (including empty arrays and empty objects) |
| null, undefined | all | n/a |

### **Conditional Branches Using Conditional Operators**

　Conditional operators (also known as ternary operators) are, simply put, a type of notation used to write branch processing within one line. They are also used frequently within MZ's core scripts.

* Structure  
  conditional expression ? expression if the condition is satisfied : expression if the condition is not satisfied;  
* Example  
  let aaa \= 1;  
  let bbb \= (aaa \=== 1 ? 2 : 3);  
  console.log(bbb);

　In the above example, the value assigned to *aaa* is *1*, so *2* will be assigned to *bbb*.

　You can also substitute conditional operators for the *if* statements used above. The benefit of a conditional operator is that it allows you to express a conditional expression within one overall expression.

　With MZ, you can also use scripts for mathematical formulas for skills and items. However, the entry field has only one row.

　In the following example, to the damage formula for a normal attack, a judgment based on a conditional operator has been added. Although it is probably an unfamiliar notation, the conditional expression *b.isStateAffected(5)* signifies the condition that the attack target is in the state represented by State ID\[5\].

a.atk \* 4 \- b.def \* 2 \+ (b.isStateAffected(5) ? 100 : 0);

## **3.5 Control Structures: Loops**

　The procedures conducted by the event commands Loop and Break Loop are also provided in JavaScript. The conditional branches discussed in the previous section and the loops in this section are implemented within almost all programming languages and not only JavaScript.

　As you may have noticed already, the event commands used within RPG Maker were originally created while referring to the variables, conditional branches, and other control structures that are found within programming languages.

### **Loops Using *while***

　The most basic loop procedure is a *while* statement. Using the event command, if you create a conditional branch within a loop in order to stop it, you will be unable to specify a closing condition for the loop. You can, however, designate a closing condition by using a *while* statement in JavaScript.

* Structure  
  while (conditional expression) {  
    This procedure will run repeatedly.  
  }  
* Example  
  let a \= 0;  
  while(a \< 10\) {  
    a++;  
    console.log(a);  
  }

　In the above example, as long as *a \< 10* is satisfied, the operations contained in the block will be executed repeatedly. This will provide a log output of numbers spanning from *1* to *10*.

### **Tip: Fear of an Endless Loop**

　What would happen if you specified a formula that returns *true* perpetually for the *while* statement's conditional expression? The answer is the loop's operations would continue to execute endlessly until the game freezes. The same result would also occur if using the event command Loop.

　In such a case, not only would it stop the game, it would also place a burden on your PC. Be sure to carefully discern whether or not there is a mistake present in the language specified for the conditional expression.

### **Loop Breaks**

　The procedure conducted by the event command Break Loop is also provided in JavaScript. It is known as a break.

let a \= 0;  
while(a \< 10\) {  
  a++;  
  console.log(a);  
  if (a \>= 5\) {  
    break;  
  }  
}

In this example, the loop was discontinued at the point it finished outputting numbers up to *5*.

### **Loops Using *for***

　A *while* statement is a structure that executes a procedure repeatedly on and on while a conditional expression is satisfied. A *for* statement, which this tutorial will now introduce, can be used when you have already decided how many times you want the loop to repeat from the beginning.

* Structure  
  for (initialization; conditional expression; increment expression) {  
    This procedure will run repeatedly.  
  }  
* Example  
  for (let i \= 0; i \< 5; i++) {  
    console.log(i);  
  }


　In the above example, this will provide a log output of numbers spanning from *0* to *4*. *i* is typically known as a counter variable. As this is a standard type of variable, you can select any name you like. However, *i* is often used here.

　You can also use *for* statements when we want to execute the procedures for an array repeatedly.

let aaa \= \[1, 3, 5, 7, 9\];  
for (let i \= 0; i \< aaa.length; i++) {  
  console.log(aaa\[i\]);  
}  
　  
　In the above example, this will provide a log output of all elements in the array in the order of *1*, *3*, *5*, *7*, *9\.*

### **Loops Using *for-in***

　In the last section, this tutorial introduced the concept of repeating an array's procedures. However, there is actually an easier way to notate that. If you wish to repeat the procedures for all elements in an array, use *for-in*.

* Structure  
  for (declare variable for index in array) {  
    This procedure will repeat.  
  }  
  
  let aaa \= \[1, 3, 5, 7, 9\];  
  for (let i in aaa) {  
    console.log(aaa\[i\]);  
  }


　Using *for-in*, the array's indexes, meaning numbers spanning from *0* to *4* in order, will be entered into the variable *i*. As a result, in the same manner as the example in the previous section, this will output all elements in the array, meaning *1*, *3*, *5*, *7*, *9\.*

　*for-in* can also be used for objects other than arrays.

* Structure  
  for (declare variable for property name in object) {  
    This procedure will repeat.  
  }  
* Example  
  let aaa \= {bbb:1, ccc:2};  
  for (let property in aaa ) {  
      console.log(aaa\[property\]);  
  }


　In the above example, the property names *bbb* and *ccc* are entered into the variable *property*. As a result, *1* and *2* will be outputted in the log. It is determined randomly whether 1 or 2 will be outputted first. Be sure to be aware of that point.

### **Loops Using *for-of***

　In the same manner as with *for-in*, using *for-of*, we can easily enter the notation for a procedure that will repeat for an array. The one point of difference in comparison to *for-in* is that, instead of indexes, the actual elements are stored for the variable.

* Structure  
  for (declare variable for element of array) {  
    This procedure will repeat.  
  }  
* Example  
  let aaa \= \[1, 3, 5, 7, 9\];  
  for (let data of aaa) {  
    console.log(data);  
  }

　As *for-of* is the more convenient of the two, it is used frequently within core scripts. However, as opposed to *for-in*, *for-of* cannot be used for an object.

## **3.6 Functions**

　As you read and decipher core scripts and master the use of scripts, functions are the most important concept you will come across.

　In a programming language, a function is something that allows you to easily call for multiple procedures in a united fashion. If you define within a function the procedures you want to run many times, by merely calling that function, you can then execute those procedures.

For the time being, you can consider this as a similar concept to a Common Event.

### **Defining a Function**

　In order to execute a function, first, you must define the function that will be called.

* Structure  
  function functionName() {  
      procedure you wish to execute  
  }  
  
* Example  
  function aaa() {  
      console.log(111);  
  }


　In the same way as with variable names, you can freely assign the function name. Likewise, you cannot use reserved words or symbols excluding a few exceptions.

　The fact is, if you make good use of scripts, you will not have many opportunities to define functions. That said, core scripts are actually an enormous collection of functions. At this point, the key thing to know about functions is that they are especially important to learning about scripts.

### **Calling a Function**

　The expression used to call a defined function is shown below.

* Structure  
  function name();  
* Example  
  aaa();


　In this way, we add parentheses after the function name and then call it. The majority of procedures written in the event command Script call a function. For this reason, be sure to properly remember this notation method.

### **Arguments**

　When calling a function, you can pass values such as numbers and strings to it. These values are known as arguments. In the function declaration, the variables that receive these values are called parameters. This concept may not be familiar if you're used to working with Common Event, so it might be a bit confusing at first. To understand arguments and parameters better, let's recall a function used in mathematics:

y \= f(x)

　Functions used in mathematics follow the line of thinking that *x* is for input and *y* is for output. An argument is equivalent to the value *x* expressed in the above example.

First, please take a look at an example.

* Structure  
  function function name (parameter(s)) {  
      procedure you wish to execute  
  }  
  function name (argument(s));  
* Example  
  function outputSum(bbb, ccc) {  
      console.log(bbb \+ ccc);  
  }  
  outputSum(10, 11);


　If you execute the example procedure, a log of *21* will be outputted. The steps involved in this procedure are as follows.

1. By calling the function *outputSum*, you pass the arguments 10 and 11\.  
2. Execution shifts to the *outputSum* function, where the *arguments 10* and *11* are stored in the parameters *bbb* and *ccc*, respectively.  
3. The value of *ccc* added to *bbb* is calculated, and the result, 21, is outputted in the *console log.*

### **Return Value**

　The return value is the result given when executing a function. Once again, recall that mathematical function.

y \= f(x)  
　  
　The above value *y* is the return value. Please look at this example.

* Structure  
  function function name() {  
      return value you wish to return  
  }  
  let aaa \= function name();  
* Example  
  function getHundred() {  
      return 100;  
  }  
  let bbb \= getHundred();  
  console.log(bbb)

　When executing the example function *getHundred*, the fixed value *100* will be returned as the return value, meaning *100* will be stored in the variable *bbb*.

### **Storing Functions in Variables**

　When this tutorial explained about types of variables, perhaps you remember that one type was called a function. In JavaScript, you can enter defined functions within a variable.

* Structure  
  let function name \= function() {  
     procedure you wish to execute  
  }  
  function name();  
  
* Example  
  let aaa \= function() {  
     console.log(1);  
  }  
  aaa();

　When specifying an argument, use the following structure.  
let aaa \= function(bbb) {  
   console.log(bbb);  
}  
aaa(1);

　As you are able to define a function within a variable, you are also able to define it within an object's property. This is an especially important point. A function that is defined as an object's property is specially referred to as being a "method." However, in this section, this tutorial will consistently use the term "function" throughout.

let aaa \= {};  
aaa.bbb \= function() {  
   console.log(1);  
}  
aaa.bbb();

　So, if you are able to store functions within variables, what benefits might that bring? In truth, when using the event command Script, you are given almost no opportunity to enter functions within variables. Nevertheless, if you correctly understand this concept, when calling functions defined in core scripts, you will be able to accurately understand why they are written in such a way.

　Having read this section, be sure to keep this concept in mind.

### **Tip: Arrow Functions**

　When storing functions within variables or specifying them for arguments, you can use a simplified notation method known as an arrow function.

let aaa \= (bbb) \=\> {  
   console.log(bbb);  
}  
aaa(1);

　By using the *\=\>* symbol, you can define the function with a smaller number of characters. If there is only one parameter, you can also omit the parentheses.

　Also, if you are able to express the contents of a function within one expression, you can omit the block (braces) or the use of *return* to return a return value.

　Functions defined through arrow functions handle the execution agent *this* differently than normal functions. At this stage, it would be difficult to explain those differences, so this tutorial will not include that information.

## **3.7 Using Core Script Functions**

　MZ core scripts are a massive collection of functions. These functions are defined in the form of objects' properties.  
　In this section, you will learn the methods for using core scripts' functions.

### **Acquiring Variables**

　The script used to acquire the contents of game variables is shown below. Thanks to the developer tool, when you input this text up to *$game*, *$gameVariables* will appear as a suggestion.

	$gameVariables.value(1);

　First, take a look at *$gameVariables*. As an object that handles game variables, it has been defined as a core script. Next, there is *value*. This is a function that is a property owned by *$gameVariables*. It has also been defined within the core scripts.

　The argument *1* is the variable number. In other words, when running the above script, this will return the value of variable number *1* as the return value.

　If there is any part of this explanation that you are unable to understand, be sure to read the section about functions one more time.

### **Tip: Global Variables**

　Variables that can be referred to anywhere within a program are known as global variables. A number of these have been defined within the core scripts. Including *$gameVariables*; almost all of the variables that begin with the symbol *$* are global variables.

　Within JavaScript, variables declared on the top level (area not within some kind of function block) are treated as global variables. (Variables that are used without being declared are also considered global variables. However, if you try to use global variables by utilizing this method, this may cause an error in an unrelated area. It is therefore an exceptionally risky method.)

　Placing a *$* at the beginning of the variable is a means of clarifying that it is a global variable.

### **Setting Variables**

　Next, the tutorial will explain scripts for setting the values within game variables.

	$gameVariables.setValue(1, 3);

　Same as *value*, *setValue* is also a function possessed by *$gameVariables*. This has two parameters. The first parameter contains a variable number and the second holds a set value.

　After you execute a script for setting a value, if you run a script for reacquiring the value, you should be able to confirm that the set value has been reflected.

### **Database Acquisition**

　MZ possesses enormous databases. All of the values entered here are stored in the global variable *$dataXXX*.

　As one example, try to run the following script.

	$dataActors\[1\].name;

　When you run the script, it should return the name of the first actor recorded in the database *Actors*. *$dataActors* is an array variable defined by a core script. It is an object with indexes that store a database ID and elements that store the value recorded for actors in the database. The element at index *0* is *null*, so be careful in that regard.

　*name* is one of the properties owned by the object corresponding to each respective *$dataActors* element. It stores the value entered for a name.

　Other databases are also defined based on the same essential ideas. A list of those databases appears below:

| Variable Name | Definition |
| :---- | :---- |
| $dataActors | actors |
| $dataClasses | classes |
| $dataSkills | skills |
| $dataItems | items |
| $dataWeapons | weapons |
| $dataArmors | armor |
| $dataEnemies | enemy characters |
| $dataTroops | enemy groups |
| $dataStates | states |
| $dataAnimations | animations |
| $dataTilesets | tilesets |
| $dataCommonEvents | common events |
| $dataSystem | system, language |
| $dataMapInfos | map tree data |
| $dataMap | map data |

　As it would not be possible to cite all of the properties of each database at this time, you will find a separate reference here. By consulting the reference, you can obtain all of the information included in the databases.

[https://forums.rpgmakerweb.com/index.php?threads/rpg-maker-mz-script-call-reference.122501/](https://forums.rpgmakerweb.com/index.php?threads/rpg-maker-mz-script-call-reference.122501/)

### **Controlling Game Objects**

　There are many variables handled during gameplay other than game variables. These include party members' HP, possessed items, and enemy characters' remaining HP. As opposed to databases, such values change based on the state of progress in-game. In this section, this tutorial will use the term "game objects." Game objects are stored in the variable *$gameXXX*.

　*$gameVariables*, in which game variables have been entered, is one version of this variable.

| Variable Name | Data Contained | Contains Saved Data (Y/N) |
| :---- | :---- | :---- |
| $gameTemp | Data you want to store temporarily | N |
| $gameSystem | System settings data | Y |
| $gameScreen | Data pertaining to screen effects | Y |
| $gameTimer | Data pertaining to timers | Y |
| $gameMessage | Data pertaining to messages and options | N |
| $gameSwitches | Switch data | Y |
| $gameVariables | Variable data | Y |
| $gameSelfSwitches | Self switch data | Y |
| $gameActors | Data pertaining to all actors | Y |
| $gameParty | Data pertaining to parties | Y |
| $gameTroop | Data pertaining to enemy groups | N |
| $gameMap | Data pertaining to maps | Y |
| $gamePlayer | Data pertaining to players | Y |
| $testEvent | Data pertaining to event tests | N |
| DataManager | Set of functions handling the loading of databases | N |
| ConfigManager | Set of functions handling the setting of options | N |
| StorageManager | Set of functions handling file input/output | N |
| FontManager | Set of functions handling font files | N |
| ImageManager | Set of functions handling the loading of images | N |
| EffectManager | Set of functions handling particle effects | N |
| AudioManager | Set of functions handling the playing of background music and other audio | N |
| SoundManager | Set of functions handling the playing of system sound effects | N |
| TextManager | Set of functions handling language | N |
| ColorManager | Set of functions handling system colors | N |
| SceneManager | Set of functions handling scene controls | N |
| BattleManager | Set of functions handling all aspects of battles | N |
| PluginManager | Set of functions handling plugins | N |

　Within the following reference, you will find a compilation of the specific methods for obtaining data by means of each object.  
[https://forums.rpgmakerweb.com/index.php?threads/rpg-maker-mz-script-call-reference.122501/](https://forums.rpgmakerweb.com/index.php?threads/rpg-maker-mz-script-call-reference.122501/)

　The game objects included in the above table can be broadly divided into two categories: objects known as *$gameXxx* and objects named *XxxManager*.

　*$gameXxx* retains functions and data in a combined fashion. For example, *$gameParty* holds data pertaining to the current party, and at the same time, provides a function that adds members to the party.

  On the other hand, as a general rule, *XxxManager* only provides a function. As demonstrated in the table, these objects are divided by use and organized so that, for example, images are loaded by *ImageManager* and sound is loaded by *AudioManager*.

### **Tip: Object Orientation**

　If you are someone with an interest in scripting, you probably have heard at least once about object orientation. Although it would be difficult to explain about object orientation in a concise manner, you can say that it is the handling of related functions and data in a combined fashion, as seen with *$gameXxx*. During object orientation, the function itself is known as a method.  
　As the data is hidden as a general rule, it can only be handled externally by means of a method. The method will determine the manner in which the data will be handled.  
　You do not necessarily need to know about this approach when dealing with scripts. However, the more you need to carry out programming design, there may come a time when you attempt to make a large plugin. That is when you should know about object orientation.

## **3.8 MDN Web Docs**

　Up to this point, this tutorial has explained the basic structures found in JavaScript in quick fashion. Naturally, the tutorial has not covered everything there is to know about JavaScript. 

If you wish to learn about the makeup and specifications of JavaScript, MDN (Mozilla Developer Network) Web Docs are recommended. It is a thorough collection of specifications and technical information pertaining to web development technology including JavaScript.　

	[https://developer.mozilla.org/ja/docs/Web/JavaScript](https://developer.mozilla.org/ja/docs/Web/JavaScript)

　As these docs are not specifically intended for MZ, it goes without saying that all of this information will not be applicable. However, if you have come to a dead end while you are learning JavaScript, you can surely find the hint you need to solve your problem if you search therein.

## **JavaScript Built-in Functions**

　JavaScript provides a large number of functions that have been predefined to allow for the efficient handling of arrays and strings. Although this tutorial would be unable to present all of those functions herein, it will introduce a number of functions that are particularly useful when dealing with scripts.

　In terms of the other functions available, that information is compiled within the aforementioned MDN Web Docs.　

### **Arrays**

　Here, you will find explanations of functions that are frequently employed when dealing with arrays. To call an initialized variable, you can use *\[\]*.

	let aaa \= \[\];  
	aaa.push(1);

　A list of these functions appears on the page linked below.  
[https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global\_Objects/Array](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array)

　Many arrays can be found within the data defined by core scripts. If you gain a mastery of the types of array functions and their methods of use, this will prove exceptionally helpful in writing efficient scripts.

* Addition and Extraction of Elements

　These are functions for adding or extracting elements at the end or beginning of an array.

| Function | Definition |
| :---- | :---- |
| push | Adds an element to the end of the array |
| pop | Extracts and returns an element from the end of the array |
| unshift | Adds an element to the beginning of the array |
| shift | Extracts and returns an element from the beginning of the array |

* Repetition for All Elements in an Array

　These are functions that can be used if you wish to execute the respective procedures for all elements within an array. A distinguishing feature of these functions is that they specify a function for an argument and pass the elements of an array to that function's argument. As it would be difficult to convey this concept with a verbal explanation, please look at this example.

	let aaa \= \[1, 2, 3\];  
	aaa.forEach(item \=\> {  
	    console.log(item); // 1, 2, 3 will be outputted in order  
	        });

　These functions can be used in place of the *for* statements explained earlier. If you utilize them properly in line with their intended use, you will be able to write easy-to-read scripts that have very few bugs. These functions are also used frequently within core scripts, so be sure to remember them.

　Additionally, these functions work well in tandem with arrow functions. Be sure to master them together with the method for writing arrow functions.

| Function | Definition |
| :---- | :---- |
| forEach | Executes the function passed to an argument for all elements within an array |
| map | Returns a new array containing elements comprised of the return values of a function passed to an argument |
| filter | Returns an array that only includes elements with a return value of *true* from a function passed to an argument |
| find | Returns the first element with a return value of *true* from a function passed to an argument |
| findIndex | Returns the first index with the return value of *true* from a function passed to an argument |
| some | Returns *true* if *true* is returned from even one of the return values from a function passed to an argument |
| every | Returns *true* if *true* is returned from all of the return values from a function passed to an argument |
| reduce | Consolidates the array into a single value, using a function passed to an argument |

　*reduce* is fairly complicated, so this tutorial will not include a full explanation in this section. An in-depth explanation is provided in MDN Web Docs.

* Other Functions

　JavaScript provides a large number of other functions that are useful when dealing with arrays.

| Function | Definition |
| :---- | :---- |
| concat | Returns a new array consolidating values or arrays specified in arguments |
| includes | Returns *true* if the value specified in an argument is contained within an array |
| join | Returns a string consolidating all elements in an array using the separator string specified in an argument; commas will be used if the separator string is omitted |
| splice | Allows you to delete or insert array elements by specifying an index; specify an index in the first argument, the number of values to delete in the second argument, and the elements to insert in the third argument and beyond |

### **Math**

　*Math* modules are a set of functions in which the functions and constants used in mathematics are defined. As opposed to the arrays described in the previous section, they are not used in relation to variables they have defined. They call a *Math* function that has been defined in a fixed manner, such as *Math.abs*.

　This is fairly similar to the core script *XxxManager*.

	let aaa \= Math.abs(-100);

　A list of these functions appears on the page linked below.  
[https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global\_Objects/Math](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Math)

　From among these *Math* modules, this section will explain about the functions that are used by core scripts and for mathematical formulas dealing with areas such as skills.

| Function | Definition |
| :---- | :---- |
| Math.abs(n) | Returns the absolute value of the number *n* |
| Math.ceil(n) | Returns the smallest integer exceeding the number *n*; can be used for operations such as rounding up a decimal point, but not for designating a negative value for an argument |
| Math.floor(n) | Returns the greatest integer not exceeding the number *n*; similarly, can be used for operations such as rounding down a number, but not for designating a negative value for an argument |
| Math.round(n) | Returns an integer rounding off the number *n* |
| Math.trunc(n) | Returns the value of number *n* with the decimal point discarded; can be used to round down a number more expressly in comparison to *floor*; *floor* is used more often by core scripts |
| Math.max(n, m...) | Returns the greatest number among numbers specified in an argument; allows you to specify how many numbers you want in the argument |
| Math.pow(n, m) | Returns the value of number *n* to the power of *m* |
| Math.randomInt(n) | Returns a random integer within a range from *0* to *n-1*; this function was added, in fact, by core scripts and is not written about in MDN |

### **Strings**

　Here, this section will explain about functions that are frequently employed when dealing with strings. Just like arrays, strings are often used by core scripts. If you gain a grasp of the most convenient functions, this will prove helpful when writing scripts.

	let aaa \= 'AAAA';  
	let bbb \= aaa.toLowerCase();

　A list of these functions appears on the page linked below.  
[https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global\_Objects/String/toLowerCase](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase)

　A list of frequently used functions appears below.

| Function | Definition |
| :---- | :---- |
| includes | Returns *true* if the string specified in an argument is contained therein |
| toLowerCase | Returns a new string that is a lowercase letter version of the string |
| toUpperCase | Returns a new string that is an uppercase letter version of the string |
| substring | Returns a string that is a portion of the original string spanning from a starting position to an ending position specified in arguments |
| replace | Replaces the string specified in the first argument with the string specified in the second argument |
| split | Returns strings after splitting them into an array, using the character (or characters) specified in an argument as a separator string |

# **4.0 Making a Plugin**

　In this chapter, this tutorial will provide information that will help you get started in actually creating a plugin by making good use of the JavaScript knowledge you gained from the previous chapter.

## **4.1 Preparations Conducted Before Making a Plugin**

### **Editor Installation**

　Plugins are principally written in JavaScript. As a plugin file contains a text format, it is possible to develop it through a commonly used notepad application or text editor. However, it is recommended that you prepare a dedicated editor specially designed for JavaScript development.

　If you search for a dedicated editor, you will find many articles that provide comparisons. Choose whichever editor meets your preferences. It is a good idea to refer to newer articles in terms of when they were posted.

　A dedicated editor will possess the following kinds of features.

* Code completion (after you write code partially, predicts and suggests the subsequent notation)  
* Static analysis (provides an advance warning regarding notation that may cause a compilation or runtime error)  
* Formatter (conducts automatic formatting for indents and other aspects of coding according to rules set beforehand)  
* Debugger (stops script execution during runtime, and checks variables or runs code line by line)

　Plugin creation is a complex and delicate type of work. By making use of these editor functions, you can proceed in an easy and efficient manner.

### **File Creation**

　As you probably know if you have already used plugins, plugin files are placed in the project folder \[js/plugins/\]. Now, create a new JS file.

## **4.2 Deciphering an Official Plugin**

　There are, of course, various kinds of notation found within plugins. Using the official plugin *TextPicture.js* as an example, this tutorial will now explain about standard plugin notation methods.

### **Using Functions to Enclose the Entire Plugin**

　Looking at the implementation of the example plugin, you can see that, excluding comments, almost all procedures are contained within the following written structure.

	(() \=\> {  
	// All procedures are written here.  
})();

　Although it may look complicated with so many brackets being used, what this is simply doing is defining functions and executing them therein. There are two reasons why you expressly create functions and write procedures to allow for immediate execution.

* This ensures that the variables defined in the plugin will not affect other plugins.  
* This allows for *use strict* to be utilized.

　As explained in the previous chapter, when you declare a variable outside of a function, it becomes a global variable. As global variables can be referenced from all areas including other plugins, it may cause conflict if you define the same global variable using multiple plugins. [Keep in mind that if you decide to use IIFE, you also can not make an addon to your plugin.](https://forums.rpgmakerweb.com/index.php?threads/how-important-is-iife-in-rmmv.106760/) 

　As a basic rule, unless a global variable is truly necessary, you should not define it as such without good reason. When you define a variable within a function, you can limit its scope (valid range) to within that plugin only.

　Although *use strict* has not been included in the official plugin used as an example, it is recommended that you use it because, when you write it, it will tell you beforehand about any notation likely to cause a bug. While this method of use may seem somewhat unusual, you will define only the string *use strict* at the beginning of the function, as shown below.  
　  
(() \=\> {  
    'use strict';  
    // do something  
})();

　For example, if you try to use a variable without declaring it, it would then be treated as a global variable. If enabled, *use strict* would stop that from proceeding because it has been judged as an error.

### **Writing Help Comments**

　Next, please look at the plugin example's comment area. In an MZ plugin, an area beginning with */\*:* is used for special comments. Within the comments, you will also see a number of notations beginning with *@*. These are read and analyzed as help information within MZ's editor, and are called annotations.

/\*:  
 \* @target MZ  
 \* ….  
 \*/

　There are many kinds of annotations. This tutorial will explain more about them in the next chapter.

### **Redefining Existing Methods**

　This is an explanation about the area used for implementation. Previously, we conveyed that core scripts are a massive collection of functions. By redefining the functions defined by core scripts, plugins allow you to change how a game operates in MZ.

　The following presents a basic way to write a redefinition.

const \_Game\_Picture\_show \= Game\_Picture.prototype.show;  
Game\_Picture.prototype.show \= function() {  
    \_Game\_Picture\_show.apply(this, arguments);  
    // do something  
};

　First, in the initial line, this declared the variable *\_Game\_Picture\_show* and assigned the core script function *Game\_Picture.prototype.show*. Next, in the second line, this gave a new definition to the function *Game\_Picture.prototype.show*.

　Finally, in the third line, this executed the function assigned to the variable *\_Game\_Picture\_show*. *apply* is a function (method) used to execute a function assigned to a variable.  
　  
　In terms of what will be carried out through this chain of procedures, after calling the original procedure of the core script function *Game\_Picture.prototype.show*, it has newly introduced the procedure that the plugin creator wants to add. While repeatedly redefining functions in this way, you can create plugins.

### **Tip: Functions Used to Call Functions**

　When this tutorial just explained about the function *apply*, you probably wondered why there are no parentheses used when executing the function. Perhaps you could also execute it using *\_Game\_Picture\_show()*. However, by doing so, an error would occur for one particular reason.

　Unfortunately, as an ample understanding of JavaScript and object orientation would be required to comprehend that reason, that information has not been included here.

### **Defining Plugin Commands**

　In MZ, the specifications for plugin commands have been upgraded. When using MV, you can directly input command names and arguments. With MZ, you can define the data for command names and arguments using annotations, following the same notation methods as used for parameters.  
![][image6]  
　You can write actual command procedures in the following manner.

PluginManager.registerCommand("plugin name", "command name", args \=\> {  
    // Procedures run when executing a command are written here.  
});

　This specifies the plugin name in the first argument, the command name in the second argument, and the function that will be called when executing the command in the third argument. Within the argument *args*, the function for the third argument, the parameters specified when calling the command are stored in an object format. In the previous version, MV, they were passed using an array. So, that too has changed.

　In the example plugin, this concept is used in the following manner.

const pluginName \= "TextPicture";  
let textPictureText \= "";

PluginManager.registerCommand(pluginName, "set", args \=\> {  
    textPictureText \= String(args.text);  
});

　If you would like to call a method of *Game\_Interpreter*, after writing the function without using an arrow function, you can call it by entering *this*.

PluginManager.registerCommand("plugin name", "command name", function(args) {  
    this.character(0);  
});

### **Tip: Closures**

　During command processing for the plugin example, this section rewrote the value of the variable *textPictureText* that was defined outside of the function. Although it might seem strange at first glance, this has come into effect by means of a structure known as a closure.

　While the scope of *textPictureText* falls within the range of the block defined, that also includes what is contained within a nested function. That is because, with this concept, the scope (lexical scope) is determined at the point a function is defined.

　Regardless of the structure itself, this concept is very useful when creating plugins.

### **Tip: When to Use *let* or *const***

　The variable *textPictureText* found in the plugin example was defined using *let*, while *pluginName* was defined using *const*. Although *const* can be used when declaring a variable in the same way as *let*, as opposed to *let*, it cannot reassign values. You define *textPictureText* with *let*, because you want to reassign its value.

　Core scripts use *const* as a general rule, and employ *let* only when looking to reassign a value. By using these words appropriately in this manner, it becomes easier for a code creator to convey their intentions.

### **Object Creation**

　The following type of notation appears within the function *createTextPictureBitmap*.

const tempWindow \= new Window\_Base(new Rectangle());

　*new* is a word you will use if you want to create an object. This tutorial previously explained that you write the following type of notation when creating an object.

	const tempWindow \= {};

　If created using *{}*, an empty object will be generated. On the other hand, when creating an object using *new*, to put it simply, you will generate an object in a state in which its properties and functions are defined according to an already determined blueprint.

　In the above example, as it has specified *Window\_Base* as the blueprint, it will create *tempWindow* in a state in which its functioning as a window has been prepared from the start.

　Although this tutorial has explained that core scripts are a collection of functions, it might actually be more appropriate to say that they are a collection of these kinds of blueprints. *new* is also used frequently within core scripts, so be sure to learn how to use it at this time.

　During object orientation, these blueprints are known as classes.

### **Basic Explanation about Implementation**

　Following everything this tutorial has covered up to this point, you can finally learn about the basic implementation of *TextPicture.js*. This plugin displays a specified string as a picture using a plugin command. Now, this section will explain what is happening when it is executed.

　First, look at plugin command implementation. Here, after executing the command *set*, it has saved the string that it wants to be drawn as a picture to the variable *textPictureText*.

let textPictureText \= "";

PluginManager.registerCommand(pluginName, "set", args \=\> {  
    textPictureText \= String(args.text);  
});

　Next, add that to the picture display procedure. *Game\_Picture.prototype.show* is used for the method displaying the picture. Even if you did not know about its specific implementation, you could probably understand what it does just from its name.

const \_Game\_Picture\_show \= Game\_Picture.prototype.show;  
Game\_Picture.prototype.show \= function() {  
    \_Game\_Picture\_show.apply(this, arguments);  
    if (this.\_name \=== "" && textPictureText) {  
        this.mzkp\_text \= textPictureText;  
        this.mzkp\_textChanged \= true;  
        textPictureText \= "";  
    }  
};

　Through the procedures added now, if the picture name is blank (image specified as *n/a*) and the plugin command has been executed, the string to be drawn will be retained and a flag will be set.

　This would then point to the result that the picture has not been drawn at the present time. This can happen because, within the core script, the class *Game\_Picture* holds the state of the picture, while the class for the actual picture image *Sprite\_Picture* exists separately.

　When using the class for the actual picture image, this monitors the state of *Game\_Picture* for each frame. Not limited to this class, there is a method with the name of *update* that provides many possibilities in that it checks and updates the state of the picture as each frame is executed.

const \_Sprite\_Picture\_updateBitmap \= Sprite\_Picture.prototype.updateBitmap;  
Sprite\_Picture.prototype.updateBitmap \= function() {  
    \_Sprite\_Picture\_updateBitmap.apply(this, arguments);  
    if (this.visible && this.\_pictureName \=== "") {  
        // This procedure judges whether it is necessary to draw the picture.  
    } else {  
        this.mzkp\_text \= "";  
    }  
};

　The actual judgment procedure is a little long, so please check the code. To simply explain its implementation, it monitors the contents of *Game\_Picture* and, if judged to be necessary, executes the creation or destruction of the picture.

　Creation or destruction are implemented respectively through the following functions. If everything operates correctly, destruction will not necessarily be needed. However, as image objects use a considerable amount of memory, if you destroy the picture at the moment it is no longer needed, you can improve performance.

createTextPictureBitmap  
destroyTextPictureBitmap

### **Tip: Sprites and Bitmaps**

　Although this section just explained that *Sprite\_Picture* is a class for the actual picture image, more precisely, it is like the box in which the image is placed. This box is called a sprite. The class for the image itself is called a bitmap. A sprite has a property known as *bitmap*, in which a bitmap object is stored.

　A sprite holds information such as an image's display position, magnification, and color tone, while a bitmap simply holds color information for each X/Y coordinate.

## **4.3 Explanation about Annotations**

　Many kinds of annotations have been defined in MZ's help comments. This section will explain what is set in an annotation based on its type.

### **All Plugins**

　Among the annotations used for all plugins, many of them must be set if you are to create a plugin. Be sure to properly remember how to use them.

| Annotation | Definition |
| :---- | :---- |
| @target | "MZ" is written here as a fixed notation; required for making a distinction with plugins made for RPG Maker MV |
| @plugindesc | The plugin's title; text written here will be displayed on a list on the Manager Screen |
| @author | The plugin's creator; displayed on the Manager Screen |
| @help | Text explaining detailed methods for using a plugin; displayed on the Manager Screen |
| @url | The plugin distributor's URL; displayed as a link on the Manager Screen, allowing for the URL for accessing the distributor to be specified |

### **Plugin Parameters**

　Plugin parameters are functions that allow plugin users to set values of their choosing. The following is an example of their settings.

\* @param paramName  
\* @text parameter name  
\* @desc parameter description  
\* @default   
\* @type number

| Annotation | Definition |
| :---- | :---- |
| @param | Name of the parameter; used as a property name when acquiring the contents of a parameter through the plugin's implementation area; written at the very top of the annotation defining parameter contents |
| @text | Display name of the parameter; displayed on the screen where the parameter is inputted |
| @desc | Detailed explanation of the parameter; displayed on the screen where the parameter is inputted |
| @default | Value set automatically when the plugin is turned ON (Please note that the value is not set automatically when the parameter is empty.) |
| @type | Data determining the parameter's type; changes the input dialog's UI based on the value specified here; when specifying *number*, for example, provides a parameter for which only numbers can be entered |
| @parent | Allows you to specify a parameter acting in a parent role; through the assignment of parent-child relationships, enables the construction of parameter trees |

　Out of these annotations, *@type* probably requires the most detailed explanation. Based on the type specified using *@type*, the dialog's contents will change. A plugin will become significantly easier to use if you specify the appropriate types.

　The following is a list of the different types specified in *@type*.

| Type | Definition | Value Set |
| :---- | :---- | :---- |
| string | Brings up a standard string input field without any particular restrictions | inputted value |
| multiline\_string | Brings up a string input field in which multiple lines can be entered | inputted value |
| file | Brings up a dialog for selecting a file for an image or sound, etc.; the file selected here will not be subject to the function deleting unused assets | selected file name (with no extension) |
| number | Brings up a field in which only numbers can be entered | inputted value |
| boolean | Brings up an ON/OFF radio button | true/false |
| select | Brings up a pull-down list | selected option's *@value* or *@option* |
| combo | Brings up a combo box | selected option's *@option* |
| actor | Brings up a dialog for selecting an actor from the corresponding database | ID of the choice selected |
| class | Brings up a dialog for selecting a class from the corresponding database | ID of the choice selected |
| skill | Brings up a dialog for selecting a skill from the corresponding database | ID of the choice selected |
| item | Brings up a dialog for selecting an item from the corresponding database | ID of the choice selected |
| weapon | Brings up a dialog for selecting a weapon from the corresponding database | ID of the choice selected |
| armor | Brings up a dialog for selecting an armor piece from the corresponding database | ID of the choice selected |
| enemy | Brings up a dialog for selecting an enemy character from the corresponding database | ID of the choice selected |
| troop | Brings up a dialog for selecting an enemy group from the corresponding database | ID of the choice selected |
| state | Brings up a dialog for selecting a state from the corresponding database | ID of the choice selected |
| animation | Brings up a dialog for selecting an animation from the corresponding database | ID of the choice selected |
| tileset | Brings up a dialog for selecting a tileset from the corresponding database | ID of the choice selected |
| common\_event | Brings up a dialog for selecting a common event from the corresponding database | ID of the choice selected |
| switch | Brings up a dialog for selecting a switch | ID of the choice selected |
| variable | Brings up a dialog for selecting a variable | ID of the choice selected |
| string\[\] | Brings up a dialog in which multiple strings can be entered; even if not a string, all entries will be included in an array if you place *\[\]* on the end | \["input value", "input value"\] |
| struct\<type name\> | Brings up a dialog allowing for entry within multiple fields at one time | {aaa: "input value",  bbb: "input value"} |

　*struct* is a parameter that defines multiple parameters in a combined fashion. For the type name, specify any string that does not contain a symbol. For the type definition, place that information within a separate section as shown in the explanation below.

/\*\~struct\~type name:  
\*  
\* @param param  
\* @text parameter name  
\* @desc parameter description  
\* @default  
\* ......  
\*/

　It is also possible to then place *struct* in an array. Some of the official plugins will serve as a good reference regarding the specific implementation methods.

　Depending on the type specified, further annotation may be required.

| Annotation | Applicable Type | Definition |
| :---- | :---- | :---- |
| @max | number | Maximum number value that can be entered |
| @min | number | Minimum number value that can be entered |
| @decimals | number | Number of digits following the decimal point |
| @dir | file | Corresponding directory when specifying a file dialog |
| @on | boolean | Value displayed in the dialog when ON is selected |
| @off | boolean | Value displayed in the dialog when OFF is selected |
| @option | select combo | Value displayed in the dialog as a pull-down display option |
| @value | select combo | Value actually set in the parameter when the pull-down option is selected; in short, the value of *@option* is set in the parameter |

### **Plugin Commands**

　With the specifications for plugin commands being retooled in MZ, it is now possible to represent command and argument definitions using annotations. If the command name and argument data are defined beforehand, the user can call the command just by selecting it from the event command.

\* @command COMMAND  
\* @text command name  
\* @desc command description  
\*  
\* @arg arg1  
\* @text argument name  
\* @desc argument description

| Annotation | Definition |
| :---- | :---- |
| @command | Plugin command name; used as an identifier when actually called; written at the very top of the annotation defining the command |
| @arg | Name of plugin command's argument; written at the very top of the annotation defining the argument |

　For the plugin command and its argument, you can designate annotations in the same way as parameters and also specify display names, detailed explanations, default values, and type names.

### **Dependent Relationships between Plugins**

　MZ has now introduced annotations that define the dependent relationships between plugins. By using these newly added annotations, you can clarify the base plugin and other details.

| Annotation | Definition |
| :---- | :---- |
| @base | Specifies the name of the base plugin; displays a warning if, without entering the base plugin, you only enter the plugin in question |
| @orderAfter | If applied, specifies the name of a plugin that must be ordered higher; used for reasons such as preventing conflict |
| @orderBefore | If applied, specifies the name of a plugin that must be ordered lower; used for reasons such as preventing conflict |

### **Dealing with the Unused Assets Deletion Function**

![][image7]  
　When directly loading images within plugins, if you check "Exclude unused files" when carrying out deployment, it is possible that required images will be excluded. Consider the following images.

\- img/pictures folder / image\_1.png  
\- img/system folder / image\_2.png  
\- img/example folder / image\_3.png\*

You can write the following code that references each of these images.

let b1 \= ImageManager.loadPicture("image\_1");  
let b2 \= ImageManager.loadSystem("image\_2");  
let b3 \= ImageManager.loadBitmap("img/example/", "image\_3");  
\* This example specifies an example folder that does not currently exist based on the plugin's notation.

　However, if you proceed in this way, the images will be deleted.  
If the image files you will use have a fixed filename, use *@requiredAssets* followed by the names of the required files.

\* @requiredAssets img/pictures/image\_1  
\* @requiredAssets img/system/image\_2  
\* @requiredAssets img/example/image\_3

| Annotation | Definition |
| :---- | :---- |
| @requiredAssets | Specifies the path of asset files for which deletion is not allowed during deployment |

　If you wish to set the images specified by a game creator using plugin parameters as being not subject to deletion, you can ensure that as long as the *@file* and *@dir* annotations explained previously have been completed. Please also note that MZ has discontinued the use of the annotation *@require*, which featured in the previous version, MV.

　The following is a list of the annotations used to ensure files specified in a note are not subject to "Exclude unused files."

 \* @noteParam sampleImage  
 \* @noteDir img/sample/  
 \* @noteType file  
 \* @noteData items

| Annotation | Definition |
| :---- | :---- |
| @noteParam | Specifies a note's name |
| @noteDir | Specifies the folder in which an image is stored |
| @noteType | "file" is specified here as a fixed notation |
| ＠noteData | Database used by the note in question; specifies one of the following databases: maps events actors classes skills items weapons armors enemies states tilesets |

## **4.4 Points to Consider When Making an Asset Public**

　If instead of making a plugin exclusively for yourself as a game creator, you are thinking of releasing it to the public as a plugin asset, you must follow the right plan so that many people can enjoy using it.

### **Multi Language Support**

　If you make a plugin public, it is possible that it will be used by people speaking a variety of different languages. For this reason, if you create a Help that is based on editors' language settings, it is very likely that a wider range of people will use the plugin.

　When creating a Help for each language, provide a language code at the start of the help comments. For example, the following code is used for Japanese.  

/\*:ja  
 \* @target MZ  
 \*/

　If the language code matches the code that corresponds to the user, that Help can be used. If they do not match, a Help that does not have a language code assigned, as shown below, will be used.

/\*:  
 \* @target MZ  
 \*/

### **Licensing**

　**Disclaimer: The goal of this tutorial is not to give legal advice. If your intent is to license software that does not fall under the definition of open-source software, you should seek advice from a legal professional. This tutorial nor its contributors are responsible for the use of any advice provided herein.**   
　A license is, so to speak, a plugin's terms and conditions. Although it is fine if you determine these terms and conditions yourself, consider the necessity of referring to wide-ranging cases, such as those involving commercial use or usage as an adult-only product, by adopting a license that has already been used widespread, you can prevent in advance any problems or misunderstandings, even among users speaking other languages. 

　The GitHub community has created a resource to help [**open-source**](https://opensource.com/resources/what-open-source) developers of any calibre to choose a license for their projects, hosted on [choosealicense.com](https://choosealicense.com/). However, if you want a quick and easy solution to your licensing woes, consider using the [MIT license](https://choosealicense.com/licenses/mit/). This is perhaps the most permissive license, allowing users of your project to modify, distribute, and sell copies of your code as long as they include a copy of the original license alongside their code. In this case, this license would be copied into a comment at the top of your plugin file. Since the license should include your name in its header, simply retaining that license in its original form in the plugin file is enough for users to fulfill the terms of the license. 

　It is worth noting that **a license provides security not just for the creator, but for any potential users as well**. If you are unsure whether or not you want to license your software, or if you want to avoid using a license altogether, **you may want to [consider the downsides of releasing unlicensed code](https://choosealicense.com/no-permission/)**, and instead consider using the [unlicense](https://choosealicense.com/licenses/unlicense/). 

[image1]: <data:image/png;base64,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>

[image2]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAloAAAHoCAYAAACRsUEJAABfU0lEQVR4Xuzd53NT6aLv+f1maubtram6derWTNW5Z5/eDSYnk3OmTY7G2IATwUCTmxwMJgeTczQ5g3HOESfovc8+86r/mN88S5It+VmyWLjlTbf9fao+hbSSlmSFr5dk8Ze4peM1a/F4Of+2cs5PmBHr45yeFz/Oxzndylmudbq9jTnxE9ttL3R66/KhWrcTqnUbf6R9az3/tX1r3Q97vyLtm7PNSPtmTwvdTui+he5L6Gkv+xa6vdD9jbRvX7vNWud3tP637lvoOpG26+Xnae9b6zZD9+173ddafY99s6eFbqd1W172rXU/7P2KtG+R7msdTQ+3b/YyjtbL/tq+hW4vdH8j7Vu4ywzdTuv8jta3982+/NZ9CN2WvW/2Nlune9k3x9d+nt+6b6H7YF9+6/Su2LfQ/fo9+2ZPC91O67a87Nt//Md/oIf7i3OHYDAYDAaDwWBEdxBaDAaDwWAwGF00fKHlHN5kMBgMBoPBYER3EFoMBoPBYDAYXTQILQaDwWAwGIwuGt8cWunp6UrPzrcnRxzZ6dn6zZ7IYDAYDAaD0c3HN4eWk1i/ZWf7/u14/KbsUaMCJ01kZacr2y6t/HSNck0MP9ouy2wr3VrnL3/5S5tRIad9RmW3W5bBYDAYDAajM8PpinCjo+mtwxdazneAhB0mhtqFixMzIUe07KhpSyATRKHREy6nRv1lVFt8pY8KE2Ktw2yrdTvZ2aNCLjO4fr7ZJ2ePWiPM/89vviNpDAaDwWAwGL93tLS0+Hxtmj2++esdOgyitpHvC6e2o1Am1toPZ364+ssPCbLfwl5OuGnOILQYDAaDwWB09XCi6v/4P/+vdv9+bXxjaP3WLqBcR7tM4fyWPardW4LO+dCRPsrMb31bsaPhvN3oP6HsUe0vwz6Clh4yjdBiMBgMBoPRleNbIssZ3xRadjSFjvz04Ft5IRP1l/RAmjlvJwbCJ9J2fEe8/hI8CvZb/m/tYqotsn4LXljrEa3W4doPBoPBYDAYjN85uviIlv8twY7GqNDPaAWG84H4cNHTcWj5j2DZH5JPb421DoYTWtn57T8X1hpkDAaDwWAwGNEYoXHVGltfG77Qcv5TzK8NJ5o67p3fwsz7zRVMraOj0HIuY5R7Q+4jWn8J+YzXb04AOvsWvKwOLpbBYDAYDAajUyPcB9/DTbPHV0PL95mrDj7r5Pu8lQmjkHfxJOfIkvNh+AixY4dW63Y6GhFDKzCcbdrLhFuOwWAwGAwG4181vuGtQwaDwWAwGAzGt4xv/sJSBoPBYDAYDIa34QutCTNi7ekMBoPBYDAYjN85eOuQwWAwGAwGo4sGocVgMBgMBoPRRYPQYjAYDAaDweiiwYfhGQwGg8FgMLpotB3Rmv7TbAAAAERR2xeW2jMAAADw+7S9dWjPAAAAwO9DaAEAAHQRPqMFAADQRfiMFgAAQBfxdERr6syfFNOnr/7617/q3//93wEAAHo0p4n69O3rayS7m1yh1dFntJyVe8f00cjRY7QsIREAAAAhnEZyWqmj4Ip4RGvIsFj17ddPi5bGuzYMAADQ0zmN5LSS00x2R301tJxDYpOnTnNtFAAAAH5OKzkfsbI7qi20nLcOp82Kc3Heg1y6fAUAAAAicJrJ7ihHFEMrRVvOv1Tlx/s6nLEqzPxvs2zVJu09tFNpGQe0KdE9HwAA4I8iaqGVndeg5ubmMFrUUv1Umy7lqb7gsjauWKHDz+vU0tISVnK77aZp/+Nq1by7qwsXL/lkX7qvD3XNKn9yTW9vHlRagvtKOZal7tbFdzVqbmnU6sC068VN5jKa9anspRJDl0/eqE0ZaW3nM1/496/+9YmQbW70Tat7cSxk2irX/rcqu72r3f68qHem17ebBgAAureIoeV8Rsue0VFoXShodMVGqObmar04vkHLzLI7zt7QtRvhtUaRT2qmntS4t+WozDng2oc2CSnKNzHmW7apQgmB6c9KP5nw8q9fX/JYR9Yn+qYn7XuoSjPt6Br/ct8SWh/z8trLL/ItR2gBAICohdbqdRu1LsPtyNMqX3jsSF/liyx7vUg2XvioBrPuy8ePlfPokc+7cn9Ald36xbW8b51DV/XCBJWzTGPFK53dlhIyf7XW7L2opyWfVHZvn1b6piVr591y3/LO0TZnOe+hZVutzVcK1NJYoEtb2r9N2hpa33obAACAP6+ohVZHPjQ4gfEpZFp621GpcHLPb/LHyKqdvvPN5Q/bba/Mt1y5bu9a7Z+2Yqsanbcnre0cSHHvSzh7Hlb4j3J9+tA2LWxoJW71Tavq4Eja8owTel7tv+wdq93z/aHV3uv7F3Vw61qt6ODtTwAA8OfWxaGV4o+Y+rch05K0YdNml40HbquoqUUP9gWOQK3aquZP+bq8PTlk3TR/pFQ+1O7k1mn+cGtuqFbh6/vadbVATZ5Da7VqfdHTpJI7u9umH7jzTu8/5Ord/aPBZdOO+ZbLv/BzmO2s0NPKwFuV9bmueY7WI1q3nn1UWb3zWbFgcDXkX3YtDwAA/vy6MLSSlHb4sZwPn5ff3x9mfnvHXtb6ouNAanDaxk3BD6gvXZ6olAMPfbFTeG2HVoRczsZ1aUoIHBXKuOgttOKTt+r4oxJ/6BTe0PYwR6FCL3vtqbdqaS7R9R32X04mKXXfzXbhdHyjvYz1Ga2EVUr+eb/yqhpMiDap4PJW1/IAAODPL3qhlbRBu05c0NV7z9QQ8lbegbVJ7mWXJ2vNzgO6cOux3hRVB5ZvVOnDI+2W2/TLQR05e13Vvrcf/Y5krAyzvaBIofW4OnDUqVVTrdYluZdzxCdn6OdfDul1SV3bB+hPbgy57IQ0bTv3NLCtJm1P8X+wPmHDCf+0T/nttseH4QEA6HmiF1rL1+vEW/+H0B1NtYV6dD74dlx7Kdr3qDokepp1I3NT+69cMN6GBFZzQ7le38gMs632IoXW5cLAW3bNjXp0JUub0zqOtoQdt1Tatn9Nqvl4x1omUWtOvlFzbb7uHN3cbt7DskZzGVVtf+3oILQAAOh5IobWt3yPFgAAANojtAAAALoIoQUAANBFCC0AAIAuQmgBAAB0kYih9W1/dRi0On1tt/c//ue/uaYBXnH/AYA/ps48P9sd1OWhtSptTbfn/CDsaYBX3H8A4I+pM8/Pdgd1eWitTE3v9pwfhD0N8Ir7DwD8MXXm+dnuoG8KranmjM1ZaYlZuSNJKWmeZJx+raqadzq9OTBt7QG9u39RZx8Xq+ztlbbl9t0vUV3lW107c0k7167R1ouvVVD4TElpGdq496T2Z7i33dWcH4Q9LaINR/WgvFHb1q5V8pp1PqvT3MvVNFfq4eENvtOpBx+qrLleK+1t4U/P0/1n3S4dyb6k8xf9th+7rZdF73Vp5xolpe/R1bwKbXCWS9uozXsPaM/+gz679+/RscvXdOlqiIvH3NsHALh4en622B0Uymkmu6McwdCa+ZOLL7TiEzqUmJzqyYZz71T/6YNO/xyYln5A1c+Oa9O+m/pY36xd61LNC0qGSpvq9P7qYe04ckNlj0/p0K0iNX2qUF1jk5qb6nVx33rXtrua84Owp0Vyq7DB/w33zc1tSu8e0OrA/EdPn+rRk6d6W9ak+uI3vtOviuvVUp3vO/3o6RNdPbzRtV38OXm6/6w5pDtFVaqsdFRq9cZTelHbooqHh7X2+EtVt1T5l0vbqxslIf9Red1L5VS3qLHOv251vXmclN52bx8A4OLp+dlid1AoX2iFaSlfaM2LH+ea4SW0VqxO+aqUgzl6/fyjL7Ru33mvqupqo8YEVG3gdLVyr+7WSvMikvsxr837B6e1/2q+GlqaVW2Wr2toNqHm3n5Xc34Q9jSX5AztuPBS5Y3NOnooW7dvHvVPX7Nf1wo+aWd6cNndlx7qQc6joIfX9cvR48rcv1Wnn5nr/vi01tnbx5+Wl/tP2tEnKq3xPxYct9/Xqbbgublv5Pi9KdW5LWbZ1D26UdqsZLPOujPv9MmE1sPqJhXcOqxNW37R8ec1vtCytw8AcPPy/GyzO6jLQythVfLXJW83Lwh1avz0XjfOX9ON23eMR6rLf6qbvtN3dPX4diWm7FHFs4vKzDqmw0dPqfrFGe3JPK9zly5o78HD2rv/kLakh9l+F3N+EPY0l+StOvOmWK+vHdKmc+9U29KgtA2ZulVQr6bq1+2WPfjUvBjWlOjd+/d6X2xOmxdL58WzMueQzn1sUN2bM1prbx9/Wt7uP5u0I+ukjp085XP+Xb1qXxxXWmD+WhNV5zab0yn+0Mp5/ESP3pWpwdx3HlQ5/6dn4Oip83+Pltxybx8A4OLp+dlid5Dn0OrsW4f2DnTkyatC1ZvQOrXJf37FlotqKr6prSkhy5kXkbryfH3IzfWpfnFWB28Wqqk+X7mlNWpoata1PWtc2+5q3/6DWKudN53r26yG0sc6+nNqu/lOaDUV31BSyhptvpKvRkKrW/N0/0neqQsfKv1HtGqqdMGEVs2LE0pfnapEI+P8+2BolTT7Hh+5JeZ+5BzRqmpSwY09SknfpMxn1b4jWq7tAwBcPD0/W+wO8hxa46fFumZ4Ca3lK1d5cuFVhe+I1smNzvlNOv6mTh9qP+nduc1KaF0ueZcqcjK1fnumTp69oOrnp3XACa3GYp0+l60LD/N0a3eqa9tdzflB2NNcktdo/S9HdPbeG/9nZxrNC2VNbZvaT01qLrujnSmrdPCJE1q3tGHzVu26nhcSWgcDoXVaa+zt40/L0/1n9XYTWlW+0Ko2obV5x27tu/FRDfXvVNxcrcen92hd+irfY+S6ua+sNus4R7k+1b3Q6/pm1VUUqaCgUMVVDWouuenePgDAxdPzs8XuIM+hNWFG50IrPmlVZKs260hOoe9tjRYntDas0up9D3x/YXfgUaWayu5rV1pg2dW7lHv7gJK3XtTLwgI9uXNJx8/c0LPcAhWXlqq4uEAbk8NcRhdzfhD2NFva8VeqbWlSfUWeLr2qUWPBlXbzD5i4ai67qx3J/tONJc99fyF2+UmhL7ScF8/Khwd1tjW0wlwG/py83H/iU7dp33H/24aOxKQUbb9Vqubqx77Qyjm8WVs2rVWCeYxcL2lWYVGRiivq1WxCq7SlRu8e3NS1Gzd174NzROuWe/sAABdPz88Wu4M8h1aktw4Xm5U7sixxpSdpJ9/43zrccdAEV54u7kg105O14fx71bXUa5WzXFKGmipytG/TUT2uadYKM3/NoTt6/iDLhFm1ia16bU12b7urOT8Ie1okh545oXVHv+zd1+b0i2rfEa3tq1dqv3NEq+iaWXaV1md/NKH1QgnJaUpctSoQWqeUHma7+HPydP9J3q97lU1KXLnFd1Rz10XncVGn16c2+ULr4aGdKr+/X0mrNmp75jHz2PCvl/DzeVU+OqzVvvNrfPct54iWa/sAABdPz88Wu4NCdUloLV2R5EnqCRNa9aUqrGjUvYPrtKxt3lrtuVeikvtH9MvFXD07tsH/olPVors3b+jKtRu6duuBWhpydeHoNb0/v0XxYbbflZwfhD0tkoPPatXS3KhPDQ1tnM+XOaG1bVWS9j/2h9bjwiLfWz0ttc+0dN1xPS4pV21ji2qeHdXqMNvFn5On+8/qfbpb2eK7rzQ2t6i+pUXVr89o3cok5Tc1qa6iXAVXtrW77y9be1j3ShqVuW6lOb9Gubl5Kq5t8h1NdW0fAODi6fnZYndQl4fWkoRET1KznqjIebvs3EXXvCUJadq3NklLVm5Sou98qracfaC8gkIVFRUpP/+jbp7YbualaHWSvW7Xc34Q9rRI9lx/ruc5Z9r9YHZffabnjy9oy6pE/XLlmZ49PKPseznKefxYt8/t1pK0fcp+8ESPH97U8W1prm3iz8vT/Wf1Xt0sqtQve/Zqp3H5RpbWrvTP++Xsdd28e1/b05Os9ZKVceJa4HSKHj5+pqdPH+vG8a3u7QMAXDw9P1vsDury0Fq8fEW35/wg7GmAV9x/AOCPqVPPz3YHdXVoOTsJAADQE9gd5Dm0In1hqb2hUD/0igEAAOgR7A7yHFqzFnfuiJa9A7b/93//1TUtHGe5//vf/pdrOgAAwB+F3UHfPbQcvfv0U98BgzrUp/8A33LOITl7XaCn6zs1QxdeF2v77KGueZ0RO2uGRg6bpfRtya550TFUi488UO+28330t96hgssOmrpEMa71Y/S3PkM1fPhQ/S1k2k8/TdaQPoHzfUZowux5rvV8evdVL/Oc42Iuu22ZIcu09+q5duvFzPxZZy7utbY3ULO2X9aAwPkJk6dq4hS/0H0D0HPYHeQ5tDr7GS17B8KJ6Tfgq5zl2ofWIFXXFunl01cqrK1WX9+08aopK1B+fr7PnP4dTfsOhiQqu6xWRa9yVFDdoLI7G/XDyFSdf/VOb3PLtHRwmHW8GJ6qJ1smRXxSj5n8s+6U1asy74UKXx/9190G5joXvszR/ae5+nBquYbY8/ENhmrhoYd69vy5y/uSXJ1dPVWP72zQqMDy+SXFKipqr7gkX9fXjGu/3UFLdbowVydTFmjOvPk+81NP6tnT/Zq3cL8m97P3I2jgnN3KKS/V7YzJ/mn9ftKu5xVKmxGrH8Ms32pI0hUVvd6vjDv5ur9hovoPHqr+sct0Mv+9+o1YqYslrwLL9tXE7c800He6nybtfKaLZ7K0Z+s6jR46sO0+33tgrIbEDldB/gktGD7Md3pQ7GJl5RX6Tw/s51t22PIz+lD22IRWH8VMXKuL74s1Y9ggDYvL0McHhxU/1v88c+jyNV2+eldvzHW7fOVqmys3X6m04q2uXDmqhFExGr/lkV5d2K+s62e06lqubqaOV2nOJo3q3U9Tdj3Xwl/u6faWqa7rD6B7szvIc2h15We0evft/1XOcu1Ca+QaHZk32He6/7wspY50po/Xo812dISb9h2Y6LhQlq+suQPVa1yG7lQWts3rt+Bk50Ord3/16xfym3gYabfLlJ+9UsN6x+hv/QaqT8gRgy5lrnPWvEFyjljkV99Vmu9nhM4ZoNFzE7UiaaWL8z8pVFTkatlo/+PkW/Sdf1wfzX3x7du3bfIqar4a7z/EDFdRbZ6y0ya1O+L0t8HTVPqpVrlXt7Vbvv+iE3r7Yr9+6B+nPa/K9eJSlj4UPdHZo1nqYyJq3IYHKjPx9bexG3Sv5K6GrDir1wXml6PSWn3My9O761u0ct+zwC9U7SVk55nrX6GmxlpVmn+d0xUVlaptaPSd/mju+4N9y/bTqJSr2rR2j85dvKQLRoPzvWSf8nynL2alaHTrY2PICmWbgF27PiNoxyXlllxsu1xfaJ1I0rwtd3Xg1gfdPX5a51aMMrdbX43NuK2S0rfKWhydo4wA/jzsDvIcWl15RMuOqnCc5UJDa8Cy88EjM/3n6+wy5wnNRNWmCe7Qck37DgKhdcSE1g8xU7X9ZUXbvD7mxS40tOYtmquxg2L04/AZmr9ojkYPMNP7jtC0hPUaGztGU+Yv0pQR/RQzdo4WLVmmeZOGta07Z+F8TRw5WmuSF2v8YH+A3ax8r/2zrBfh3gM1cu4qrd2Qob6+F5chmj11muampGnh+CFKS0/QxMFDw0zrE2bd4OVOX7G+7XKd6+y7vuZ0TvlDrRvtX3baolVKy1ivYX2D+zNm/mqlm2kjB/ZtmzY8LknpGzeEfXFF0Phtz1R6O9013YvEKwV6fXBuu9t46/MK3U4f7Vq2Vez8rbrwpkzpU/y/6NhiRi/TrlsfNTwk6GceeKO8c+b+s+mByptKdGPPRt09sllbTj/Toq03VVT9QvvX7dXrvErVvNmvmOGTNHnKT0q+UKj4qdM1ZcpULT3yUoP6D1b/QUPa9O0b/CWjIP+4Zoc8JxzNC/4yE9Rf/ReeVO6bLK2Yu1CHX37UuTWLtXj7bRU93myF1nulr13XJm3rxXahtf+KuU7Pb+vWg6cqrm5Qfd51vXr1Ouj2dk1pfSsTQI9hd5Dn0OrKz2j9GNP3q5zlgqHVR2M3P9Xwtm2MCfwGPl4NddWqqqry8T9phpv2HQRC62TCZCXsf6Ty6gdt8+zQelp6QytjY9RrxgG9K72k+CExelL9RntmDNCItFuqbHqvfTP7BZYfp8chRx9u1zTqQ9YC/W30Ot0ue6JN4/sov+iMFgxsvz8PKt9o9wx/fL2uytH6seNVcS1Fw8b+rJz6Eo37OUcl93aGmbY+zLp92i63v7MPgct1rnPjp09qaGrQ4sDbMs5RhdZ9eFF6TUnDYnwviicX+V+0f+zXX72c+SPTdXi2czTMvIAWntHCQdbtiTbHC0qUndAa230UOyfVhMH6MLbp/IcSXU6K9S3be8J6XVo12vVLyOvym0oe0Xq+v4bPXq3rz/NVWVutkjc3te9Zme6tG+vaj471UXneCc1z7oO9J2vrs2pVl5WoprxYxeXVGrH0nPJyL2nbzyd02IT1+ox1vvX6xGXqQ1OzPrw6oBn9RinlZqF6x/TTjyb0884u04De5rkh5PH8tdD6UF6mUnN54xec0Id32fo5fa1Ov/6oazvXad2hh2FDa+yESW3GLTlqHo/B0Eq4lKecbYu0KvuVkq7m6kbKKKVfeKvid/d1+2WhRhFZQI9kd5Dn0OrKI1p2VIXjLBcptB773h4cr8fbpiomxv/hVv+8cNO+Aye0yhvMi0uFCl5e085Fo9rmeQmt4oLj/iN4I9fpbnWE0Kr+aALFRM3geJ0tNsvN6OcLrYVWaBUXn22bdrq4RGeWTNPrPbPUa9R63a18oRFr76r44a4w0zaEWXdI8HLNtNbLda7zsQXDFDNgpIoLz2vpUP86C37O0sXbOeZFr/XtxJEqyjmq5J/GtO1fTNwRpc+coWkzZul+uYm5Me33H0GlRee0eIh7uu1vo83PseKVdk5xHk/9NDblRJijhQNVfCMt5LE1QLN23tD21MWaONz/uajNT8u/KbR6jV+vG6lj/PfRmKna+TJPp+In61rGTMXteqx11/L19uYpZZ28qasnjivr+EH5PjB/6pWePn6rg88/KjslUZkfigPbNPfpM8t8Ue+cP3I0y6e0KEenAqePHD2t+0XFgdOZ2rRguJzPfI3OuO8Lrdw3R7R0RpwOvcrV2dS5mr8leETruRNkZeWq+dSg0tLSoPJaNTbWqrzylfbO7K+rxa+0Z+ZgDVqwTZdf5evW7vXKyS1V8VsTWs+LdPP4DiVMGeK6PQB0b3YHeQ4t54jWFPOiZ3NWWrRseYfsHQin/V8checsF/rWofO5psWtcTJ4mY4vcI6IhHubMNy07yD0rUNrnh1aT8puKXl4jAYnXlF5uT+08ksuaKn592/jNyunNkJolT/TZudo0sBlOl30XvvNclfK81yXm1+S3XaZ50oKdGz+ZN3fMF5/c6LKhM3wNf7Qck/bEGbdgcHLNdNaLzf0rcODH6p0M3WUfpz8ixKdo1hm2rsq+3Nb/VVktr3EbLvXtL1aOybyZ896upixK3XiTZVGezpyMlCFde90eF7HL/x9J6/X5YKqtr+g64jX0Jq+/rze1tQpNzs1OL3/AmXlfTK/cDgxY1TWKPN8ts5lGxfu65bzb/Z5zc96o1cnErVg13MNjBmo8RvuqfzN/sB22odWq97j1+jE6QxNNL+QxB/J1u4l7rc/R5pfFpzQ+vhmn+9tvR0vP+qEee4Yuvq6Ca2ffaG1+uBt5VaW6emZ7YpPWKmNF3OVkJCo+MQ0bTnzVDcPpGh6rLl/D16us0WVyn/zWkVlJXr/6pWKywr11vz76k2BFnMUFuiR7A4K5TST3VGOLg8tr9p9GH7Icl1Pn6De5sV5dPoNLfH9Rh8uqsJN+w4ihFbvnw4rIXC0x3G9/J0Ozh6szQ8q1RQIreySaj3dv0SrT79W5adAaPneOhmnp9unqrcTpL3Ch1bChSKVPdyhGYP7aujMhZpitneprEjnE0erl3nRKiq7ohWx48JEVfjQcq8bcrm92odW1nwngPvqXd0r/TKtnwnFLUobY+b1Ga2GmkBo9Zmsob7Pa/XRh5KLvuv7w4D5evzLLN+L6fCpkzTIvj17tH5Kz8pRUV21Xp9aFWZ+e8NmpujA/WIdTxgT/q8Be/fTgAmLVVpXovu7OvhKhBARQ8tsa+K81dp87LY+lT5V1urJ7Y+axaboauH9QET31YStj5WSvkapRsq6LB1Ym+473XvSMi2cMMD/V4f9ftLuVxV6tGVKYDvhQquP7pZV6cnu2b7poxOz9LyyWqNCPgfohPy4TQ+0ML59aGUlpKi4olYlV5M1zCx348xWLV6wRgfPZevsufO69KRI58y/zulz5w7p5zM3lJU40hda54peaZe5X5/7aK7TaLMPH1t/UdhDaAE9lN1Bf4zQ+jFG//lj74ic5dp/vUMfvauqVXV1tWqr3gdCKlxUhZv2HThf71D6UZlhQuuHoStUZ36DLi+55QuP+DMfVdtQrwenLuplkT+0hi0/oVdVDXp8PFM3S/yhtfJSge+vquqqK1WZn634oc7no57q55DQcpb72/BlOvy0TLW1NarOP+fb3uiUS/pYW6fKiiplp4w30TRO9zJCoir9roru/xJmWkaYdUMut5c/tHwhaK5zfW21qiqrdHvbT/4Xxt6jVF1VopLyMt0uuBMIrWmqqi5XcZF5od8xq+2F+Wl5vWoqzO1yf6PGfK/P1v3BXH74SnkmKN7eOKSV04aFDydjdPxOHTyRres5b81966PuHVvvWuaHwXN07eFr5ZdVq6aqSIvHBb8yIZKOQ2uwFpwoUG15vp7fOK6Bfez5MYr56ZDe553UPOcPPJyvbNj+WH0C8/42dpN1hLOPJmx7poQDL1SVe1zz2o76WqFlon3+rvu6vG5K27YcvUYuU0nOXs0e6r9fztx+XyUlOSp5fUm705do2vgxGjZylIbGDtewESM1dNhQ9TH7PGBorAYPG+4zaPBoLTn5QcMGDQtOGzpUMTHOX1gGQmv6AF9orRvbzxdaSwf3Ucy0vSa42n8nGICewe6g7x5afDO8N0NGDvN9wePwlOsqL7ushMDbb8Cfi/PlxP4/pOg/eJgJGf8fPPj0H6Eh1vd29R8zy//HEZYhg4J/RfvjwCFtf/3q0meEYp23+czpfv3db0XbH1HwEpqtXF94Gkboh/UB9Ax2B3kOLefD8PaMaISWE0/2f8gYjrPc//Pv/+Fav6dYdbVENZXFqvtUotsbp4Z8qzYAAPijsDvou4cWAABAd2F3UJeH1rLMOs3f+0pzdj0AAADolubtfelrHruDujy05u154dqZUP/2v390vU0YjrPckNmprvUBAAD+CJwDS3YHdXlotV54wrH/LyznMFvvPs4HZAd1qE//4H8qba8PILKk4+5pfwhmv1bY06LsUcVnVVb9quyr/+2a92ey8uI/ono91lz5p9ae/qcy/qj3DeBPqLV37A76l4XW8qz/DssJqJh+A0xMDQxjsEbPWaRJQ/1fieCEVui6yRf+Swfv/EO7LvzTP+2kefI4GZh/4p9a13r6D2CFeVLbevm/tC2EvUxnJGf/l/Zd+6fST7jnfdWZf+hW4Rf39K9Yd8lcprndj9z9hxLDzEfX2WTu6+GsP+1e1uf0P3TpYpjpAavNYyaclcety330Rbnv/qHUMNto53j4bdrbc2x59kUFryM/DpzA2GTft0/+lw5FuE5B/9SVK/+tpOy/62Xh39ume7oeNvN8sv3yP7X54a/KOBZm/td0cLs4XMu6/FNHPn5pux4ZZlrSafd9oFW49Y/nfw6eP/ZPnS35rAe3/ks5t8Mt397Ki8GfUZLZXx7zQHi/O7Q6+/UOrRccf+QfYfmOaIX5T6QdB+8814sXL4zHvu9WckKrbd3Tv+rmFf/plVe+6Kh5QYk/+6vqi37VmsD8s+fcl/e9LT/3q850ar/+rqyClnbT7tZ81qNb/tMpl/6ujcfsdb7i6D+UdDzM9Hb8l/s+5+9t03LqPutW4LYv+/RZWc5t71oP38sKcx+78uKLbrz+onvvv6ik+LPeGPkVn1VS9VnnskOWzWovwdwncs3P9Oz59tvc+OSzKvN+VUqYy2vnqHt7qy7+6tqe45W5Hz189qsuPg2qKv5Va0OWSbr6Rb/Y9+vjf9edq8Hzay//qoO3wqup/6x3eV+070xweU/XI+Dk2y/KMfsVf/TvOl7wWR+e/l1FpV+03d6nr7FuF4dzuzi3dehy9v63ynzuvh5eJZnnx1JzOYUVQaX1LfrwKPiYDmf7o8+qaPisnLvB5Zab2z7z9WdVNbVox6n2y6+89kVbstzbAXqK7x5ayzJ/DavD0Bo4JRBZz3U3M7HtiFbreiuvf9aOrMB2sr7o/jXz75kvyi//bELGnD71RWfOui/vuzP7eOpM+2lpF7/okHmxSAyc32WesDacMKeP/art5oVmi4nGhCO/+oIn8eivWmHEm+UemyfLKxfclxF//FeduPdFO8z1X27Orz73RbvMcgnm9jp254v5jdxs4/QX7b7m17reTvOEnGYu9xezTPJR/7TWy/3w+Evb5ebUtejmJf/8t+aF7LjZv3iz7Z/Nvmbd/6KUwLqOtZf909Jbf1aZ/uub9eBL2/VFdC0/byLrxWddfvpF53O+6P3LLzp484t2mp/FlgvmZ3HMvU4b8/MufvNFq6zpGx6b0Ppo7hf28l9jtnfkY4tre45yEw5p1rQK6zISr3zWzpD7js+xL7pzxb29cKryvyjVmub5eph9ry79rLe1LVpn7tMrzf32+FVz+x4Js2wnOLeLc1vb08NZb6LHvh5eHcxtUf7zkMsx+3+utEUv77qXbZVq7ivVJsiyzrvnORLM82tpbvvbdouJwXA/Z6Cn+O6htfTw57CcgPJ/ud8gxU6ZquH9nNNDNG3TRV9oPbm0VTMG+79w0Amt1vXS7rVoTch2Xt8z/575rLuvW/TKPCnFnzTBdcZ9ed/d6c86dTp4fseLFtWbYMp3PP2sFWbahTLnCNJnrTHXsbLsszYdMb/NfjLLmd8ia82/ddUt2nvss46aACp51377y8+Z28Js66WZV1z8WRszP5sXSbNcXoseVbbosZmeaW6bpCstelFsLtO8iLSuW1jVomfmCbjQqPpontgPBy+3qTF4uU5o3TIvgCtPmN+M881+msu4YNYpKWlRztsWVRd+bvvZ1FT7p5WHTHOu74uPwevruo3gdvSzdpv7+In7HVt/NMx6xkfzeFgWZno4a8197sBJ9/QMcx+qMfePW2ZbCZnu+R1xtlcVch9rlXD+sy5mu5fPNy/WCSHnV1xu0Q77epn74M1L7nXDKXrRfnuO1uux85x7+VCbzHXeddz/XFL2wTznfMP19sK5XcLd1uHsedfS7no8No+fJx24eiO43KqrLSo1l3Mo9HKyPutOTYtuX3ZfzjJzWz+paFFjsxPH7vmhlh9pv82bVe6fM9CT/O7QmrlorGvGt4TWkoNNYTkB9WNMX93zHb16odv7Fmrb1We+05kJY9TbzHPmt4ZW63prHrQoJWQ77x+Yf08169SpJh3Lb9H1m806fcp9ed/dyWadPOk/HZ/drOK6Zh0936SNF5r12pw+fsLMO9SkIyaMij42K/VQcN0j5nq5tmfmfzQxVPC8WYnm/GXzJPnyTvtlMh616FNZszJCttXqeGFwm0WfmnXkuP/0TRNI968EL9d3+waWe+g7omX2P7NJFTXN2n3UTDendz5oVk5+s6rqg9upKGrW4ezgus519l3fc03B62vtE75u6elm5YbczpGUvm3WavPzSTbLppr73poObvMPDS16fd893bHe3Icqzf1xtTmdet48zl4265NZ/mOu+fmecy8fur14a/qy483Kzml2LZ90pVl7nPtSyLQVl5q1PbP9tHhz+QePuS/PtvpGs3ZZ23O0Xg/nseNcj4La9tdj6YlmPTXTXtwNuUxzez839/u858H93vmwWVefd+yKmZ8cZr8SzWPduW3s26UjzvWorHHfXmGZfT9/Jnj+nnncJljLbH7WooqP7fftxftmnbvVrPWB2/V0SZjnmghemF+ent1yTwd6kt8dWr/3iNbiA41hOQHl/NcXW64FPo/18IyeBqIrNib4X2O0hlbresm3m7XmYGA75t8Xt82/5kXk1MlGpZgnjFzzxHn6pPvyvjvzInfyhP/08ovNKjdPuIUmgvKMfONYYJ9XXm3Ww6vt1800wePanrHCbKfERFLmsUbdMIFkr7fevKhV5DZpZZh1jxUGt1lowmfvUf/piybYcq4FL/fd/eA6Tmhdz/afvlppLs8sd7LAXI8PTdprouptrX9fnPk7zIvNO+cIwvVGLT3gv87hri++TaK5f1RWNWvLYfe8wx9aVFMf1OwcCQ05X2p+TvY6qddNXJg4yDfRvizM5Tn3oUpzH1oVMm2leUE//bpZly+7lw/d3qNb7vkuR5p0vSL8Zds2PmlWeutjvyNZJjLMY8G5z9nz7OvhCL0eZ4taVPLGvczys+a+ba7PijDb9Mq5XYrMY965bZzbxcv1da7Hm5DHXySbn5pY+spt89bcB25cdE8Pdaok/HNNOMvMc1rJWxOEYeYBPcn3D639n8JqDa3RqWf1KBBYjud3M9v9H2RtoRVYL+FCk3ZlBraT2aBbF8y/JmBOnzT/mljIMS/ip0+4L++7M/t4MrBfS80LVb4JpKzj1jKHGnTZ7H9ZeZN+PtQ6vUGZeS3u7TnM9X1W36yLZz75Pnvx5m5Du/nOi2T5B/PCaK9ntukLrcD5wgbnCJP/9D3zG7TvNg1c7rv7wW0+NEF2Pdt/+ooJrec3P+ljbZP2Hwlsx4m+rPaXVV7r/3k519l1ffHNMj+aF+wXDUoIM2/FsQalmNt/1VFz+vAnVRc3Kv2Aezmfgw3a97JZdeZntsScTzSh/OxOg+Kt5dY/dEKrUavs9cOwt/fB3Dft7YVaZvb3anGLyj82uubZlp1q1OtPHTwOQtwqb/Hd5+3pjq9dj/wi87g77J7uWHG+Se8fhb/dv8rc1s7tcu1yg++2cW4X57Z2LRdi2fFG3/VI6+jnF2Lt7SaVNza7podabm6/vKcNWhFmXlCDThV//TZebPZp450mFZhwTDsYZj7Qw/zu0Pq9X++waG9tWE5A/fBjjP7zx4Ga9vNlPXr6RPdOpmh0TG8zLag1tELXLXQ+r+R8hsg8eS12ppkn7JPH/PMSzG9sp467L++7O/ZJJwL76FhxvkHv61pUZa5Hdf4npZppD6qbdf9ynVZdN799VzdqT6Z/2dXmfE1ts3nhbND6fbU6ZV5saxvN9W9wnrDrtMzZ5sF6nck3y5gYqqto0JYDtVr3oEll7z8pKWQ/DrxrVk29f/3aKnMZh83tWdOkux+aVW+mPb1Vp6WBZZ3LrTDTWi/3QW2LGhqcoyTNenG/XsvNMvvemG2Zn0Oludzn1U3KPGLW3Vfnm+a8vfjqQb3iA9tzrm+9Wbf1+rpuI3Ro35NG5Zvbb3/IfehrSmsateOge/p6c7+4faNOCdb0FecalGt+bo+u17VNc+5DlR8+aWWY7Ydur7auybU9R/vt1Wnnkybffa/B3A92mcep7/Hbgc03G3TjfZNKzGPk9k33/jqSLjao1Dw2nMdCQW5DxO197Xp8zYpjdUoMM70jrbeLc1vb85zb2rldWvfXuR6PCprarseBU+51WqVeatCTQvP4MrfLJ3M7bgw8T4Q69qxRT8z2Ss3j8sObBu30dL+pM6HVHGZ6rbabiG5qNo9fs72Tl+q0Yp97GaCn+u6htXBPdVitoeX7t+0IlvV/B4WEVrv199do5ZEaJewLnN9bbZ6wgvNDT/9hWPvYOm3lITM9cH7p/sAye/2nl4Qsv8pc3xX7g+cXHzDXP+R8q9WZNSa8gttf2nobBSwy55ft93MuY5GZVljboF0HzbTDNa7tLd4fvNxF5nSi2Y/kI+2XW3rI/DzM+kta9z+wXpK1nLM/K8y01usL77be+aRDZ90/n0g+1jbqwGH39IUHO97OihO1Sg65z6y93agXz+qUFGbZ0O2tOhBmepjtrT5bp3RzH10SZlnbLyYu7z6p1/4I13vpyTptPRnyXBDBV69HtEW4XRyht4tzPU44MenheiRe+KTjJtI2HasxvxS55zv2PfQv8/OJjm87txodftUYZrp5bJvrsuKA//nCngf0dN89tBbsqgjr3/63P6C+xllu2OwdrvURPYW1n7Rrv3s6AACILCqhNXn6LBdnpYVLl3do7q4nbReOP7ZlBx9pwW73dAAA4MUTVweFcprJ7ihHSGjNdPGHVnyH5u38oDm/PA6zMwAAAN3D3F+e+JrH7qBQ/tByt5QvtObFj3PN8BJa7T5rBQAA0I3ZHURoAQAARIndQZ5Dy/keLXsGoQUAABBkd5Dn0Bo/LdY1g9ACAAAIsjvIc2hNmEFoAQAARGJ3kOfQ6uxfHdo7AAAA0F3ZHURoAQAARIndQZ5Diw/DAwAARGZ3kOfQ4ogWAABAZHYHEVoAAABRYncQoQUAABAldgd5Di0+owUAABCZ3UGeQ4sjWgAAAJHZHURoAQAARIndQZ5Dq7P/qXTfAYMAAAB6BLuDPIdWZz+jZe8AAABAd2V3EKEFAAAQJXYHeQ6tuE5+RsveAQAAgO7K7iDPoeUc0Zo0bYaLs9KCxUs7ZO8AAABAd2V3UCinmeyOchBaAAAAHtgdRGgBAABEid1BhBYAAECU2B3kObTilhJaAAAAkdgdRGgBAABEid1BhBYAAECU2B1EaAEAAESJ3UGEFgAAQJTYHURoAQAARIndQZ5Dq7Nf7/BDrxgAAIAewe4gQgsAACBK7A4itAAAAKLE7iDPoTVz0VjXDEILAAAgyO4gz6HFES0AAIDI7A7yHFpz4ie6ZhBaAAAAQXYHeQ6tuE5+vYO9AwAAAN2V3UGEFgAAQJTYHURoAQAARIndQd8UWhOnTndxVpq/aEmH7B0AAADoruwOCuU0k91RDl9ozYsf55pBaAEAAATZHURoAQAARIndQYQWAABAlNgd5Dm0nC8stWcQWgAAAEF2B3kOrfHTYl0zCC0AAIAgu4M8h1Zn/+qw74BBAAAAPYLdQYQWAABAlNgdRGgBAABEid1BnkOrsx+Gt3cAAACgu7I7yHNoxXFECwAAICK7gzyHVme/R8veAQAAgO7K7iDPoRXHES0AAICI7A7yHFp8RgsAACAyu4M8h1YcR7QAAAAisjuI0AIAAIgSu4MILQAAgCixO8hzaPEZLQAAgMjsDiK0AAAAosTuIM+hFbd0vCZMmebirDRv4eIO2TsAAADQXdkdFMppJrujHG1HtOwZXkLrh14xAAAAPYLdQYQWAABAlNgdRGgBAABEid1BhBYAAECU2B3kObTiOvlheHsHAAAAuiu7gwgtAACAKLE7iNACAACIEruDCC0AAIAosTuI0AIAAIgSu4MILQAAgCixO8hzaPH1DgAAAJHZHURoAQAARIndQYQWAABAlNgd5Dm0Zi4a65rRGlpzzcodsXcAAACgu7I7KFTE0Ip0RMveUKi+AwYBAAD0CHYHeQ6tOfETXTMILQAAgCC7gzyHVlyEr3ewN0RoAQCAnsjuIEILAAAgSuwOIrQAAACixO6gbwqt8ZOnujgrzVmwqEP2DgAAAHRXdgeFcprJ7iiHL7TmxY9zzSC0AAAAguwOIrQAAACixO4gz6EVx1uHAAAAEdkd5Dm0nC8stWcQWgAAAEF2B3kOrQkzYl0zCC0AAIAgu4M8h1Ycbx0CAABEZHcQoQUAABAldgcRWgAAAFFid5Dn0OLD8AAAAJHZHeQ5tOI6eUTrh14xAAAAPYLdQZ5Dq7NfWGrvAAAAQHdld5Dn0OKIFgAAQGR2B3kOrc5+RsveAQAAgO7K7iDPocURLQAAgMjsDiK0AAAAosTuIEILAAAgSuwO8hxafEYLAAAgMruDPIcWR7QAAAAiszvo20Jr0hQXX2jNX9ghewcAAAC6K7uDQvlCK0xLtb11OM6csTkrzTYrd8TeAQAAgO7K7qBQTjPZHeUgtAAAADywO4jQAgAAiBK7gzyHlvMZLXsGoQUAABBkd1CXh1bfAYMAAAB6BLuDCC0AAIAosTuI0AIAAIgSu4MILQAAgCixO4jQAgAAiBK7gwgtAACAKLE7yHNodfZ7tOwdAAAA6K7sDiK0AAAAosTuIEILAAAgSuwO8hxaMxeNdc0gtAAAAILsDvIcWhzRAgAAiMzuIM+hNSd+omsGoQUAABBkd5Dn0Irj6x0AAAAisjuI0AIAAIgSu4MILQAAgCixO+ibQmvsxMkuzkpx8xZ06IdeMQAAAD2C3UGhnGayO8rhC6158eNcMwgtAACAILuDCC0AAIAosTvIc2jx1iEAAEBkdgd5Di3nC0vtGYQWAABAkN1BnkNrwoxY1wxCCwAAIMjuIM+hxVuHAAAAkdkdFJXQ+mnu/A7ZOwAAANBd2R0UitACAAD4HewO8hxakT4Mb2+I0AIAAD2R3UGeQ4sjWgAAAJHZHeQ5tCJ9Yam9IUILAAD0RHYHeQ4t3joEAACIzO4gQgsAACBK7A7yHFqd/YxW3wGDAAAAegS7gzyHVmc/o2XvAAAAQHdld5Dn0IrjiBYAAEBEdgd5Dq3OfkbL3gEAAIDuyu4gz6EV5xzRmjDZxRdac+Z3yN4BAACA7sruoFC+0ArTUiGhNcnFH1rzOmTvAAAAQHdld1Aof2i5W6rtrcMx5oyN0AIAAPCzO8gOLbujHIQWAACAB3YHEVoAAABRYneQ59CKW0poAQAARGJ3EKEFAAAQJXYHEVoAAABRYncQoQUAABAldgcRWgAAAFFid1CXh9YPvWIAAAB6BLuDCC0AAIAosTvIc2h19nu07B0AAADoruwOIrQAAACixO4gQgsAACBK7A4itAAAAKLE7iBCCwAAIErsDvIcWvzVIQAAQGR2BxFaAAAAUWJ3EKEFAAAQJXYHfWNoTXTxh9bcDtk7AAAA0F3ZHRTKH1rulmoLrdHjJ7o4K82aPbdD9g4AAAB0V3YHhXKaye4ohy+05sWPc80gtAAAAILsDiK0AAAAosTuIM+hxVuHAAAAkdkd5Dm0xk+Ldc3wElp9BwwCAADoEewO8hxaE2YQWgAAAJHYHeQ5tOI6+dahvQMAAADdld1BhBYAAECU2B1EaAEAAESJ3UGEFgAAQJTYHURoAQAARIndQZ5Dq7NfWGrvAAAAQHdld5Dn0Jq1mCNaAAAAkdgdRGgBAABEid1BnkMrjs9oAQAARGR3kOfQ4jNaAAAAkdkd5Dm04jiiBQAAEJHdQZ5Di89oAQAARGZ3kOfQivMd0Zrg4g+tOR36oVcMAABAj2B3UCh/aLlbqu2I1qhxE1yclWbGzemQvQMAAADdld1BoZxmsjvKQWgBAAB4YHdQVEJrRtzsDtk7AAAA0F3ZHRSK0AIAAPgd7A7yHFrOh+HtGYQWAABAkN1BhBYAAECU2B1EaAEAAESJ3UGEFgAAQJTYHURoAQAARIndQYQWAABAlNgdRGgBAABEid1BnkOL79ECAACIzO4gQgsAACBK7A7yHFozF411zfASWn0HDAIAAOgR7A7yHFqdPaJl7wAAAEB3ZXcQoQUAABAldgd5Dq24Tv7Vob0DAAAA3ZXdQYQWAABAlNgdRGgBAABEid1B3xRaI80Zm7PSdLNyR+wdAAAA6K7sDgrlNJPdUY5gaI1184XWT7M7ZO8AAABAd2V3UChfaIVpKV9ozYsf55pBaAEAAATZHURoAQAARIndQZ5Dy/keLXsGoQUAABBkd5Dn0Bo/LdY1g9ACAAAIsjvIc2hNmEFoAQAARGJ3kOfQiuOvDgEAACKyO4jQAgAAiBK7g7o8tH7oFQMAANAj2B1EaAEAAESJ3UGEFgAAQJTYHURoAQAARIndQZ5Dq7NfWGrvAAAAQHdldxChBQAAECV2B3kOLd46BAAAiMzuIM+h1dn/VNreAQAAgO7K7iDPocVbhwAAAJHZHURoAQAARIndQZ5Di89oAQAARGZ3kOfQco5ojRgzzsVZadqsuA7ZOwAAANBd2R0Uymkmu6MchBYAAIAHdgcRWgAAAFFid1CXh1bfAYMAAAB6BLuDPIdW3FJCCwAAIBK7gwgtAACAKLE7iNACAACIEruDCC0AAIAosTuI0AIAAIgSu4MILQAAgCixO8hzaPH1DgAAAJHZHURoAQAARIndQYQWAABAlNgd5Dm0Zi4a65pBaAEAAATZHeQ5tDiiBQAAEJndQZ5Da078RNeM1tCaOvOnDtk7AAAA0F3ZHRQqYmjFRfh6B3tDhBYAAOiJ7A4itAAAAKLE7qAuD60fesUAAAD0CHYHfVNoDR89zsVZacqMnzpk7wAAAEB3ZXdQKKeZ7I5y+EJrXrxzZqyLP7RmdcjeAQAAgO7K7qBQ/tBytxShBQAA4IHdQYQWAABAlNgd5Dm0nC8stWcQWgAAAEF2B3kOrfHTYl0zCC0AAIAgu4M8h5b/rw7dMwktAAAAP7uDCC0AAIAosTuI0AIAAIgSu4M8hxYfhgcAAIjM7iDPocURLQAAgMjsDvIcWnyPFgAAQGR2B3kOLY5oAQAARGZ3kOfQ6uxntPoOGAQAANAj2B3kObTiOnlEy94BAACA7sruIEILAAAgSuwO8hxanf0wvL0DAAAA3ZXdQZ5Di89oAQAARGZ3EKEFAAAQJXYHeQ6tuKXjFTtqjIuz0uTpMztk7wAAAEB3ZXdQKKeZ7I5ytB3RsmcQWgAAAEF2BxFaAAAAUWJ3EKEFAAAQJXYHEVoAAABRYneQ59CK48PwAAAAEdkdRGgBAABEid1BhBYAAECU2B3U5aH1Q68YAACAHsHuIEILAAAgSuwOIrQAAACixO4gz6HV2a93sHcAAACgu7I7iNACAACIEruDCC0AAIAosTvIc2jNXDTWNYPQAgAACLI7yHNocUQLAAAgMruDPIfWnPiJrhmEFgAAQJDdQZ5Di693AAAAiMzuIEILAAAgSuwOIrQAAACixO6gbwqtYSNHuzgrTZo2o0P2DgAAAHRXdgeFcprJ7iiHL7TmxY9zzSC0AAAAguwOIrQAAACixO4gz6HV2bcO+w4YBAAA0CPYHeQ5tJwvLLVnEFoAAABBdgd5Dq3x02JdMwgtAACAILuDPIdWHG8dAgAARGR3EKEFAAAQJXYHEVoAAABRYneQ59CK+GH4qdM7ZO8AAABAd2V3UKiIoRUX6YhWmI0RWgAAoKexO8hzaEX8wtIwGyO0AABAT2N3kOfQiuOIFgAAQER2B3kOLT6jBQAAEJndQZ5DK44jWgAAABHZHURoAQAARIndQYQWAABAlNgd5Dm0OvsZrR96xQAAAPQIdgd5Dq24Th7RsncAAACgu7I76JtCa+iIUS7OShOnTOuQvQMAAADdld1BoZxmsjvK0fbWoT2D0AIAAAiyO4jQAgAAiBK7gwgtAACAKLE7iNACAACIEruDPIcWH4YHAACIzO4gQgsAACBK7A4itAAAAKLE7iBCCwAAIErsDiK0AAAAosTuIEILAAAgSuwO8hxafL0DAABAZHYHdXlo9R0wCAAAoEewO4jQAgAAiBK7gzyH1sxFY10zCC0AAIAgu4M8hxZHtAAAACKzO8hzaM2Jn+iaQWgBAAAE2R3kObTiOvn1DvYOAAAAdFd2BxFaAAAAUWJ30DeF1hBzxuasNMGs3BF7BwAAALoru4NCOc1kd5QjGFrDR7r4Q2tqh+wdAAAA6K7sDgrlC60wLeULrXnx41wzCC0AAIAgu4MILQAAgCixO8hzaMXx1iEAAEBEdgd5Di3nC0vtGYQWAABAkN1BnkNrwoxY1wxCCwAAIMjuIM+hFcdbhwAAABHZHdTlofVDrxgAAIAewe4gQgsAACBK7A7yHFqd/TC8vQMAAADdld1BnkOLI1oAAACR2R3kObQ6+4Wl9g4AAAB0V3YHeQ4tjmgBAABEZneQ59DiM1oAAACR2R3kObQ4ogUAABCZ3UGeQ4vPaAEAAERmd5Dn0OKIFgAAQGR2B3kOLT6jBQAAEJndQZ5DyzmiNdicsTkrjTcrd8TeAQAAgO7K7qBQTjPZHeUIhlbsCBdfaE2e0iF7BwAAALoru4NC+UIrTEu1vXVozyC0AAAAguwO6vLQ+h//898AAAB6BLuDujy0AAAA8JXQ6uxntAAAAEBoAQAAdJlOh9a4SVMAAAAQAaEFAADQRQgtAACALkJoAQAAdJEuCa3YkaPUp28//fWvf/UtCwAA0J04jeO0jtM8dgd5Dq1I36NlbyjUf/7nD/qxd4z69B+oAUOGAQAAdCtO4zit4zSP3UFdHloEFgAA6Amc5rE7qMtDy94JAACA7sruIEILAAAgSuwO+sOE1pW3JSr9eFe7F49zzft2IzV+4Xxt2L1O04bZ87rGmMS9OnX6jN+pQ1o1Lda1DL6DocPd0/6khs3Z2n0eIwaPke9j5NyVSlw0XcNCpo2ePV+Thrdfbtbs6Ro14jv/jEbNUcKske7pwB+Y3UGeQ2tO/ETXjOiF1mQdMi8ew376Rfce7PJNGzoxzjzQ57pMmzgqzPrTdXX91OD52Dna8TRXW3NydTl1Upjl25s3Nnh62NhxGhJmma8ZnXZdmzduUsamn5WxcZ3mT4zVoAmzNX/RkoDFmjFhhGu9bzXypwStXrNGScvnu+Z5cfL+Q13YFOeaHlHseE1ZkKC1a1O1dPZE9/wuNUXZ62dqoGu6ZdI6nX98yZo+UvMOv+zUzzOskTO1cGGc3tzf3qk4GTh8jEaa+1c49rJuk7X2+iNPjxGHe/0/2GPEcB4jzn0rKW291q5LV/y8wPPF6Om+x8y8BbM11nrx98rr/XxO0hqlpSZ+/f4VLYHHUlL6et9jqTO34+8Vt++F3p1O1HDn/Pjl2nf9gg68KtTN9dPa3Q5PSqtVXVOlkncPNHfSKN+8/ftSNG2Uf/7NwjKVlJZ2qKzwltZNdl9+qIFDYzU40mNp5HIdmPf7nzeBfyW7gzyHVme/3iH0wicvS1NK2pqwKivz9OTWEa2c+u2/vcTGn9H79+/1LkR+ZW3kJ89hE7Vw930V1xZoaMj0gWPmas2pZ8q7uVuLJ7Y/GvL+VabmdfDE77yITAozfdDMXXpa/cw13YuM++V6tnNW8HqMStTVtMmB88M1K/CE9y1iR49V7PCv/ZY6tf3ljk3VlfICczpWo5OylfGVJ89vM12bHxWFme43cPoOrW+9vGFxOnDocIiDSp/rv79M3pKjvOtrzIv0Ch24k6P7Dx76vSrw/fvg4RnXtj0Zu0hbzt3UpYMp5vJnadODYs1cf00fXh7Rwm+9/YcO15DhI9sMjh2pEQsP6UXVi7ZlIj1G1mQ++tc+RoxvfYyMWHH22x4j5r51ctlo3+lB07fo9PIxvtOxCedUWHZZSWPc2/Hiq/fzodN9j69xQ/3nhwX+7XKBx9LJZWN8j6WC6gfuZTot8mNpdtp2bdm+Q9fzPurqPv/phLmTNHjsKmXEzdCcZXEaEXI7JO8/rO0r/M/hg8ZO18QZaTqdMLZt/ujUqyqsKFZ+QYE+1VWo0PxbXvdJ1SWFvmmXU/2/lM2NX64ly+K1aMlSxZlfAmYvTlVhSa7und2vdYkLNSwQWvGp6a77fHLqdp3Z5J+enJqkGZ28PwD/SnYH/UtDq2OxKru3UeNd072YotTrhe0Ogw8YGqddryrDLNtqpK68K1fFu8vaMNv/xG7bfzdP+TfWh0wbpfyLKRoVZllH2BcRx/SdrtCasDhdG7dta9vnoVMXa+a4wIvCmDjNc15Ih45QxgMTWnvmmheMURrkzBu/RpkL3C+yg8bN0fL127R50xr/cub2XL5gmoaMmK5Fa7a0PTkNnbZECUmrtDRuvH+9ifO1LH6+4jO2aWPyQv/2zOUOGTat/eW2hZZ5kZ22XT9PDVzuqGnK2LJF6SsXBPdn6BhtMNPWrFqsSaNaX4RH+a5v2rL2b1f4RX5xGLrkpJZ+NWhGal7ma70+ssR31GnBytVKWp1spGjjuTdalZyqlasTw6z3dRvvlKj85QM9Lq3XNBMQIxZv1BATTIOi8cJsXuzX3SrWx/Or3PNcYjVj98t/6WNkfPwuT4+RCW23xSjNP/Lu2x4j5r51YmngKPWwObq30X/UbZgJw9DQGjhhnpatWOY77dxvJ7feJ4ZP0uaMRE2bME2zJ/nvb/b9fMC42VqSEK+5qZu1cV3gfjBpo+5U5br2ccDQ0dq0batSnfuquV5Tl63U4jlztXzmWI2ck6KMjSlhp4Vb177c6WNj2x5LznV2HkuPKx77r5N5LM1Zscb3WBrXGqrmsTQ1fq3rseQ8f3TmsbR011mdPXfeRM5zXTL/nj2XrZL6j8paHqcti4M/44Ejxmq4idT97yp1Z0Prc/gozTn4WjPGTtbokf7lRqdeU/6TnZoyNFYF+Se0YESssvILdWbFOA0cOlNXAqEVakLyWb0t/6jRTlwNG63YEWO0d6V9RDVWF5/mKi/3tW4dM79Qze0+b/+jZ7A76JtCa9Cw4S7OSmMnTu6QvQNhjUrQpeQJbefHL8nQxp83h3Upt0zX0vzLDpm5RXfKS3R1TchbIsbgeYf1tuJu2/kJi9dqy8FzuvWyUKXv7ujIxnV6uHm6ez86FKvJmx5o2Wh7elDYFxGHHVqTNyprif9JrbAoW8sD2ywsuqAVU+J1LNcfNM7Rjw2+0JpjwmdE25GHU2+rVFP8RMfXzg5sc4LKbm/QxMCLnT+0hquhsVAXU6e4jlhsflSpZ7/85Ds9eMFRfWiq8i0zbOFR7ZgZ67vcQb7QCrlc58WholkNTQ0quHMgsK3h5s7hj8PBcw4obbyZNiJeJwqK2y5r0PCRvut7p+Kj7/yIFdm+6xy6P197cRiTfkPTQ6JmbuDFtL0JWn0lTw+3zrSm+wOss2/PjEo8qwMLgy9AV4tqlXsuud0yq7Ou6tKVCI6mdRhHb6rzdDopeL+PyDxGTheWtZ2P9BjZsGl322PE4eUx4txW9mPk8Ity9350yP8Yqcg/G2aeX9jHiLlvnU2J0+SZC7U686k2Tfffp1yhNXO3npfd9p0ePP+IVo0102bt1rOad77Lnrjhrg4vCL7FFHo/HzB5k+7VNmmEs50pm7VtRqx/+yXt74sDp2/XoypneybW5mean88TbcqpVeWt9XpcX2aeoyZr2o4n2h1m2qQw69qXe6/8Wdtjqanhk++xlDjdicz2j6VXZbfaHktnV/iPIIU+lpznj848lvym6uGW4FvxGx6UKWfLdN0pfaO9c/2337zMN3p3cnm70Dr0ulKvM5do2elcvTm61Bd5o1MvK6/C//ZhWXWDPlW3fyvxoiu0pul9ln9d3/mJa3W94Jk2PSg0j91ZgWViNW3nM41rXWb4Yh3irUP8ydgdFMppJrujHF0eWmPNi2liyGdAInlQaZ4QZvtfbKeuP6vsnQsV226Z0Vpw9L1K7mxomzZ/3x3du3pKuzMCn8UY+tM3hdagGVt0t7LSFS2hwr6IOKzQGrL4hDYumK858xcqp+KJNk/zT8+4m6ecmw/04c7Pbcu63jp0DB2nuA3n9fr/b+9O35rI8j2A/w33zX36zczzzJ3pnntnekZtZRNE0NZuu1u7FRfWkI2wCYKACoiCIKioyI7YKDu0C/sesickBP6n761TlYRwqkhoh9BN+3vx6SFVpyrJL+fU+aaq4tid4gH8UEwK+ou3T6LswO2avI/vFe59kAUt/6WLuHS0ZvvvFVK+dHj0+Gn8VPEaqkTf8thv0dU/ivF3s77Liaeh61xC3uWziPaFI/Z+5y294vs9n1otvuftryn05JBg6A0ErcOnhYB85xL3eTPyoBWXlIw44Zt5ysOPC1pHzl5Hr8mCr4KWHf2hDK/Nzm1nbNIrm/CwcWf1laqtSSMgGnFX6zBYfn7Xr42NEdNKm2y5ksNnSgNj5NDRWIUxEiUbI+yMBT9GKt5aZPveiX+M/Fx4VrbOT3GMCH3LabHCajNj6cMr3xeF3QWt2Ox2GJd8l4RPl4QOWo4F6e8EDeouxiIqtVkIWq3bXkusqg1G/7L4bLQYV1E8bMNkbQoGbB9Q+UMMkoUwWamw7JzCtvzzthpnA2PpScZJcSwZl333FQpjKe3WE3EsmSxsTEpjaWX0kWwssePHx4wl0enrKGNfqHyPi4dMwrHwLK49nsL0U5V4TLk+sIqBG2fFoPWanWGM/g4rb8rxbYx0Fss4cU88tly6loYrqZJJ+xSactMDj0XXUvHtyaDLt8J7f5ImXSaWxOKcoRxHore+SDLsNoAz/mNXgipwlpOQg4LPQbsOWj+lJcpW7EXQOpysQ+uSPXCADS0B1rfV+E4hQPgdPV+JEds8Hqdv3Usg8yuC1tFvCtC24MRCW45sXTDFSYThgha792RmcgoTk5OYnPwZN3wHvQRdF4wbJnTotr4FKgYtn9iMZ1K4Eb75dup8l0gCYmDszccJhe1kQcvcLa2LTkGX3n8WRDloiX/HXkUnaxd9HmVDRmiuXsS3V6q37tuKOYvRBSvs5g94mntOfL/LrlXx/frf8/bXFHpyiNN0+AJjElQv5na4LJWIzJZZjNz+Qfhsk3C1dhQOhxMupw0rRvO2+4t2JS4FlWNmzLfpZeuiL1bj7YNUKeR+lDiczm3DrMuICfsyuq9/FzZs+cfISEX4m7vZGLlUPxFyjDC7GSO/Jmj5x4j/niclimNEnHzlryNU0Dp6uUkMWmzSX52pl7ZJNIQOWpZ30t/xajwQ2h35sQ5Tlr5tzxmv74F54bH0OPYaGhcsuDFsxmjF9xiwjKH0bDSShFBVpbDse4Vt+edtCQpa4uVSYSw9nDcHxtJM711xLI2YfF9+hLGUVtkuG0vBx4/g1x9uLDEnC19vO0N8+50ZPxecxlc/3sP71Z9hSBY+y5Vp1F6KE4PWmwoNSnsXceVENI6eSUHcN6UYWB1G8RmhnXgf5AD6h6cxPTyAN/2S/vFF2FcnhXUduBEI/IKkAtSnyG99kElUY3noOWpqGtE1sYzB0m9lbaKTv8OZU8qXtAn5rfE56DcKWjGI/SYNRU9GMfE8F1/vcPNswLHjqBcORG7n9I6BLO5cFkpb3mKoJg3HQxzspf2FCFrHYhB14ixuNb8RDsRuPM77QeFeCDnFSYThLx0eT8d4TYr4i5+kC98jXlwuBKOx2/gm7hJqJsyB96jrMeLD/YviRCyGnkQNLiSyb3+xSNR3+n7Rcxz2qcdIS2IHtBicipX2t/IyFwn8axHeG5uAfqm6IO5PunToQnxUPM6V9UOf5G+bvP15A0ErBvEZzbj7o/Aazt3G2OobHIo6A03rghS0hAkjM/cq2Bmb2NQnmF3tEt/vowWH9AunYwnie95eo9CTA7uPRQpxiUh/OgvDxbOIjZVuJE++kIZr56VweKpkAAsv8xGT9QKLU3W+7U8g4/kc+oSwNVJ9WXj+U8gS9rFmHZI9z68Rl9qA904r+kv8lzt2Q3i9mfeEz7kJqqCb2WOv1GLcZlQMWx87Rpq1ymeV/GPE5DLtaozsGLS4MeI2/fLxYyT4Hq0gR1MaMWvugdZ/9lSYpF9ZZnA47iJuDdvEoHUoUY/2VQdOJV1AbsvkVtDi+rkUeHw/OPAFLXbGSNu5gp8SYnD4WBzOs/2dNKDLvCKMvxic1HdhRXj+G8MmDN08J4Sq0aCgJV+WrLAt/7zBQYuFSzaWZlwTgbFUeDZGHEse50BgLLFfXQaPpSZhLLHjx8eMpSPfV2F8tR9RyWcR7+tPsxYpXG21S8DowwzExJzBstuFicdqnPSF9jhtF36ISoSqdR7v7gnHh/Ol6J35gM7GR1gwGrE8+xZm0zjqMk/vcJyOg8PYg9yzu70UGItTeV1I426AZ8eEH9jrj/kRN78N8YMHQn4jfA7addDaq0uHJ1R1WDDb4XKaMdX3cIcByUSj/mkHXo1Ow+hwY7C5BD+JYSKozYlrKHncgd6RSTjsK3jbUa149kdmx6CVgLRnS/BuePCurxnl6gsKbZSxG0gVn5sPWoJfLGtwWs2wDJXjDJvwkvRo00pnsk7mv4LaF3iSCl7BKBzsrGazcIATlsVfht3lhMPhEOq3EpjcKgdXsbZmh9lixxXxRtUYLPXwQes0DN1LwvZurNmFiSrRF7RWB+F0e+BdNwVN9tHbn1eYHNpNHthtNqHOy77Q9DV0bQtYtZjx7tlTKQxF/YjyASOMRhPsTmEyqpJusD+e9lB8v2a7U3zP22sUenJg9yY1XvXfLH0GH1ad8Hi9WPesw7o8hVe3pH/mgl0Kmp95KLxWNZ4tmJGr08NQ1YUZ+zSOnSvEg/saaR/HzkDbvgjNqf/kAB2N4+e+Q3y4sBLk+6q3sFk+bPtVl1/ctQZ0538T6D9sjHQPT+xqjHytuRt6jAj4MZL5TfDlmx2ECFr8GIkLc/bMT3GMCH2rUSFoHUrUoW3FA5fN7Avap6B+MQ+n3Yjhli4paAnvP1HzDF6PBePNTb6gJe/nLPC8Nm8FHn8gO5yshss3nqT9xeB0QTdsVptQ+0V0FJxDsRBe2T1NgVBVNIBKhWXJCtvyz9uyIgUtNpbWXA5xLL2pZF8ApLFkt5vEsfR6qT8wluwOi2wssePHx4yllIYpzLdpkd48KzzXCiaG+jH7OFN2dvZiyXOMm1zo+WDD+N0U8YtNVNwpXGucRqJQ86QrWlw5lyi87mgci09G8vk0dI7Nw2SeQ//MKiymOQy1VCr223zhs1lzzsOgViE1UwNNnkrWhlEV3cOL0UVYjQpfis6U4hL7McTxq4FbLwj5PeFz0K6D1knhgMKv+JigRX4/xKBl6pItj7TDX6tQercGVUH4NoSEdxwJp9kZzRjxS4mG/SBD1uaPLeJj6Rg77sfiyDH5F5Mj0XEhf317PEEe+vfKkbgkHA/8EpOQ3xc+B+06aLH/8CsoaB1sv1XQImRvnIah14Qlow1r7uAzsoQQ8tvhcxAFrU9ZzAnEn9zNv0pOyO9UVDzO/3geyRE8e0IIIb8Gn4MiHrT++e/DshdBCCGEEPJHwzIPn4MiHrT+/n//kL0QQgghhJA/GpZ5+BwU8aAVFRuHf3z5Jf7617+KbQkhhBBC/khYxmFZh2UePgdFPGgRQgghhBAKWoQQQgghEUNBixBCCCEkQj4qaP3lL/+D2PgE2c4IIYQQQoiEZSWWmfgcFTZo/e3zL/BVVLRsh4QQQgghRMKy0udffCHLUWGDFvu/Zvjb55/jX/8+JNspIYQQQsinjmUklpVYZpLlqLBBS/DlocPiDlhao8uIhBBCCCHS5UKWjVhGYlmJz0+7DlqEEEIIIeTjBILW4WMxhBBCCCFkDwUFrWhCCCGEELKHKGgRQgghhEQIBS1CCCGEkAihoEUIIYQQEiEUtAghhBBCIoSCFiGEHHD/++UhfPanP+O//vsz4sPqwerC14qvG7/dp47Vja8TXzPqa9uF62sUtAgh5IBjB/srqRlQ6XKQrTd88jKytWI9WF34WvF1Y22pbgaxBv668XXia8basLb8Pj5FrG7h+hoFLUIIOeDYQT41MxvZOgMRqLQ5Yj1CTX7+urG2/PafKn/d+DrxNWNtqG5bwvU1ClqEEHLASZOfSpz8iITVI9Tk568bv92njtWNrxNfM+pr24XraxS0CCHkgGMH+WsZKmRp9MSH1SPU5OevG79deDlQ5+RDo+eXR1qOwrK9x+rG14mv2W/V18bm5zD8pGz7cn0+9HmFOzMYZPvZa+H6GgUtQgg54KTJLwuZGt2+ysopwo3qB6hrbEJBbs7WOm0BCm5VQu17nF1YgfI7VSgrKZDtI1JYPUJNfv668duFo6nph3nDhV+arsvW/Ro5N28hVy9frqikFTMel3w5p+xRG1peNCIzrxINre1oabwtaxMOqxtfJ75m+9HXhhen0XY7D/0zM5icnhbZ1r2wLUuPp6Yn0FNbCFXFSyx5N7G5qcw904IChf3vpXB9jYIWIYQccOwgf1U42GeotfvEgNKOOSwPPUFpvhCw1DrU9M7BuemFjq3XVaJndQO57G9DJby2t2i8oVfYT+SweoSa/Px147fbycv+IQyOjOP91JIw4W9izbKMVbMFFpsdDufi9vbaUtzvGoRBYT9+eXfbMbKyhg0hDHTcv4HswLpcVL1ZxR3DVlspaLlR1fAULb2DGJ1cgMcXLu7kbLWrG3dg0zKAjNw6DNo2YRt+IHvecFjd+DrxNduXvmaoRuf8GhrvP0Sd8L77Ftx40NCIxt5ZvHzUiLr6eygSapRV3oNlIfhK2+WhetCKMp1/PyVwTz9HAb/vPRaur1HQIoSQA06c/NKzxF+C7YvrzXjv2kQem2gCy/NR1W9CR3mOEDR8QUt7E4/fO9BSLv0ScD+xeoSa/Px147fbyZzVglWjEXNzizCvbcK5/AEDAwPo6+tDT08X174QD35xoFwrPdYX30F1Uys6n9dw7XJxvf5nWEcfIse/TFeNl0YvDMLfuluP8XZmGSaHRwxkLFh5PS5YVubR+aId/YtuFAV9BrVjvqBlCApa3PsIh9WNrxNfs/3qa1mFlcJ7smNDeM82ux2ejU141hxwrHmx6RjDvUDQWsfU9IxoxujCtO9vRgxaCvveS+H6GgUtQgg54NhB/kp6JtJU6n1xvX0B3vUF2fK0vCaY++9CpbmDbuMGPF4zBuoK5e32AatHqMnPXzd+u7DUFehY9sI99Uy+TtC3YIHDsyGGonWnCXMfRlBd2YBXK+uwjTyQtd9GU4ZnM2vYtI5Ij7M14v+mF7/AtMcd1FaD1XUvzEN127ZveO+C19iLtJxaDLCg5V9vqMdMaxky+OdTwOrG14mv2X70NbcvWDaP2+Be+AX9Y29hdHtgmnmHvvFFeB2jqMlRI7P8JVY2XL7tDKgatKJU499Psfg55Snsfy+F62sUtAgh5IDbr8nPr7B1HuveRdnytLxHML2uloLW6gZGzetYm+2St9sH4SY/f9347XaSLoSeDLUOWdpSPJ12Y32xG/nFpSi6WYHSW5VQ+do9GhhBb3sz7j7oxdSzYqQLy/KbJ+DcMOHnKoNsv8Fuds4LAWMNE09Ltq8ragkKWjoUNr+HY/IFirTbt38+74F7tkUWtDLLezDWkC97PiW/l6BlyK9ClxBoxaA114Om1kGsrHlgnBrH/Y6FQNDKut2H1U0nrpfexPUbFagfsaKqpFR8XFhcSUGLEELIf06a/DKQqsreF+q6EdiFyY1fnlXZh8lnRUjV3BaDVmFFO6bXNpCnlu8j0lg9Qk1+/rrx2ykrhmd9HV6vdKZKSS6/Tc596eye8Pe8ewPW0Xro+DbBsvPg3NyA7e0j5PL18gWtwGP9beRp5Ptg4co++kB8bilo1QrLtSjtWUZDgby9ElY3vk58zfalr6kr0LnixRMxaHWj8dUSnr9oxfPX06hlZ1SFoHU3JxvZ94dgE+rPPh9mXfiM/H8z7uln8s9mj4XraxS0CCHkgGMH+ctpGbiWpdo32rphuJaG8KSmHHmFReiZtmNDCF/pbL36FrqMG9CJbbVCgHBh4nkpMhT2EymsHqEmP3/d+O3CU6O4axkbnmmFdcH02LQO4o6OXy7JqajB/Sft6B2bke69ci0JoUzeTqSXglNJfi6y9TnIzslF7o0ylFbVSvUWZN54gg3rKGpyWft76BfaW8eaMe/awLppQL7PHbC68XXia7YvfU3oQ53LXrSP2QNBq62jE619U9Jl2eVulKhVqH/vwqZ9xLedHncGrOJy6fF1rE09hYHf9x4L19coaBFCyAEXmPwyVfsoG6PLTqxvbGBDsGaeRFdtkbQumwUtL3S+tnf6VqT7tWrzFfYTGeEmP3/d+O12I/fpjPB+lmXLee71OTwtypYtZ+6zXwiygOW2o63hFrTZ8jZb9CjrXpCdRdvc9CJLWJ9W1Iz3zk10V+VK7XVS0GJtrJPduG1Qfg1Kdh20FLbdSy/nhQDlscBtmcVwbxseNzXhTmUVKu7WobahATU11Sgp0GHWswnb6APfdr6gpc+Flv37WboyrE08QY7C/vdSuL5GQYsQQg44afJLx9XMrH2XpjVAm88C1PblqdmarcdZ2UhXa5CuUsm2jxRWj1CTn79u/Ha7oakfh2PDLFvOez85htZqg2w5k5lXBL1Bh7Qs+bqdFN2qwq3qalRU3kF+YQE0Oq1vnRoFtY1bbXUVqGt5hsaGu7LPJRxWN75OfM32o69Z7VN4cTsHD3vfYnbVCofbIwZ6v81NO4aE4G5dW0DrTbVvOx1uvzbhZkUXFn3//IXpTbUQRuX730vh+logaB06GkUIIeQAYgf5lNR0XMnIJD6sHqwufK34uvHbfepY3fg68TWjvrZduL5GQYsQQg44afJLw+X0DOLD6hFq8vPXjd/uU8fqxteJrxn1te3C9TUKWoQQcsB99qc/40hMLC5dSyOCC5cu46vYOLEufK34ul1IuSLb/lPlrxtfJ75mrK9R3baE62sUtAgh5ID7+z//LR7o2bdqImH1YHXha8XXjd/uUxcqMFBfUxaur1HQIoQQQgiJEApahBBCCCERQkGLEEIIISRCKGgRQgghhEQIBS1CCCGEkAihoEUIIYQQEiGBoEUIIYQQQvbe/wNalJevWGWL7QAAAABJRU5ErkJggg==>

[image3]: <data:image/png;base64,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E0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRRtAAAmihaAABNFC0AgCaKFgBAE0ULAKCJogUA0ETRAgBoomgBADRZFq3nP/+rpwcffFBEREREhjzwwANT9KUoTufN/wchHhDVdWkTSQAAAABJRU5ErkJggg==>

[image4]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAloAAAA4CAYAAAAl+FaSAAAI10lEQVR4Xu3dzWtUVxzGcf+KQrf+CaV05abd9GWl4Ka40lXpQtyUglSQVhfiIgQbRItEkFZQF2mLCELjyqhgSOsiYLW11FEMmqiRJmnT9pTnwjP85uTcSTLJTabk+4HDzJx7Xu5kAvNwzmXutrT4KFEoFAqFQqFQ1r9sSwAAAGgEQQsAAKAhBC0AAICGELQAAAAaQtDq4sKFC3kV+sCBAwfS9PR0Xg0AQN/pCFq3bt1KT58+jVWbZm5urvpC3b59+6q/VNV+165dVV+N04ubN2929F2cfpZ++uC99HLsevV66puvqyJzP99Nv3z6Sbtt9M/cH+n6669VfTWGaAzVuf9qqI/6qvhcNLbrdC7mOpU68bzufvxRdb45Hdcxt1srjRP/dnoferz95hvt89V8ovPxc9Nno/+NXj9bAAA2SkfQWlhYSOfPn0+tVitWF8Ug5JUf1el1rBsaGkrDw8MddXp0O4eoUl/R8Ri0jh071m63nHv37nV8Gft8Y199abtux44d7TrNE+kLX2HKQaYuaP125PMlIaouqORtHJgcoEo8r9pP7vmwmjuOrbo/W78vCSd1Hn91Oj377ttqTo+jMR14PJeP6dGBzO81Bjm19/uoOweN/3BwIC20Hlbzx7+Dj0WaJ6fP9tChQx11hC8AQL9ZsnWosHXixIk0OTmZH+qgIJJvrTmcOIS5Ts/1xbhv374qNJW2fkp9JQ9aMdQpEHWTB628r8bVOUl8P3q+3NhxZcmhIoYvvXZgWknQiu0doEo8h4ORV3w8tkKJ+noMrxLVefXjRBV2FG7UN56jw2U8/xh6fP5qF1f64rmUeBXLIS/+HfJzqBM/OyNoAQD6Tc9BKw9L+oKLKwx5aIkBS49aPVIQ6tZXYtCKq14qy4WhGLT06PlEc6w1aDkgeEVLYSSGr9UGrRhQ6la1HPDill/cOlTocdCyusAjaqsx1cYhR8XjKajptecwb4nm7zW+pzqaU2M6DMY+K+kv+f8MAAD9qB20FLBOnTpVlZVQWKpb0fI1Uq7Lg1bkQFPq69exT76lZwpu+fnUrWhpPM1b2n6S0tZhrhS0HFhyKw1a7Wuu3n93RStaCkH51mFs5+utSuckDmXmrVG39xzx/L2KJqVxVxKU8hDpcUrj1Sl9dvq/yf+/AADYTD1fDO9AFK+pUl1+nVUpaCkUuZ2DUN43jq/ibaF4nVX8Uo1BS1/CcQ6Hpjie5ON5yzKudNUpBS1v48UVp7g65BUnr0rF1aC4zZcHkSjOq2Ci56WgJXGOkrqgpaI+el3aOvR7iyt4nr/XoBXfv/9+3ZS2rvUZLrcSCQDARlqydbiVxJWrPFzpGNf79Cd9NqXrsXwNIAAA/WJLBy0AAIAmEbQAAAAaQtACAABoCEELAACgIQQtAACAhhC0AAAAGkLQAgAAaAhBCwAAoCE9B614i5rSrXVMv96d/2K3f6E93jx6pfwr7v51d9G5uK706/B1t9PROamNqF+89U9uvX5x3L9Gr3Pyr99r7vgL9fE+kAAAbEXxloATExPp6NGjaWRkJD1//rx9fH5+vnp++fLljvZqu3v37qqor5Xqcg8ePEh79+5N+/fvzw/1ZN2DVh54LA8q+b3q4g2j875RvN2Pw4jPxSFGberCVaR2Q0ND1TgXL16szicGtHgePn/VeV7VOTBqbo+n8FT65XLxrYiGh4fT2bNnq3+OeK7qUxdaAQDYKhSWHIgOHjxYBSCFqdHR0apejw5dEoPWwMBA1d4UyFQnDlKm13nwUp3mXA89B624suSb+TqYOPBEywWtPCzV8RzxFjnuqzF1Gxb19/FuK1oaS+0UetRXISly8BK1U/GqVzx/Bzuviulv4Xs85nzszp07VdDK5+0WMgEA2CriKpVCl8LSuXPn0qVLl6rHJ0+e1AatuKKlfmrn4KaVKvW3vg1a+YpWq9Xq2P5SifLQEYOKAlEMXd3CRgx35q1Db7k5aIkelwtaXn1S4Ik3s45beDFQum98rw5a3c5dHLT0qLlj0MrDJwAAW5XDjkKSQpcoIDmAOUBZDFqR6h20HNg8Xp2+DFpxRaukW9ASj+egUyeuaOVbh6b6nTt3Vo/dgla+6qTXDkwSg5bn07ji1bNoJUHL79urcX7d7TwBANiKFIi05adwFLf/RK/j9mApaMVQ5Uf1iddf/W9WtBSQ4nVWDktebYorRL4GyitBov6u6xZW4jE/LwUUBZd8jlwpaMXzy7cO/ejncVVLdWsJWvlqYB5MAQDYahR4fD1VXdBSgPI2oS90V5Dy69i+dDF8HrQ0n9uVwttq9Ry0AAAA0B1BCwAAoCEELQAAgIYQtAAAABpC0AIAAGgIQQsAAKAhBC0AAICGELQAAAAa0vdBa3x8PM3MzOTVAAAAfW9J0Jqdnc2r1oXC0smTJ7uGpitXrqTDhw9XxdYatDSmCgAAwEZrB62pqak0OjqaxsbG4vFaMTT5LtgKNLpho4KS63SrGbVV3fHjx6s+Ck8OVL4VjZw5c6b9OvaLQWtkZKQ9h6mtx9PYEucgaAEAgM3QDlpXr16tQtbi4mIVuvRaj3XqgpbqVAYHB9vHXO8+MVDpuOoUwhyMFKTM45nDmsr9+/erOs/veVWvR71mRQsAAGyWjqB148aNNQctUYhSmIrhKj53oIorXxIDmOVBK86hQFUKaTFcEbQAAMBm6bhGS9dnaftQYWs5XjlS0KkLWt7+0zae2ng1yqtNuV6ClsSwJppP86qNgxcAAMBG6/lieIUXryDVBS3xtVLXrl1rr2i5b7ymSmLQyleqHJxKQSuukrmdr+/SNV0ELQAAsBmWBC0AAACsD4IWAABAQwhaAAAADdn24sWLRKFQKBQKhUJZ/8KKFgAAQEMIWgAAAA0haAEAADSEoAUAANCQjqB1+oeFdPfxP7EKAAAAPWoHrdn5lN7+4mV658jLeBwAAAA9WrJ1qMD11mcv0/fjf+WHAAAAsAoELQAAgIZ0BK1HM/+mPV++Srd//TtWAwAAoAdcDA8AANCQ/wDqp2Wp1xXQqgAAAABJRU5ErkJggg==>

[image5]: <data:image/png;base64,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>

[image6]: <data:image/png;base64,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>

[image7]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAloAAAFNCAYAAADYYMFUAABxyklEQVR4Xuy9Z3cbSZq2WV/27H7ds2ffd87Mzkx3V3dXyVS1m2lTpsu0me7qKkk0IAxB0IPeeyNSJGXoJHrvvRVF0XsLwv+D/jH3ZiSQIJAJZAIUKVHS85xzSUQ8EZGZRPDOOyMDiQ++V38Fxtd/+y2++utv8Z3qKwn3tH/k6zC8y4UyhlCH/e8Poa13H97t72i/8dQVb0PcF6vrvV3v/fOGHZP4WEI5HmE74u1f9jGFcjzi98hoNOI3v/8E//3ZJ/ivP7hgrwWEMgZf57NPPT/7Q2jjrz1r613Pu464H2E73jm2r8Eck4D379jf7/d1vkf+3ifvfgSCOR7vfRHvz2Uc00WP5yqPyd/2gz2eV3mPQj2mYI/nVd+jYI/pVY/nMo/pMo7nKo/Ju20wxyO0DdTHqxyTdz8CoR6PeH8u45guejxXfUzi7Qd7PK/yHoV6TKEcj3j7H7ACCgoKCgoKCgqKyw0yWhQUFBQUFBQUVxS80WJTXxQUFBQUFBQUFJcbbDKLZrQoKCgoKCgoKK4gyGhRUFBQUFBQUFxRkNGioKCgoKCgoLiiIKNFQUFBQUFBQXFFQUaLgoKCgoKCguKK4tUf7/DPVhhbN9BqbMU/xTkWG638QypZHQoKCgoKCgqK9yle3Whx9qqVM1IbG0a0+nFaGywH5sda+f8vHFz/n/nbgCc2YPwsgNnzG9x+f+baNwoKCgoKCgoKIT744ANxkSecTqdsXhwhGa0N4wd85974mB/ODInzfB3PjBYzN9K8pB9x/LMVn33wmV8j5wm2baNgm5jp8m/8zoOMFgUFBQUFBYU0mJliiIOV/R//5//lNxcoeKPF/rmqYObM4394cyM1TP9s/UzGaHGm6QPvPtzBbll63a4U9/HPDWbOfA3chtF722S0KCgoKCgoKPyH2FBdxGSxCGlG6yIhNTehGC02M8WZLL85ZqaM+Iy/Xei/X749Z8ZcIa5DRouCgoKCgoLCf3gbq4uaLBbsS6Y/+Hvkl+JyaQS4LSggmXHiQ2xmxGbHXerPaP2TmSyunMN/365wma3P8IHS+ix2+9GnjnAbk9sGt4F/yjamoKCgoKCgeN9CMFgXNVks+Mc7BGW0ROF7SzBA+DU3ykZLME+siOWUtsOvHVOoJN6GtwlktxnZzNlnxlZskOGioKCgoKCgwBs3WlLDJA7/5kbazqceM2eitVeyHspt5lqNcgvq2Tov8W1C6WzbRitbtB+oDwoKCgoKCor3JS7r1iFvtL5TfSUuVwj/hsk3XJ/8k5obaTupITsPeaPl6s+VZ2ZK2jcLdotQ2r/YaFFQUFBQUFBQuEJsrC5qtvjF8CEbLcktQXF4GyBpudjzXNRoSW4Zbhi5uuJ+/smvwZIGGS0KCgoKCgoKaQizWOK4iNkK6VOHrrVTRtl1TJe9zsmv0WL7wRawi4rPw72QXnaROxktCgoKCgoKiquNkIwWBQUFBQUFBQVF8EFGi4KCgoKCgoLiioJ/jlbIa7QoKCgoKCgoKCgUg4wWBQUFBQUFBcUVBW+06NYhBQUFBQUFBcXlB/8cLTJaFBQUFBQUFBSXH7QYnoKCgoKCgoLiioI3WuwfCgoKCgoKCgqKyw3+1iEZLQoKCgoKCgqKyw/2gUMyWhQUFBQUFBQUVxC80WLTWv/zjx8IgiAIgiCIS4Q3WuwfcYIgCIIgCIJ4NchoEQRBEARBXBFktAiCIAiCIK4IzwNLxQmCIAiCIAji1fB8BY84QRAEQRAEQbwanudo/fW77wmCIAiCIIhLxPNkeHGCIAiCIAiCeDVCNlp//tt3+PV//Tdu3rqFDz/8ED/60Y8IgiAIgiDeaZjnuXnrNu+BmBcS+6NAhHTr8PM/foUbN2/i9ief4Nu//BU/3AuHWqcnCIIgCIJ4p2Geh3kf5oGYF2KeSOyT/OF5Mrw4IYa5N9bx7//wGcJVakTpogmCIAiCIN4rmAdiXoh5omBmtoI2WmyqjLk4MlkEQRAEQbzPMC/EPBHzRmK/JCZoo8XuS7IpM/FUGkEQBEEQxPsG80RsvbrYL4kJ2mixRWDf3w2TuDqCIAiCIIj3DeaJmDcS+yUxQRsttuJevBGCIAiCIIj3FeaNxH5JDG+0vv7bbyUJMRc3WgnIbZnHzqkJR2sjeJAR66cOQRAEQRDE20UwRot5rFc2Wmq9AdoY/xhKBrBj3cF4SxM6Fw9xutSAZL5dEkpahzAwJE9/Szni/GwzZJIfY/bEjDPLCeYepUrzftDEG5GUkhoUCfEGSfvXjTavE8s7LzEz2ou6vHhJniAIgiCIyyNooxXsrUOVNlpKdC5a1q1wOBwBcMJ5MoOqpDhkta/jbLMDGdGsbTKqZ01wOp2ymGYfIk68zYuQ9BhzZtanGQuPU6R5PyQ2vIDFzz5JcWCrKx9qP328TpKbXrr292wBtcnSPEEQBEEQl0cwRot/YOmrGq3WDZsf8yGCN10nmHuSgSi+bRIKm/vQ3atAcxlixdv0RmdATGouUhL0/GtNQhqMqamIizP41ruA0UqqfwGz+Dj8Ysd6W7b7uAKjzu3CptmMk6VmGP3kXw2jx7ja1lqRphPnCYIgCIK4TEIyWn/5+z9kYZ1FanR+MMCQkgFjupTklBzUTB+7Tv7r3ShI4syPpH2IaFNR0beA9f01dBZk4uGCCQ7nKSarE/l8XN08TNz2jieroPdul/jIy2ilBrcfOnb7MzYg0emNWLS4+3yU4tVWj9isEhSWlPpSM4QthxOW1W6UF5VCr/WzzYsSdx9jx2xfHNjuKYBGnCcIgiAI4lJh3kjsl8R4PnUoTogJbLRk0Gbh6bprtuvEx/gkoWpyHycnJ8qcHuNlay6iPG0NyOnd5cyVDWudJchrX4OV6/9gpBzRXD6p6SX/+nC4DDrvffEYLQ67GYcbCxhqe4iC9ESoxfsdJNqiIezxM1p76C00eOViUTh06Gfmy5dUwWhpYxGbmonUjKygSElNgla0L7riYezz/R5isCTOXR7NmcFKPHlUyP9uxPtPEARBEMTFCdpose86FCfEXMRoqdKf4qWVnfwteF6f6pVLCmp9lgsbVp9l+sxARZeN4pDLmZcaYMzrxrbDCft2D7KiY5E/eAB2K2+tNdt31srbaImwne5gcaQN9/NSoA16likWef17nOHj+jiZRHm8d86A9AdtaGlrP6d7Eutnru1Zt6bQ0d6BJGFb0fno2LJL9isQ9q1u7lh99yV/YN+1L0fjKIllZTHIbFt3rdkyLaDWKN5/giAIgiBehWCM1iXcOgxEPAoH3UbEvIRHKd45PfQpWUjLzA5IRuUAtuzMWBxjtCLet+/Eh5hlpuVkGvdTyzG0d4rdlXHUZeahbZMZliOMlIvbnN86fDHQjv7ZNeybpebGutGBTB8T4x9VyhPMm1xtDscqfW9T+hCDxPtD2OBvMbq3sfIURm9D96pGS1+Inl0HnzuerEaMUJ7MHTO/jzZsdOXT7USCIAiCuETeoNHSI+HBJPZ5o+TA/kiFjBHxgy6dX3vFGwvOTFUmiPLaRCSlG6HT+ZbHVo7jgG8jnmHS+a7RemR092NAbFYlHvfNYu3YyplCOzY68pRvJcYVo2PN4to/ywqaM2OkdRj6dFQObOCM1XMcY3F4mp99kxgt7veli09CXGJyUMTGx3rdStVBW9iPXfbpTucJJqtca9VccGZ3yD3TdTyFCvHvkSAIgiCICxOM0WJ3DYM3WmqtIprEAtQNrcPEn/idsO8OoyROWi8QmuQytD4/hp2fvbFgpSUHGj/1fNEjvrQHK/ytORs2OvOlbRIenhuth8l++zBklqMwPcZPzoVKn4L8+mGsnLhmj5zOUyw2ZEAtqRuNuOI2zB241qc5Tl6grSgJupxufjG89WUzjBpxm4tiQP6Ae+bweBIPMjKQmV+K8pp6NHcOYGR2Ayf8e2HBUkM6VJL2BEEQBEFchNdntKLTUfykFZ3DM7C6DRbDsj2CSmO0tL6HWCQVVOL+wya09k/i+faJV3sb9sZqkKgVt3ETk4Ls0lrUd41jaffMZTQ4TC+eIVPvp76i0fKPvvAphqYWsbJzAovXsTlt+5h8kgWtnzaM2KopHHHmZneqCblp6UhNTUFicZ9rRoszWsl+2oSKKr0ZSydnsPAzh8qwdWw5/n43BEEQBEGEzOszWuoY5LbO4/ncBEqzjdAFPVujQ2rjHNbXljE/NYzOploUpCf4mSHyhxGVPWPo62jC/cIMxOjEeREJdZjcO8TB4S6m6ozSfCBiCtE4OIiO5kcozUuDXmk7ftDnPUZrVx/6BofQ39uCyvRYSZ0LEWNEWkYGko1GxMXHQcceBCuuw9Bl4UFLPQqMBv95giAIgiBCJhijFdoaLT8bIQiCIAiCeB8ho0UQBEEQBHFFXLrRilBrCIIgCIIgCA4yWgRBEARBEFdEMEbLsxj+z3/7ThbWWXiUmiAIgiAIguBg3kjsl8SQ0SIIgiAIgrgA18JoffH1N7jxyaf4jw9/hv/3X/+Nh/3MylhOXJ8gBMRjh8YNEQzicUNjhyCIqyJoo8X+ESfEhGq0vvzmW3z48Q38P//yr/i3//wx/pMTug9//jHPj7ifWRnLsTqsrrg98f4SaOzQuCHkCDRuaOwQBHFVBG20LntG64uvv+WuIv8/Xtg+/OgGPr71CW7c/hS3Pv0lbnPc5K4sP+Ze/5TLsTqsLmsj7od4/wg0dmjcEHIEGjdvveawBbfiMiUu0uZ1oNZBpfFTThBvMcEYrTvab/DB3yO/lCTEsM7CVGpFvAXvo5u3OLH7BS92/mC5j27e9hE+cX/E+0OwY4fGDeFNsOPmomNHl1+Pto4WlCRrJLmronVuHi21rVg+XkVzuk6SlxBXHHqbIAnq+NV6qKP1vME7L9ciUmtARuMslse70b9xhNmaRGlbgniLCcZo8Y93uEyjxablmYj9/MYt7iryFzxanR6FRcXo7etD/8AAyisqodPHePJMHPkrUa6tb38aJFS2o6unBUUJQlkschv60N3bg4e5MZ66CZUd6O5uQl6sq07JwAa25xuR7POHHwzxKB/ZwPpIFWIkOeIq8Td25Ag8bl4j2mTk1Lajf2IW09MT6Gt9iJzEaN86+gyUPx3A2MwcpidH0NFYhfS4yzsRvu+EOm5CHTvaikmc2FbRkCJjNEJGC01cMuKSjH4pG9zB4Vw7mif3cTBZDYNC/diEVD9t2HbiUdw+htGx8YAMt5ZCL9m/c4I5/piaOZjO5lEd71VuqMLEqRUr45PYPp5H19Amjubq3PtFEO8Gb8Ro8Wsg3FP3bLo+Lj4BI6OjmJ+f94GVsRw/pX/rU74Na/v519/49KcuHMKB8wB9BXpXmSYHbVt2OJ1WLDemuuvFoWziBJaXTUjijVUsinuX8XKq/mJGa+oEJ9MPyGi9Rtj7Lh47SsiNm9fF9IENDusx1hanMD71HOvHVjjth5h6mA4VqxNdiK5NK+ymbSxMjGJ4cgEr+8dYbs5AuJ/+iNC4yLgRjx1xn/GlT9HS1n7OwAucWLcw3ulVxtFYZpS0DZqoNDSsWCVf/O6D5QXqiwqQa9QHV1/cht9WAsoHOS1cWQnI0kCVj9EK5vjFxx5TO48zzmg9kBgtG1baHuB+fQ3yikpRkB6PSPHvgiDeYoI2Wt+pglujJd6AP1zT97dx4/Yn0On1fk2Wt9nS6HR8XWE6/2NOBH36jHuAKZMVL5vSXCemxCdYNO9iefkYh+P3Ec3KNHno3LFjpyffdXJ7JchovQnY++49doIl4Lh5HejyYd0eQkmC9rxMnYTSkV3YbZtoz4lGlPtCob/wfPaVzWZEqP30R4TMRceN99jx7VOD5GfrsFuOsbOzg+1tP+zs4thix9qzdB+zHGUsQHFZeUByPOaHEYPY9Bxk5uT6pbR3A/azOVTFBVc/MzvPT5uLoHD8omNPfDyLje1tbB+cwW49wR7385YHVtcJ89EO/3p7tRf50eLtEcTbTTBGi18Mf5lGi3265yPuyvJjTsjKKiok5kpMQVERX/fjW7f5Twmxj2H79BmViifLFhxPVvGmSlMygsPTKTR3rsK604NMDVcnqR7PLScYr4hzt3PdOtxdaOZntOb2V9FR8wiDKwcwmU3YnXuKDM8fvAaGkm4s7p1yV2THWB9vQ9vcsY/RikqrRd+LPZycneH0cAPjjXnQcuXxD2ewsz+PR/zaBc6gjW5id38TgxXxfL/J9QvY3RpDeWwccp7OYOPwFCbTCQ62nqP/Ybbkd/c+w95377ETNIHGTXI9/773NHdh6cCE0/3neFaYieKuZRyYTDjenEBNmvsWnz4btQPPscXeH+49PjlYxfDDTES5+1KlPkDP4g6OuZzp9BAbc70o495zbdkYRspiJccSZqjE2LEThyNliM7pxrbDhPnHqXQlfwVceNx4jR3fPt1G42AIeTrp9nj05Rg5lhotXfkYDixmTkfMMFtscDgdsHleH2Kk3M9YCUDB0CEcBwPIDbQPEmL8tNFBn8rMWZ4i6UkGdxuF4xcde3xFB3r6+tE7tQHz2Tom+vv51zz943h5asPO/KDrdc8TZJLRIt4x3ojRYh+lZqLH6O8fkBgrMb29fZ76rC175o1vn9HI7N6BfbcXWVoNUlrWYVpuQmrhAPYtL/AoSc2d8MZxZF7Cw0ShDWe0xo9hXX3GG60XVhusp+voqy1CTkUnXnjPkCU9weKZDXsTDcjLzENl70sc2xw4nalxGa34akxwwnK00Iri7BzkPh7FttWM5eZMqNLbsG4/xhgzeNoCdHNm7YA7qW+0ZyOCGa/JE5wtPEJS4SAObNsYqM5DSkYeCus60fFAuO1JMNj77j12QsHvuElu5N53Byxbw7iflYeaiQPYOCO9Od2InIwKdG2cm/cwbT4aBztQXZSLlPQcFLcvw2RdQ1OaxvX+Hzlwtj6I2uJ8ZBVUob79IVLU3Fhs3Qwwe5CI6rkz2NZaYIxKQOnwLqxOK45WJtBSnYsYdnEgaUNchFcZN8LY8e1TwWgwYtksu43TkMB/w+q8fuw6dtGT7z2TGTytmzaYQlnPpM720yaO1yDJ7UUJDmx1Ms1ibRSOP8Cxx9S4bh36rNGKrcakn7oE8S4RtNEK9vEO9yKjFBFEj62XYCZKbKzEMDPG6rKrS+GEKe5TUzaGI+syZ6oScH/mBDs9BYiMrcGM6RgjZQlIa9+AZaMdqVFCGwOKx5jReookVRR3wrVimRkrPpeAqlkTjicqoeNex9Qu4Ox0GuUGd1tOsFo2bDidfgA99zr20RIsphncjxP61iOnbxf2nW5kROdz5srOiVQOVEkNnIF7ieGxbZzMP4RBw3JWrD5Ng7pomDda/ZXpiOZOsuLjI6J8Tpiu8RAsAcYNez+sJkxXx/OvdVUzOLWtojGF/f51yOndg4UbH4mq8zaRhjRkFlWg5EE3li3HGC6NQexj7v3nTDwz9L77rEV65w5K9dJjuRcZizLuBGff6kQaPya1MOTXo3dxBya7E7aDWTxM0/lpR4TKxcfN+djx7VON5IZF7K71IFcr3R4jIqsTW45jjJYbJDlPnewe7HBGqytHK8kFw7bdjIVHyZLyQKhye/22CdcaoI2JDUh0Vite2rh2D5PcbeSPP9Cx62vmXEbLo5McCY+xYDFjvi5B0g9BvCu8EaPFpuJ/fuM2v/6hoLBIYqzElJVX8HU/uvkJfwuA3QoQ93kv4RHmzdwfd1Ul+vbdJ09VBprXLdhor0Dd/Cn2BosR5WkjNlpHGCjSe3IlY65bg9FMVLirN9suZ5rUQtt4VE6f8nk9d4LM6NqBbbsT6Z58FAwPn8PMm7MYFA4fwrRYj/TKcRzt9aOkehIn3NVgfnojXlh20JnNnVBVSSjtX8OJzQGH3YLjtVHUpAv7QzDY++49doInwLjhjdah533XlI3j2HMiYCZpG5a1Z0hmRisqCeXD2zBzJ6rD7TW8eLGOAysz8XH8+2/f60O2RrrP8fXLaDCKDRiHKg0Nq1aYFx8jTpQLj6vAIGfOTfN1MIjbESFz8XFzPnbEfcoTg/yBPThOZ1AZK86d80pGS5MJx+EYiv2aeD9w9RtenIXWhkeH9PZN2Kwv8cTfOPZDoGNXpxajpLwYyV7bVxUMYN+5h+5cuqgg3l1CMlp/+p+/y8IbrQiVImxx6c9u3OKFL0qjw8iIzGL4EbYYXs/XZW34Rc23P5X0eU+VjqfrVmyOjWLFso7mFO4AI/QoGDzA6dwgxg+Y+YrzahNzbrQiVa4TbmG0J+cyWtWI5l7HPX4By9EoCnVCWyMeL1twyuX1EVFIalqF7WjEK6+GsWWDn1rP16qgr56F6XASLf0bOGRtkhqxfLaK9uYJnBwOo8DTjiMqBnFZ99GxbIJluVF6nO8x7H33HjvBEnDcJLqNlvt915QyozWH6liW1yC9w220uPHBbj0fW16iOcNVN9z4FCs2zmiVxrjef85UV8RI9zk8pRlb3XmIEpWrc3uxxRnqFw0pCBPl2LgtHD6Cc7cHmVHiHBEqFx033mNH3GdgNIirnsCBw4r1tmxESvLnRGR3u4xWtkaSk0WXjfr5I4yWe+uZDO76dsdB8G141DCUDWGHu/jbGyqFVpL3hyaoY+eJTEDl1Akc+wPI0/rJE8Q7AvNGYr8khn9gKVujJU6ICdZo8R+1/vnH+NnHt3hiDHF+zRYrYzm+3g02he/6qPVnf/xa0ue9iGjk9e/j7PCQMzWceXH/4cbWLcJ8vI/9sxXUG5n5EuoHb7TC01qxZjvD8+ZsqCO1iCsfxo7didMZZrS4fCp30rWeYbk1DzqVmrtyq8PEgR17A8VQs/4S67F0tovV9WOsNqcjTJ2Hnr1TLL/YwuFUlWsbKZWoK0uHjn3SjLsizu3bgW2z3c9xvr+w9108dhSRGzchGC1+fcnJFCq4q/QwdTIqRvZgc55grDwGYckNWDLbsTNSjUStBuGcWU7ITufHBhuXVqcJL3uqkZ4YB11MEtIf9OHlqYPrux2ZbJwa7qNnrB3l2Ubo9bGIy2nE3IkTptkaxPj5PRChcaFxIxo74j4lqPQwZFahdXYPFqcd+5M1iFdJ60XFpiApJY3HWDbAG60+7u9eKEuMFTRIBKc7OmMhqjtmsWN2wGndRYS4jkL9kWqjfBs3YWz85tWha/GAG7sOHM01IEUjreeD1/EHOvZzoqBKKET9tOtvaPpBop+LDYJ4d3gjRusn7q+4+NnHNz2otTqUlpWjn30ipbcX+QWFUKm1PnVYG9ZW3J9A9P1pnDqdrsWe7rKITLZewAn7djey1N71OaM1egTLSnMAo3WEkymX0WIny/SnSzjhzJXDYYd5exx90wc45me0WF6N+Psj2Dxjt/3scDitOJhtQppwlaZKR/Mae77NIQaL2DZiUTHJXck5zVhk6x64OvrSAayeWLn+bbCx24fmHQzfT5Qc4/uOv7GjRMBxE5TResobrXv6MgzsWmHnDLWZY32wDUPbZ+73Lwr64m4sn9jg5MaHze6A/WQW1XGu7aTXT2LTxI0Lh8OF3YSN8XqkR7vyqvRHGFnjTL+Q505uZ5sjqGRrvsT7TFyIi4wb2bHjJjK7k/u7NcHM/c2yBePWw2X0Pkh3XWBJcM2w2ziNsPO43mumGa7XNuwNloja6lHYv4Mzvn8nZ5i4i7XRJuTGBZoFC7W+m8hUPJrZxM6hiRuHrsXvlv0l9LBjYeNfXN+Nv+P3f+wciQ8wuLSB3RMLd9ycJp+uY6A6RXnmiyDecoI2Wpd56/CLr77xfB3Gzz6+gZ9ygsa+X8wf3oLHfx0G11bcnweVFlHaaKjY4mKhLFKDSI2ozE1YlI4zc66TmYqrE+l1FcbnRG3CtbEwxMYgMtJ//p4qGrq4RMRES0WN1We3SSPcosW/5sxlhM+VnxpRMQmIjYtFFN0y8kuwYyeoccONDZ/3nRs/Ko0W4V7vkTA+XPW10MYmIFrrKmPfyxbJ1m955TWxiTDE6PkxIt6Wmn9v46AWjxs3bFGyISEJBr2OrvAvmWDHTdBjRyCxEs86W/D4QSkykmIUZ4xcf/fRAZFoCkdc2TM8q69BUVYyNEHoQqj1XeiR1zyEvq4WPKoqRmqCHuGSOn4I5fjV2agfHUdvewPKc4zQyM56EcS7QzBGi39g6WUaLcbnf/zaI3w/+fnHvPAxAeRF7iMmgjf5MjbdLwgeayPuh3j/CDh2aNwQMgQcN6Q5BEFcIcEYrZAWw9+NiAyaz7/6Gj/56GN+DQQTNvbpHiZyDPYpIVbGcqwOqytuT7y/BBo7NG4IOQKNGxo7BEFcFUEbLfaPOCEmVKMl8Nkfv+Kfwsw+hs2eecNgP7MylhPXJwgB8dihcUMEg3jc0NghCOKqCMZo8bcOr9JoEQRBEARBvIsEY7TYBw7JaBEEQRAEQYRI0EYrmDVaH374If7y9+9wJzySIAiCIAjiveav3/2D90ZivySGN1rBPEfrxs2b+PLrbyQbIgiCIAiCeN/48qtvcPPWLYlfEhO00frVb/4Lt27dxj/u3pNMnREEQRAEQbwvMC908+Yt3huJ/ZIYj9H6lnshxzd/+R98fOMm/vt3v8d33AbucBsiCIIgCIJ4n2AeiHkh5omYNxL7JTGeB5Z++9e/KfL7z7/gO77Bubgvvvoaf/nb3/FDWARBEARBEMQ7DfM8X3Le5+at27wXYp5I7JP84fkKHnEiEN/8+a/45a9/w5utn3z4Ib/iniAIgiAI4l2GeR62Xp15IOaFxP4oEJ7naIkTBEEQBEEQxKvheTK8OEEQBEEQBEG8GmS0CIIgCIIgrgi6dUgQBEEQBHFFeJ4ML04E4o/f/gW3f/Ub/kta/+1HPyYIgiAIgngv+I8Pf4pPOA/EvJDYHwUiJKPFOr71i1+5NvaTn+LGp7/E7z7/El988ydJXYIgCIIgiLedL77+E+91bnL+h3kf5oGYFwrWbIVktJiLYxv4yUc38NvPgnt+BEEQBEEQxLsA8z7MAzEvxO7uifP+CNpo/f7Lr/gpM+bmyGQRBEEQBPE+wjwQ80JsCdUfvlT2T7zR+vpvv5UkxLApM+bg2P/iHEEQBEEQxPsCWzoVrCdiHos3Wt9wL+T48ONbfKe//fxLSY4gCIIgCOJ9gXkh5ol+euOWJCeGN1rs1iH7YkQ5/uMnrk8ZfvHVt5IcQRAEQRDE+8LnX3/Le6J/57yROCfG86XS4oQY4aON4nIx7DuA2Jct0vcgEgQRKq7vErvF68jXf/qLRF+UYG1IgwiCuCjeGiTWFzHB+qJLNVq/++wL3Lp9G199+yf8/fs7CI/SEARBBA3TDaYfTEc+vnGD1xSxzgSC1WVtSIMIgrgo3hqkpD/B+CKG51OH4oQYpQ7ZlSQTubvhkZIdJwiCCAWmI7/7/R94TQlmZkvQH9aGNIggiFeF6YiS/ij5IgHeaLGv4BEnxCh1yKbZmAMU7yxBEMRFYELHNCWYKXxBf8hkEQRxWSjpj5IvEri0W4fsniabbhPvKEEQxEVhmsLWW4n1RgzpD0EQl42S/ij5IoFLM1psAdnf/vEDwlRqgiCIS4FpCtMWsd6IIf0hCOKyUdIfJV8kwO4aXorRYqv1xTtJEATxqjBtEeuNGNIfgiCuAjn9UfJFAm/OaGkSkJydh8zcPKQkREvzihiQ+XQOO6enOFwdxv2Ui/RBEMR1R07olPVHgwi11odwTy4OJX0vsTJcjRhxO10CEtMyYFQkDTE68TbViCl8gie1lcjLNCI2JZfXuUzuZ414OwRBXGvk9EfJFwnwRoutiBcnxCh1GFjoAhBdgoEDJ5zOE4xVxEry4WodIjWB0Rb0Ydu6g7HmBrTNH+B08THi+LYGFA5sYX9zGTOjPWisK4da7Wf7l0Ts/VY0laZA7SdHEMSrIyd0SvqjyuvHnsMOu92NYw+TvQOYnJnFNMfClgln28/5n6dnptFzP9nVNqkBS1amTwpYXuBRkni7sSgePeLz+0OVyG1ZhZX72bbWAmOUuC5BENcZOf1R8kUCl7ZGy7/QRUOfmoX0rBwJaZkPMOw2WlOPC1zlmemI0XLt1Fl4umaBw+GQgWt7MoWKOD3SW9dwttGGVGaoWNt1m48YtmRoz/eJX+Qm3s8LEl2Arm07tw0HLHvzaKtIlRouQyrSjHFQXdY2CeI9Q07o5PXHbbSYDthtsNod3N/qHiaGnuNUbJh4zJh/mORqKxgtxxFWZqYwMSliZg1HTIP8Ga2YCowesf5OMfUgBWkta7Bx/dvXW91GSw/j40ksjVQjlnSBIK41cvqj5IsErthoJeLB/JkfQQvA6RTKDWreLD3b8DVLAeFN1wlmH6a6bwlEQ5eUhbzKx2jum8DC+h5KYs73KTK7ExvmU+xtTOBB8nl5eHQ8YhOSZEiEjplAr+PT5T3D9K4ZDs/+OGDemUS1UeOpoy0dxSGXc5zO40GC+PdDEIQSckInrz/nRsu02IonYwdgRquvJAmZ3MUZm2U6mqxG0dA+V27HZnchdBp3W4/R2kFPsVGqB0W92PZrtDRIeLyEM17PprkLQQ2SmlfPjZY+EzXju/y2nU4L1jrypRdnBEFcG+T0R8kXCXiM1td//qssQoficgG2M/cio0Qk4P7YJrZ3diTsnQpGygbTwS5ftrM1hvIY1k7HmaVUJBr9k5CUgeqpY769ba0TuXHRCHNvMyr7IZrrH6AgOxUx0VpPuUD8kxewMOOz04NMzXl5dNVMgKtcgT305On8HGM04ktaMLXDDJcDe0Ml0HhyeuQNMhFnItuGlChxW4IglGDaItYbMf71JwqReX3Y5Y1WCx67jdbEs3o8ahrGqoX7uz6ax+SeA077DsZbGlDHmapw1japPoRbh17bjKvCOD+b5cTxWAWnBWokuo2WbWcFL4/ZDDiXd5iw3FmMaJV0nwmCuD7I6Y+SLxK4YqPlB5UB2a0vYfKI1QnGK2Kl9eRQpaNpzWXUjscroPXKxde7jJSrbzvMJ9vnZkuVgkcvLHzuYLgUaq92+vIeTM/NYVbCc2yZWF+BjJbQtx6JFY9RzF3desriajB96tqPzY5sRIjbEAShiJzQKemPx2gt9aJl5pD/O56ZdM1mSUwTd6G03ZmDiCgdNMlFqHr0BA8fK/CoFnnGGESyiyhNOh4tmjz9HY2V+xgtodx2uIinBfGSi0CCIK4fcvqj5IsEXq/R0qajdnLfJToOG2w2l9EaKzdI68oQZmzCMn+1acbi42SvXDRSHnRhcOYFNvZPYWVT+84DT17Fbhvy2zzAQFGMpN97KukDy8L1ZRjir1AVjJaEWBSNHLhuK1qW8cToZcAIgggaOaFT0h/BaJ2bqT2MPL6PyqoHfqhGUUYcEptWeCMmXRfqH6fTipfNnDGbPvJaRuDHaFn3MddWjnivmXSCIK43cvqj5IsEPI93ECfEKHUYSOgE1BmPMbZrdYmQbR9j3NXg0OFFjFYM8gb2XIJmfo4672l7EWFqA2Iz8l2vtVloemnmt29da0WKWlw/AfenT2CzMwPohd3uFs9QjFY0UpuW3Lci7djpL/KZPSMIInjkhE5JfwSjdbY6ht5F9knAPQy1jroWyEvYRWdONBKfzGF7bxe7ByaXQbKf4WB3BztseYM/drcxV5+OxPoXMDsOsbruWtYgNlr29RYk87cK9YjPykGKMRFaDV2AEcR1Rk5/lHyRwNUbLU0yijuXcGR3iZn9aB712TG4pyvGQMhGS4PY+xPY5/tyYH+41Gs9VGDCYnLRsHDsMkz2bfQU+JnN4oxWxegmJ5q7PuzuHeCUnz0LzmiF67NRN77juX1p3exBTrS0HkEQwSEndEr642+NlsdoHS+ivb4ejxoH8NIsGC3hb1wDY8s6b5Ac+0sYGhzCgF/68DBb72pjKEdjQwVqJpWMltG9hMGMhYdJkn0mCOL6IKc/Sr5I4HKNVoRKhAHFo4fuGSEr9qYbkM5MB8tpi86NVlmMn7a+RMbmomZwDSb+diAnWjuDKNRL6/nAiaUmKQ/bZ2x6n7Uz4XlTJlTienLoSs9vHeZqpXluG1ExyUgvq0fn1AZO3IaSN1nbgyiOcx8vQRAXQk7o5PWH041ct9Fa4IzWqNtotYy4Z7TssFmtsFqFWWvOaGW7/8YjU/Bk2T0DL4dlCQ8TvLcZg5KxEz53NFoGTUQUEpu8jFYk6zsVTatsjekZZqrjJPtMEMT1QU5/lHyRAG+02D/ihBilDgMJXVjiY8ztLKOzLBmRnOgYa/sx2N+D9s4RvOQXih9jpNSP0VIbUfDwKToGp/FiR1hv5cKyNYSyBLW0DSOuHO3jc3i+toMjs/sTPgzzJgarU7h98NOGQ1/8DD29fX4YwVIgoxVThYljwcR5YT/FSn81EjXS7RAEERpyQqekP4LRMu8uY2HzlP879hitkzVMjo5hZGweW8KMlttohRmb8ZKfyT7CaFUa4hKSPMTGJ6Ogd8tlzk4mUOpzwReE0YrKRecO041DDBbpJftMEMT1QU5/lHyRwBXPaDGiEMbEhf9Zi8zuXV9T4thGe6bGT7skPHzu+oSggP10E+NNhYiJEtf1QpOPnj1v4+PAeEslknTyM0vs8Q7nn4T0hx+jFZWF1k3h49o2mPZeYrz9ATIM/o6HIIiLICd0SvojGC3vv2OP0bIeY2drE5vbBzjlZ6LPjZY+rx4dQ7N48aIH+TquL3U2noxMYWx0FIND43i+75rtsq08RaJH3xhio6VC/JNl16ccbafY3dzAxu6Ja+2XbR3NqQEuGAmCuBbI6Y+SLxK4o/0GH/w98ktJQoxSh4GEzhctEkvr0dTWhe7efvT2dOBJeTrUknquulnP5rA4O46eZw9RlJGIKB9BC0QiyrtH0df5FLUVBTDGRfupIyUqMRd5BUUyFCI1ViyKeiTlFyM73YhorThHEMRlICd0SvoTmduLHbsNx3ONyDSmITk1DcbyIZfRclhxZjLBdGZxP37B69ahmMh0NLsfKXOOFWutWYjwqcuMlnuNlttoqXK6scV/2tkbB0wvmmGUu2gkCOKNI6c/Sr5IgH+8w+szWgRBEKEhJ3TK+sNm1Dm8yiKSClBeWYXyimIk61QIM2ShqOI+yioqkZ0QaDZaB0NaDrJy85HLXXgVFBUiKyVOZLJc9ZKKalD1oAb3i1I860HDNAYYElOQlJqOZKMRcbF6RAZ14UgQxJtETn+UfJEAGS2CIK41ckJH+kMQxFUipz9KvkiAN1rfqa5yjRZBEMTFkRM60h+CIK4SOf1R8kUC/GJ4MloEQVxX5ISO9IcgiKtETn+UfJHAudH6019k+bf//DGPuFyAF7rwSIIgiEuFFzo/mkP6QxDEVSOnP0q+SMDzeIevuBdyCB2KywXYztzldoogCOIyYdoi1hsxpD8EQVwFcvqj5IsEXqvR+s3v/4B/+ff/wP/9v/4lZFg71l7cJ0EQ7zZyQheK/jAuqkGkPwTxfiKnP0q+SOC1Gi0mVv/+4w/xs49vhgxrx9qL+yQI4t1GTuhC0R/GRTWI9Icg3k/k9EfJFwnwDyxla7TECTFKHQYjdOzKkInWjVuf4Nanv8DtX/xKEVaP1WftWHtxnwRBvNvICV0o+sMIVYNIfwji/UZOf5R8kcAbMVo3P/kFJ2C/VODX+PxOJL79r19y9X8ZktCp8toxtzyPZ7k6Sc6FCknVnWirL0F8lFCmR3HPEpYmHiMpQlw/EpGJucgvLFYkLy8NOj/t3w3USKluxZPKTOgixTkvdElIzcxGepabzEzE6lztE+93oKe3E9VpWmk7jojMJozNDKM2XeNT3jc4gIdZ/tv4koiK3mlMtBRCJckRbyNyQheK/jBC0yAXcvpzTxuPhGQjEpNTgiJGp3K31SOnvhON1VnQhseitH8JC8MPYdRoEKnWIkLu74sgiNeGnP4o+SIB3mh9/5puHXquJm9/KsvNz7SoHprD/Pw8xxTacr7HJwGE7m64Dnn9+7A77LDbXTiEL6B2OFxlXG5/oOj8xBtTjalTG1YH29AxOIh+N2MrJ7DuLGDQq6yrOg1hXBtN2QRObKtoSlHzfYQl1OO55QTjFQb3fmiR3bsH+3Yn0twiaXj4HGafr90QY8NKo5H/ZIP0uC6ByHgUdq/hzGnGSnse1N45dQF69x3Y7y9AJGc8E5vWYDubxf0YUR+qLLRteX05dwAcR8Mo0LrbJDVhxbaP/gIDkhuXcbY1gEdtL3DqOMH8kzREqIyonjqA3byOnpIE/vfLt4sw4tELM/f+ud9L9j5aFlEbF4kD5w46Ml2/+/NtOLi6fvB+79l4sK2gPkk4pkQUNLTiWWubD239z3Fg547DvIW+YuE9Ja4DckIXiv4wgtUgMYGM1t1ILdQ6PY9Gb4AuxgB9QS92HLvoKYznX+v0rjwjUuVqF57RgU37KSYe12Fg1wbTix7UPqhB9YNaNHF/G63VlfyT6nOSXBccylrCuHo9eSUtIYi3EDn9UfJFAq91jVZQIvfLPyOpacJtsuYwXBuDzz6VETqOcF08DHEJPDEc8WXsu8z2MVCa7CnX685P0jEP5mGyraOluA6jmzvY2trm2Tm2wG7a97ze3llEQ2oU30YwWs9ykhCXmARDeiNvtCZq0vnXcfHJKB7wNVphmhhEG+IC8sJqweLDBK9jiUJiWTOan7UEpqkKKRrp78CXKGgyHmFkywynbQ/jtamcAIrqBC2OUYiMNkAbbUTV1DHMy81IM7Dfabzv8cToESHM5LmNVl9RPlo3LDgzceaJOwkcbb7EixfLHlb3mamyYKu7EFFcu/DUFqzajjFeGYewiCjufZqFyWnFBpeXGC1VNHcSi/VgMGYiK78QWen5aHh+hoORChiiY937ZkCU+wQnJjy+FG3PjzlTZ8LqQA2MWmHGgbguyAldKPrDCEqD/BBQf9TpKGtowsPCfNTO7OHw8BCHx2bYufF+dnzEv96dbURRWT3q6yth5P92NUjv2IL9+CXmub8Pp92MY67eAcex2Q6biWt3ZILVeYC+fNcsrpKWRKc3vxY9eTUtIYi3Dzn9UfJFArzRYv+IE2KUOgxG6ASR+/jWJ25+hd/++S/43SfC69/gr9ntmOZN1jymO/Lxt1+7cgGFzg9RBYO80eoviJbk7kZlcSd/G5zmBdRk1GLmzISFjjpUPajDs7ljWNcHUFddg6qmKezb19Gc4jrx8kaLzdx4ZlscrqtIr5kTNgPj8DJaSuw6jzBY5L2PaqQ1zWN1bQ2rq1LW9s/g2O9HjlralwsNYnIeonfpkBNpB05X+lDuviKWoClE/6ETe335QYljZHYXdwVuwS63H3unJpwerKCvPNH/1bPbaI32TOPkeArtT1tRU9OMjs4udIyu4uxsDaNd3M+dLaipfYbmsjiuXQyKRg5h2x5AeXIM168KCQ0rsBzt48BmkRotLzQFvdiwcO+F3Qabzca/D4dDxbx5E9f1EBmH3GfzXN+cAVzqRllaPDTqKP/HQ7xR5IQuFP1hSDUoOALqj5r9Hdmx9qwMj5bOsDNci5z7g/yM1kB1IaqGd3G29BQVHeuwHw4ij/3t6iswduzE0Xg9HvSvw3I2hweJemi0KVwfZu4ioQy6rDas2s+NlhIROb2vRU+kdSJD1hKCeJuQ0x8lXyTAJrNeu9H66Oav8KU6D4/7JjE304Ws//kVV3Ybv/i+CF0zLpM1P9GMpG9/yZczAgodd1J/abbAbDafY7XDwQmD3XpeZjl7ifpkNeIfPccZM0heRmuykt0qikHZxCmsy41I4PqNzB/wNVrlrhmt5lQtwlVqRCS5bx3ej0N4pBphETrk9PnOaMkTBbt5ETVx4nKBeOTXt+FpVQYi2Gt9CQb27NgbKPIyECpExiQjragWzYPz2DjhDKTTDovFCufJJEqjxX16oS3B0JEDO905CBeLY4QRlR09aK5IdW07MhVPXpj5vo+ed6O6pAx1o9vclfc8ntU0on1wCgvLI6gwuPt2G62xvlmcnM6hJiUGmmgOXQwSH83jzPIcj4wx0OpdsNmmiMwOrNtMWByaxA73/8vuh2iYOcbxVB2yqka5bQcwWhGpaFix4nShAUbOKIVFF6BjgzNmAY1WFHQ5TZjcs7puedqssNrdppk7PvPhCvqrUlzHTVwL5IQuFP1hnGuQS1eCJaD+iI3W0ANku41W//18P0ZLi4zOTdi48XY0Vo7EykmcsIs3z4Wb62f+gsG+H6TRioLx2fqb0xM5LWF5sZ4QxFuEnP4o+SIBtg7+DRit2/iN6gFG3DNXg5UR+NWvf0BB96zLZM2Nojb6C9wIQujuGTJRWFqOYoGyBowfukTLcTCFJ+Vl7lwJUg1GXgwPNrZg8hitM2wtTGJ8YhKzGyaYtxb4n8dn1nDsZbR0VTMw2VbQaAx+jZYsnNE8W3yEWHG5QEQKGlet2O7Og0pfgNZlEyfU4yj1uUpMRO2iywCZD9cx3VOPwpQE5PTswCEnjIyYKkydshNEKj975COOvHBasdyQDCbiCY+fw+Q8w8u2fOh0qShrm3aLsBO2012szE+gr6MBeXHu227CrcOCNNQunGJnbRNnnvVy7jVdnlnAE4yVGxD3YAa7L58iJSoaKY+nsW9j9cxYeJjI93nAtbFsj6AqWXTiicpDN3fC2OrI4kSelelRPHoM62qznw81xKFkcBtm7vd1yr3PfU3VyM8wwhBj4IygAYaUYjQtHMNp30FXTjAnOOJ1ICd0oegP40qN1nMzzg63sbV7DIvTgqOdbWwfcRd63kZLm4mWDXbxZ8fhZCMqnnRjcu0QZtMO5he2YD17gYGxLRg1KaibmMXTHL10m2I4Lenatr85PZHTEpb30RM/7QniGiOnP0q+SIA3Wq97jdbPb9zCz3/xHfJ63Avex5tRWtWNGbfxGqnV4bc3b7nquQkodF7ciylG98YZjlbWsOc8xPrGCc42en3qxN5vQG3DtMtoZZWiobsHvX396O7ux/S2FUcvhtHFlXUNLuHQy2jF1C7yJ2ir+QxnnDk7M1th507+bNaMf81htjqCvHWoQ3rbGoaKZUSUMxA9ezastuYjq/kFTvanUOM2eedEQROfDL3Wu1yNtE4FYeS4x2YCbWeYqWa37XzFUcVm8xw76MzS4K4mAw8nN7HaX4aErKdYPOF+B4cv0N/YgolDbv+ambiK+heMVr4BmV3bMD1vRGZWIXJTk5HyxD2jlZ6O/OJsxBriodOw37EWUZ7jUMPYvAqLaQ5Vsa4+DxyH2NrmTgL2YzxvL4Le8zvWo2BoHw7LDqY6m9HU95x73zgjt9uLLM8nSs+JyqhAaXosVDEZKH7cio6eXnQ8e4yiFL3rKxeSm7l9t2O1KUV6XMQbQU7oQtEfho8GhUBA/RHPaPXkQZPVzc9odWXrkdUjndHKqmtFz3MTDkeb8XRiBt2PypFb1oQxplcWG46Xl/By+QC24xlUJ7jWiAbGpSUWx8Eb0xM5LWF5Hz3x054grjNy+qPkiwR4o8U/3uHbP8vi6dBPjsF25k5YhCy+IvcJPk96ikm3uRKYG66F6ne3AwqduE+BiORajO5aYFppR0HZAL9Gq6e0BO1rZlQlq33qau/PcEZrHtWGSOgrp3DkOMFMaycWOfO09CSJrxMWl438wkIYObG4ExaFtI5tOI4nUZ2ZifTMbKTmPeVntCYf5fGv0zNzUDHkmtFKjZDun4eIWOR3rsDktEEjznnB3xK1HWO0VM+10UGlktbxj3tfTyZQqhPnzompXcCZbRWNyez4IpHQtMqJ4wwqYyK4K3MTLCvPYIwU6nMDTpWOp+tWHM/UIZ6Vq3JdM0ntWQgT95/I9n0fk63PMLRqwsnMMzRMHuJ0sR45dbO80WprmcepbQNtWVrJvoUl12PxzIbNzhxEusvYGq3OnCRkN05ipi0XEd5tVMko617Axt4+tlem0DO2AfPqUySGi/bLzb3EOswcO2A9WMPC3DyWtk9ht22hkz0OJL4eS1YrXrjHAfHm4YXOj+aEqj+MVzVa4v7uRBWg/4AzWk9LeaN1uDqL6flNnDiOsTY7g9m1Y85oNaO8nTNaB4PIjWLt4vFggas72YQHLaN4sW+GzbSF8ab7uN+7DuvpApyni3iU4qtbEry0ZLu/6I3piZyW3IlM8aMnBPH2IKc/Sr5IwGO0/si9kONfuc4Y4nIBtjM/cDslhyByHv5bjeoRb6M1hkf6z/GRdx0vWHtxnz+EaZFUM4ZtqwOnL1qQruFMV57LaPXmafGDNgcO6zaGa9L4kzNro65kM1rzqDKw1zqktbx0rds6m0ctdwUp2Ua467ED1pdNSAh3l8U9xiJntJhwueqpkdnjMlopEb7t2SfkolMKUdU2gdUTO5wOE1a6iqXbEYhIQPnEISfM7JEJfvKyRCHVLYwlOnHORXjKE8xyRsO81IB4fl8jEc+L4yxqs0u539cG2rN1vu00rnUY290uk/MDd6UbFev6NKe4/x/cRmuibwSLMz2ofTKKffs+BkviYKid441WTVwC7s+cwLrRgbSo87b3EqowvGuDZa0DGZrzcma02jP9vDc+RCIi5RGmj61YfZaOe5K8i2juxGA2P0ddgspVFpGBlq0zLDUVoLB3EzYrd9JIceeINw7TFrHeiAlGfxgSDQoBv/rDGa0+ZrSeFSP/iZ9P9THqK1DsNlo5/FiPRzUzWuOd6F6YR/fDIqQVNmBk4xSm/X2c2DewcGbH7mAJb568txdIS3SCLvnjCvVESUtanx/71xOCeEuQ0x8lXyTwZozWRzfx049ucPwSf83pxOTMNKanpzHSkIjPb7JyX1h9/0KnQVobdwXoNGO9rwx6t8EJy+njjVZ3jssEFPdtwOy0Yq0tG+Fh50brUW4RHnRMYo0Jlu0Uh9wJ2mk3YWdpHJ1NdSgtKkBaQjQisjqxabdxYpqOu8K23UZr/H4SNOzxAWoDCoYOYN9sg9HLaN3L7MSW3b0uyXqC9al2lBp1vFMW/354ogvRuXrG1d1Cb5FBmldEXhjDMlqxYnFyojuN6iTBuLjFkV8Q7kRzjmAevdEhq2uT+13bcLrzEnNTExgZHcPY1CwWXm5id6UD6ZHuum6j1ZevQ0RaExZN3EljpAbpaenIal7iTA6bTeROGomPuROKBS8aUrgTSDxyGiexZXbCstGPQkOkz/Z5o5URwGjpcvGobwKLW5xxYwv2FxqQ7GXexNxh2zU5YTvewNzYEHp6p7ButuLMZIXDdoCJWmNAk0a8fuSELhT9YUg1SJnA+hPhNlrcmD3ew87OTkB2jy1wSozWE5Q1DGBh1wwHuyXeWY6U8hEcckZLf38Khw4bdoYroHebqJC1hHGFehKMllgPFgLoCUG8Hcjpj5IvEuA/dcj+ESfEKHUYjNB5i9zPmICxn32m6KVXkXw9OaGLyUNJbuy5AQqTGq0fwlTQ5lciO8aVF4xW/aMxHJr3sTTSjPwEDXflp0dicT26p1ewfXQGq92K1eZMpNQv4vhwEqXu9jxxj7BweoDhinw0rlj4B2UyYTmZrobOZ/+yUVpRjHRjHCJFM13+iURs2UMUxvuZKQqKKG5/JzA334MiP0aLGabUsjIkqH3L9fmPUFdbhbz0eD9tBFRQpxSjuqkTvcOcyZqYwOjIMPq621FfV3rep2C02IxiZBJKG2qQnNqEZatLfO27fcjmTzhRSK5pRmkid6yaQvRtH+J5VwUMKvF2FYxWRAYa5l5idrgN93Pi+VuZkjoi7uqzUPG0D6PT85hfXMD0xBDanpQjWR9gG8QbQ07oQtEfhl8NkkNJf3ijZcMGpyEPn9QHpGFkEzax0ZoZxezeNma7HiCrijNYbnNi3x8CmyFPqB3CYJ3xXNtC1hLGVeqJspZEyM20EcRbgJz+KPkiAc+T4cUJMUodBiN0//uCX+jKYO1Ye3Gf/rijS0RSSipidL6zIgL39Mlc3ohoLVtoKs17CBfykYjUaqV5nkjc0+ihNcRBp49GmFx/7wsqPaJj46H2nlUKVyEsSotIjRb3AvyO7gQoZySlpsEQ4P0k3m3khC4U/WFcVIMC648K4Zpo/onv0tw5d1Q6RGk0btOkhjoxDcmJMeczp5zWhKt1UGmjER60iSII4qqR0x8lXyTgeY6WOCFGqcNghO7Xv/sDL1bsyjBUWDvWXtwnQRDvNnJCF4r+MC6qQaQ/BPF+Iqc/Sr5IwPNkeHFCjFKHwQodQRBEKMgJHekPQRBXiZz+KPkiATJaBEFca+SEjvSHIIirRE5/lHyRwGu9dUgQBBEqckJH+kMQxFUipz9KvkjA82R4cUKMUockdARBXAVyQkf6QxDEVSKnP0q+SICMFkEQ1xo5oSP9IQjiKpHTHyVfJEBGiyCIa42c0JH+EARxlcjpj5IvEiCjRRDEtUZO6Eh/CIK4SuT0R8kXCZwbrW/+JMu//uePeMTlArzQ3QsnCIK4VHih86M5F9GfX//u96/wHK3fS/ojCOLdRk5/lHyRAG+0vv7bb/El90IOoUNxuQDbme+5nSIIgrhMmLaI9UZMsPrzqk+GF/dHEMS7jZz+KPkiAeaxyGgRBHFtkRO6UPWHzU4x43Tj1ie49ekvcPsXv5KF1WF1WRvWVtwfQRDvNnL6o+SLBHijxW4dihNilDoMVugIgiBCQU7oQtUfwWjd/OQXnIn6ZVDc/OSXIRmtiLw+7Fh20ZOnkeQCEZnXgYW1RbTm6SQ5giDeHHL6o+SLBPgHlpLRIgjiuiIndKHqj7fRCoWARstQhYHF51hYXPSwuLwLk9OE7WVR+eIgyg3hiK6awNb+Pnb39jzsHZ7B5rTBdHhevre/jbGqOH47EfGZyMjOUSQ1Xivdx0skoa4bTbnRvuWqXDxbXMV8ax7C70Ug4eEkXq6OoEwvbU8Qbxty+qPkiwTIaBEEca2RE7pQ9cdz6/D2pyER2GgVoaGrCx0909i02bA924eOrm4PXVObsFg3MdHN1elsQh5ntFQpxSgtr/Sh5PE49p0HGHtS4VNekOIyNdF1izA7nXDKYsPLhmR+Aa9kPy+D8FicOc142ZaDSO9yVR569h3Y68vnjVZ84ypsZzOoiPbTB0G8Zcjpj5IvEvB86lCcEKPUYbBCRxAEEQpyQheq/ly60fIQjYLhQ9j3h5CncZep89C1Y8fxdBV0PnXjUDV7AitnzARsdgccnFmy28/LTmZrEO1ucydKD63eEBBNahOWrBYs1LlmwFxEIq6kEU1PnwWksfE+kqPExyImElHpDzG8ZcZYjRFh4jwZLeIdRk5/lHyRAG+02HcdihNilDpkO/OPu2EEQRCXipzQhao/gtH6+NYnISEYLXF/hroZbO3uYntnBzv7p7A67TAdul8fnsHutOH0wP16dxvTdYn4/m4EIgxJiE9OQYIMsQYt7vg5Bn/cy+rBrvMQAwUar/JIGBvnsLK66pfVvTM49vuQGSntz4UK2sxadD8/4I7LgZOXvX7qcKjy0XvgxF5vLu7dDUecYLR0fuoSxFuGnP4o+SKBS711KN5BgiCIV0VO6ELVH8FofXTzdkgEMlrq9ApUVj8ImtKMGL7dndR2bDmccAgzWO4ZLfbaxr12SEyTHBFIeLoOm3kB1THinEAsch63oKkyFXe5199ri9C/Z8defwHCPXXCcU+XCGPBAzT2z2HjhO2HHWaLFc6TCRRpxH26iSrCwJEDO11ZXN9+jNa9RJS1d6OxLJnftqQ9QVxj5PRHyRcJkNEiCOJaIyd0oerPZRstnvAstG1ZYLVaA2LZ6kRq+Hkbl9E6QH+BDj/ci0B4dg92HLvoytbwT6N+aQvBaEXmoGPbjrOFOujFOYF7yahftWK7Kxvh2lw8WzbBfjCGomjvenF4sGiGkzNXZ4drmOp+jLykWGR2b8MhZ7R0lZg8tWOt2Ygf/BktzogNHlnx4gmbzfPTniCuMXL6o+SLBNhdQzJaBEFcW+SELlT9EYzWz2/cCgklo9Wx68TBSI3kU4AZWbmoGj2AY7fLx2jdy+7FnvMAo08qUFJWjqLaYd5oDdaVo7S8AitBGy01UlpWYeFM20Chzk/eTUQOuvZsWHmWg/TGJRzvTaIqMVJULwKq2ARooiK9DFEkjO3yRuv7hAYs284wXcVm66RGKzy3H3uOHbRnqCRtCeK6I6c/Sr5IgIwWQRDXGjmhC1V/rtJomQ82sLq6JmH9wCwxWlEVUzh1WHF6eID9AykWRxBGK8yA3I4VmJw2bPcXQiXOe/FDYiNnho4xXMyZsTANwiOkdfyjbLR0NfM4s62iPikcPkaLzZaFG/Fw0QTLylMkeh0/QbwtyOmPki8S4I0WWxEvTohR6jBYoSMIgggFOaELVX8Eo3URlIzWwXQLauoeSXg6I57RikJGzx5nXsYDmpeWnm7UZWkl5T9EaKEzFuB+6zhWTuxwOkxY6SqC5p60Dw9hcSgbP4D9YBh5aj95WeSNVpjxMWaOHThbqkdcGCsTjNYsajJL0PL8GHbrBtqyFEwjQVxT5PRHyRcJeNZoffH1t7IIHYrLBXihu3OPIAjiUmHaItYbMcHqj8dofXQTP/3oRlCwuh6j5afPf4S5jNbx8ih6+vokDC8fu4xWmLu+tgwjR1z98XJEifuS4W56B7bsrmdmOazHWJ9sRUmiGt/7qetBk4+O1TOu/hZ6CqKleUUi3EaLM4Vq39y9tGdYsThhO5hCVUKEuzwMcQ2c0XI/28t6MI8mzjDK7iNBXGPk9EfJFwmQ0SII4lojJ3Sh6o+30foZM1F+Zq58CNpoOXC8NouJiUkJM+sncOycG63w1HrM7iyhPlkwJ0Giy0RJWSHSEmMQfs9P3i9hMJTUId8Q6ScXDBFIfjyO2bluFIiM1j/uqGEsKUFcpG+5LrcOtQ8qkZtiQNhdcRuCeLuQ0x8lXyRARosgiGuNnNCFqj//+9//A//+4w+lhkoB1oa1FffnIhKR0bHQqiP9ztzcVRugi9bgrlcZW2zury5BENcLOf1R8kUCZLQIgrjWyAldqPrzq9/+jjdMbHYqFFgb1lbcH0EQ7zZy+qPkiwTIaBEEca2REzrSH4IgrhI5/VHyRQKexzuIE2KUOiShIwjiKpATOtIfgiCuEjn9UfJFAmS0CIK41sgJHekPQRBXiZz+KPkiAd5osX/ECTFKHZLQEQRxFcgJHekPQRBXiZz+KPkiAZrRIgjiWiMndKQ/BEFcJXL6o+SLBO5ov8EHf4/8UpIQo9QhCR1BEFeBnNCR/hAEcZXI6Y+SLxLgP3VIRosgiOuKnNCR/hAEcZXI6Y+SLxIgo0UQxLVGTuhC1Z/ff/YFQRCEB7FGiJHTHyVfJMAbLfal0p9//Y0sQoficgG2M9/duUsQBHGpMG0R642YYPXnTngEQRCEB7FGiJHTHyVfJMAvhueN1lffyOLp0E+OwQvdD3cJgiAuFV7o/GgO6Q9BEFeNnP4o+SKBSzVaf//hDkEQxKUiJ3SkPwRBXCVy+qPkiwQ8j3cQJ8QodUhCRxDEVSAndKQ/BEFcJXL6o+SLBMhoEQRxrZETOtIfgiCuEjn9UfJFAmS0CIK41sgJHekPQRBXiZz+KPkiAf6BpbRGiyCI64qc0JH+EARxlcjpj5IvEiCjRRDEtUZO6Eh/CIK4SuT0R8kXCfBGi24dEgRxXZETOtIfgiCuEjn9UfJFAvwDS8loEQRxXZETOtIfgiCuEjn9UfJFArQYniCIa42c0F2a/mhSUXS/CmUZ0dLcK/BdWATu3JWWEwTxdiCnP0q+SIA3WuwfcUKMUoevLHQEQRB+kBO6UPXnH/HlaOnpRbebroZiGOITEJ1ci+kzG1Zac2CIS+DLNKp7rnbaMvSvrmN1bS0ga6tDKNaIt3cP8U1rsOz1IiMyCU+WT7E7WIRwP/slprDvJdZmHyPujjRHEMTrQ05/lHyRAH/rkIwWQRDXFTmhC1V/vourx7LNjIP1Fazun+FotA0Op5PDAYeDwX52wuk8wUix2tVOU4EJkxVrI09R39gooWlkHVbTFErFRutuMhrXbDgaK0HEnSQ0rHI/D3sZrTs65FQWQO3HTGUPHMKx243UMGmOIIjXh5z+KPkiAfaBQ95o/f/t3Wlb1GjeNvD5Cveb+5j7meOemaef6c3u6bbbFsUdV9xQkH3fV0ERQUCURRRQcVfcUEBFRVBQ9n2pKqjlO51PrhQpIClSFSiQac4XP7uTK0klufB/nSapsG3XHl3/5+//lKnnK8TOBB47TkTkU6K2qOuNmrf153BCjRS0RvAoNw4FTWMYe1mEO/02jD4/j1MngnEy8za6rRNoKonBseOz60WWykHr47UEHNZsMwgxVz/JQetCxMK2E7mPMWifwIvCCAQGpaBWDlrnESy1HYk4jevtE7BJ+/KiOEZePvR0BWpu1KP+7n086xiFfbIHb1vf4d2HDnR86sLnni94UhSpOSYiWjl69cdTLlLIQUtc1lI3qHnaoLeFjojICL1CZ7T+qIPWaEs1yp4NwDryEmV5Z1Dc0AvbRCuu5J9BZmKYcz05aNlhGR/CwMCgxuD4NOzqoHUiCVXtZtiHHyM75LgraI01XUZO2RN8nrLDOvoO17LCXOEt9EKTtK1RDA0NontwCrbpEXS+f4tXr1rwovE5njxpQG1+tOaYjDh19joePX6C+qJ4TRsRaenVH0+5SCEHLfGHukHN0wa9LXREREboFTqj9UcJWs8v5aPy1RjGXj/F5OSUxpRpAm1XEuVbB0fCkpFdcB755wsXV5CHhPAT0vLic04grrodJnFLcrgBWcHHXUHLZrXCbregt7EcSaHa/VOElb2FydqNupQTmrblCC5qxqTDio9X491cnSMiNb364ykXKRi0iGhN0yt0RuuPM2g5pMAzgxmbA+Mt1bhaU6N1rRI5MUEIv/QOUzYrZmYkVvHfmUVZbSa8vRSDkDOP0DszjcHBcU3Qmup8gMLkUI8h5+S5Rozbh3A/O1jTJjuRiVs9ZphMnk19uY3UE871QnIqUHv9Bq7kx2m3SUQaevXHUy5SMGgR0ZqmV+iM1p8Ftw5fjmG0+Rqsk0Po7etz6Rsxw2ZpQ1n0cZyIy0LW6VzkXHqOAfsEXl09K08vJjUuFLHV7Rhqq8Glx0OaoKU8oyXvz8lwhEVFIEiEoOPBCI5JQFxSCpLSM5FT5vy819dLUXKpHJerrqK69jrqagsRGyTWTUHx7Qe498ALty8i8aT2XBCRZ3r1x1MuUrheWKpuUPO0QW8LHRGREXqFzmj9cRe0LB03kJ2agdTMTNnpGx2wzAYt53rByHgwKH8zccZigdmsZTF9QnVikHP50HhEh4cg6+GwftCKuoRWsxmvL0Y6r1D12ZzferTbYbPZnd+GtFkxLX2maWoKE+PS/nbeQtrs1SkiWnl69cdTLlK4fgWPukHN0wa9LXREREboFTqj9cdd0LJbp6WwZHaxzNjhmB+0Tp3F42E7xl9fw5kzZ5F7Nn+BskYphE29Vn3rMBiZnoJWXDXaZ8RrJMKl6ZM4GRWD8KhInAoPQ1DsZbwx2fDlZiqOujmOpQo5XYUb9bdwNT9W00ZEWnr1x1MuUrjeo6VuUPO0QW8LHRGREXqFzmj9cQYtC4a/dKJryIwx+YrWVcSHhuNURKQs8Wr7gitaYQUP0THUgwd5oZrtBR6LQvEbE2z995C24Pac+6A18bLQFbSOZ91Hv30I99w9hxV6Ds/GHBh8kI1j6rZl4MPwRMbo1R9PuUjhejO8ukHN0wa9LXREREboFTqj9ccZtMbR/vwRHjx8hHs1l+Cw22C1WufYHAuvaKm3EX8Fb4eG0Nfbgy89g5i0OjAhXkq6YDlV0DoWh8ttFtitJowOiGfBBjFmtsNhakVJlPYzxK3E2wN2jDUW4KS6bRlO5dXg3sOHuFHI1zsQeUOv/njKRQqfBq1DR48TEfmUXqEzWn8Cw1NxOr8A6bHBs/Mi8OpxORLDIxEWGS1LvvwYr1obUBijXV/eRvQZVNTV4+ad+1JokcJafQUyIk6olgtGWt1bfGy7hcyTznlHo3NQWFmLuvo7qL91EzXV5TiTFIZAN59x6FgMMsvKceFMEoLUbUS0avTqj6dcpPDprUP1DhIRLZdeoWP9IaKVpFd/POUihU/fDK/eQSKi5dIrdKw/RLSS9OqPp1ykYNAiojVNr9Cx/hDRStKrP55ykcIVtPx36vsfaWOCer5C7MzBI8eIiHxK1BZ1vVFj/SGilaBXfzzlIgWDFhGtaXqFbin157/++69E65b67wPp06s/nnKRgkGLiNY0vUK3lPojBpvtuwOI1iX13wfSp1d/POUihRy09gT6aRrUPG3QSKEjIvKWXqFbSv1Rgta3P2wgWlcYtIzTqz+ecpFCZCxe0SKiNUuv0C2l/jBo0XrFoGWcXv3xlIsUrl8qrW5Q87RBI4WOiMhbeoVuKfWHQYvWKwYt4/Tqj6dcpGDQIqI1Ta/QLaX+MGjResWgZZxe/fGUixR8GJ6I1jS9QreU+sOgResVg5ZxevXHUy5SyEFL/AoedYOapw0aKXRERN7SK3RLqT8MWrReMWgZp1d/POUiBW8dEtGaplfollJ/GLRovWLQMk6v/njKRQoGLSJa0/QK3VLqD4MWrVcMWsbp1R9PuUgh7hoyaBHRmqVX6JZSfxi0aL1i0DJOr/54ykUKV9DaumOXrv/5+z9k6vkKsTMHDh8lIvIpUVvU9UbNSP1h0KL1Svzcq/8+kD69+uMpFynkoCWeiFc3qHnaoJFCR0TkLb1Ct5T6w6BF6xWDlnF69cdTLlK4ntFSN6h52qCRQkdE5C29QreU+sOgResVg5ZxevXHUy5SMGgR0ZqmV+iWUn8YtGi9YtAyTq/+eMpFCp8Grf2BR4iIfEqv0C2l/jBo0Xolfu7Vfx9In1798ZSLFAxaRLSm6RW6pdQfBi1arxi0jNOrP55ykYJBi4jWNL1Ct5T6w6BF6xWDlnF69cdTLlL49PUO6h0kIlouvUK3lPrDoEXrFYOWcXr1x1MuUjBoEdGaplfollJ/GLRovWLQMk6v/njKRQoGLSJa0/QK3VLqD4MWrVcMWsbp1R9PuUghBy3xh7pBzdMGjRQ6IiJv6RW6pdQfBi1arxi0jNOrP55ykYJXtIhoTdMrdEupP0rQIlqP1H8fSJ9e/fGUixRBUQH4y+HQnZoGNU8bNFLoiIi8pVfollJ/RNAiWq/Ufx9In1798ZSLFPLrHUTQ2rJdn7JB9XyFXOgOHSYi8ilRW9T1Ro31h4hWgl798ZSLFAxaRLSm6RU61h8iWkl69cdTLlLIQetI2G5Ng5qnDbLQEdFK0Ct0rD9EtJL06o+nXKSQH4b3RdD65ptvsGN3APYdCiQi8omde/bKtUVdb9RYf4jI1zzVH0+5SOGzoPXd99/Db+s2zY4SES2V31Z/fPfDD5p6o8b6Q0S+5qn+eMpFCtfrHdQNap42+NO/f8H30g6pd5SIaCn27Dsg1xRRW9T1Rk2pP2Id9XaIiJbCU/3xlIsUPgtaftt24NvvvmehI6JlE3Xk199+l2uKqC3qeqOm1B+xDmsQES2XqCOe6o+nXKTwWdASNm7aLCdAcbmNz0sQkVGibohbgKKOiCInaoq6zixGLCvWYQ0ioqWaX4M81R9vcpEgv7DUF89oKcRlNnFPUzxAJp7WJyLylqgb4nkrUUf0/iW5GLEOaxARLdX8GqSuL2re5iKvg9bf/vmNvMFNW/w1bURERETrxSY/fzkTiWykblOTg5Y3tw7/+e138kZ/3fSHpo2IiIhovRBZSGSif/zre02bmvzCUm+C1r82/Cxv9F8//qRpIyIiIlovvpWykJyJpGykblPz+mH4jX/4yZfI/vaP/4t//8arWkRERLT+iAz0t398I2eiX6VspG5Xk4OW+EM8ROrJtz/9W05wf//mW+mDNmnaiYiIiP6sRPYRGUhkoe82/Kxpd0e+deht0Nq0ZZvrcpm4svWvHzbgl9//wO+bt2qWJSIiIvpP97vfVjnr/D8p84jsIzKQyEIiE6mXdUd84dDroCWIDYsU97d/Oj+MiIiIaD0Q2Ufc3fM2ZAly0BJ/qBuIiIiIaHkYtIiIiIhWCIMWERER0QpxvUdL3UBEREREy+N6M7y6gYiIiIiWx9DrHYiIiIjIe4ZeWEpERERE3ltW0Nqy5xAOHjmGgD07NW1qWw8G41REJI7uX9pnLZt4Fb56HhEREdEKMnbrcMce7NizF9t2OKd3JNzFoGMItxP3zrbvdrWp7Up9hBF7P+pi9mja5tub+RC9Y+9Rdkra1qkytPT2oae3V6P7dTlCpM/aFVeG2w8e4p7KrdJkHA0KQ3hiFu42fcTgSDPyDms/j4iIiGilyK93EGlrs/92j/yjb6BPCkvXo53Lb4+/IwetWwkB8vS26Juom23bvG0PAo4F4/jJENmpgkaM2XtxM+2Ua57iyEHn+sLuzKcYt37E5ZBd2Bpcjg/WETRW5CP37JzLL0Zh+1yN4O3bsTOxBi3v3+Ptu4WaastR322F3W5Db0cz7lScQdjBnZpjIiIiIlopBoPWTe+D1vZwVHTNSEHHPssBh0Pimp7lsKP/VgK2zX7GnqxnqqDlkMOSzTaPtN5M1xU5aG32D0BgdBqS09IXiApJRm2fFV1XIzXHQURERLQalhS0bsQ5g9XOpPty0LqTtE+e3hF3ay5o+e/CzoNHcPDwUVl4eRumLa24EDo3b/+RTNwftmNADlq7EF7xBl1945ixTWKwuwvP6u6ifWYET0szkZKe4ZSWiZLGuStam/0PIfP5BOxWC0wmE0xmi7T+GB6ezsbtISs+Xk3A4eNBsoP7nPsWkFyBW3fvojorSHOMRERERL6yhKBlhXl8FMPDIxgZN8PmWDg9F7Tm243wul7YRhuQsnfe/IA03B+1o+9GnBS0duJIygVcqHuD8Zku3C8rQX7hNTx+/w6tb914fhHBO8R2DiHj2ThMr8/jkNjm/mw8Hh/DozNn8XB09iqazIrP1RHY4j971cwxg7bSE/DT7CsRERGRbxgKWtuCM5B/vgjnFFUvMeQYRmNloWtecvDc81ZzjiKvZQqWDxdxbNu8+fsy0TBmR09tNPxn5ynPaJWdikLFpymYLRa3LNMmtF8Ok4KTKmjtcwathuIKvDZP4kVhODptg7iTGYxDyhWt2EJcrqhCScpxN/tKRERE5Bty0NoT6Kdp0NgWjIIn7/GqJhW7Zue5ntGKV8LVfrx7WrQwTAkHcvB0XLlyNW/+wTw8n7Sis1IEJuc8JWhdCjmIg6eScL6hB5bJNtwoPi+FvMJ5CpB6StyyDET2i0lYJ4fR19ePvv4hTMyM4WnNA/TYnLc5RdCqj9ujPSYiIiKiFSQylpdBKwQXO6Yx8ihDN2hNd1zG8QVBawcOFbzGlHiIPlZ1tetoCd5OW/D2wtyVJSVoVeWWobHPBPNoP3qGJjFjt2CsvxeDUzaYJ6VpWxcuh+yQ1jkiXy0bf3MdRReKUaiob4N5qgm5h3YwaBEREdFXIQctr24d6gWt2W8dugtafodz8XTEjqm3xTgqP7w+Z1tsPfrtY3iUcWD2M3bhYO5zjE8PoKNjCF8aziA0sQpvJ6fx5VY2YoqaMT71BqUXHmFECmMXT0hBa3soLndaMfIw3bVfm7edwPm3JphaL+CwtC/qoLUn7gKqqq+iNJW3DomIiGjlyC8sNRS0mmtQVFziVN2MYccwXlyZnS4uXRi09sXj2iczHKb3KAkRn7ETe46F4vjxo9i7/xgSb/XAJp7HOimuTO1BhHhg3m6Dqf897pfnIqu8BUMzU2ivSUdo5l10T4+isSAER/ObMWl6hTOHpc84kItnE1Z8LA9xPdi+K/k+BuwTaMw9LE9rghYfhiciIqJVYCholbZPY8Y8jtGxsUVNt19yBq3dUajokELWdA/qUw7NBpoAxN0Zgt31TUBxpesijsvfHtyOgJAYnDwUIC27C8eKXkvbe4+arGjEXnyJQesk3t65iQcvGvG6xwxbdy3Cd0rrZD7FmH0AN5QgtTcZ9b0zmGwtdW1XHbQCEi/hen09KjP5egciIiJaOd5/63BbMPLuNeHZ1RTsVre5HMDLBwWuh+G3HElCatTsbcFZ/nuP4lhIJMJjExAdFYK9u9TbUD5vN/zloLQXYeWPcftMMHYE5aD67kM8eHgbJfGBcnjz2xuBs9UXEDpvO1sCoxB2dO4t8PWP76M4eq/2M4iIiIhWkBy0xO86VDcQERER0fK4bh3+IU0QERERke/MBa2t24iIiIjIh8RdQwYtIiKi/0C7TiTicM4NBBU30yo7nHtbPv/qPlEzFLT+67//SkRERF+BekwWxGCvDgC0ekTIVfeJmhy0xBPx6gZ3REdv3x1AREREq2ixoKUM+Ft27EJYVAyi4hJohYnzLM63cu7VfaJm6BktJWh9+8MGIiIiWgXeBK2wyBiciErF3tBMbA/OoRWyNzRLPs/ifDNoERER/Ql4E7QiYxMQcCoT205m0QoLkMKsON8MWkRERH8C3gWtePgHZdIqEeebQYuIiOhPwPuglUGr5KsEre9+2Y6D4QnYv/VXfOemfb6ftwUicL8/NrhpIyIiojneBK2ImHhsPZ72FWRgV9hp7AvPnXUaAaE586Zz5eeatinLnziLqMI6ZJ8twh7Ntv5ziPPtbdAy/HoHd0Frw74zaByxYLynDf0d1Qj6RfuDMt93O7LxoucxErZo24iIiGiOd0ErDluOpa6K7fHX0fClC+UZWdgSUok7wzZYrRKbHXb7CO7UNKNHTM/Os/U3IvLk7PonilHVY8N4Sw32S9P+yQ/RNmnC+MTUAv1NtTjg5rPXCnG+Vy9o/bgLac9H0HsnAZt/lELUvzdiw4/aH5SFNiPi9me8OrsP32vaiIiISOF10DqSsjpOFuNSuxm2yU6UpJ9HxJkqpOZfQUppC7ptI7hVXC5PC+eeDsM6IAWtIGm9Y2nYHnRhNmjV4qA0vSulAZ+sZpTXPZr1BE96rZh4XYcD6s9dQ1Y3aG1Nx9PxLlw68ovmh0Pwi7mM+lv1KInctmD+T8eq8KnzCo56uPpFRES0nnkTtMKlgd/vSNLqCSlFdacZU59b8eTLDCaH+tDR1YuPXz7hatULfLZNY6hndt67hwgPSsLBix2YsourXg44xH9tw7hV+VQKWqa57R47j4ovImjVYr/6M9cQcb4NBS3xx6Yt2zxyF7R+OHwZnaMNiPPT/nAIm1OfYdIxiaep/gvbftyLvNfduBPjp1mHiIiInJSgpR6TBVfQipaC1uHEVbU18gIiYorkYDTQfA+5Zc/RZjaj6W6zFLTG8exaLQoedMNs/oizEYnYHVeKhJyruNltxfibe0g5fRnR+Y+dQUvZ7tECZ9B6VYP9bj5zrRDnWzn36j5Rc13R2rTF3yN3Qevn4Br0DtxEyEbtD4fgF3URddfrUBSx8IqWsDmpAd0vc+Dv8VYjERHR+jQXtLTj8lzQisXmwIRV4R+cg8PRebLA0FzEXXuNF++68HnchvHORmRlXMLFZz0Yt5vR296OhvoqBB6ZXf/oeVSKW4fN1dgrTW9JeIhOmwmXau7PeohH3SJoXcM+N5+9VojzPRe0tP2yoI+iAvCXw6E7NQ3uuA1aJ51B69QiQUvXxlBc6/qA4kPubzsSERGtd94ErTBp4P/jYNyqOFzRBYvDAYdkpLEacVVt6OwZwKDJDvPoILq6+/G5fxJm+wxG+wfwue0hwo/Mrn/4HCq7bRhrqUNE9lWkFj3FF5sdI+MWzDjssExOYHh0HL3Sdve6+ey1Qpxvb4OW/HqH5QStb/2S8HC0B1dObNT8cAjfb9wCP//t+H3jz5o24bvtWXje+xRJW7VtRERE6513QSsGmw6sosBzuNJrw0hzA648f4/nLR/QMWrDRHe79P/v0djajwm7CZ/fSv/f8goXkhMQcP4dxmbMmJx2YPzNDZw8kYCDpR8wae2TtpmOzOYpWPueIvKom89bY8T5NhS0xC+VVje44zZo/eCPmLsDGGkpRODvP0tp9RT2b5prX/QZLZfNCL/ZiZb8/fwGIhERkYpXQSsqBr/vj149h/JRJYJW0yNUPmnF4xeteNL0Ee2f2p3//74Pn9475z9+2YyipHhsOpII/8CzqOi2YbypErv3xyP8zjDsY6/kbe7IacKgFM5eXMjAJtdnxWBrUBr2hqRhR6A306tDnG9vg5b8jNbygtYGfLclEpVvR2AyTWGy9xaiVEFrwjEhBS3tM1qKDUcr8KmrGsf4DUQiIqIFvAlaoSJo7YtcPYHncLXHBnPXA8QmXMblF32YtNkw+v4+okKzkXarAwMWO6bHOlF7NgtblfUO5jmD1ssK7D50FpVfrJh6W+NsO5CFgvdmKXi1IjNE+aw05LVa4LB2ozQqyotpN/u6AsT5XtWg5fQzfv5jO37aoJr/0y/4+ZeN2PCTevl5fgxAQtVNFEcsdtWLiIhoffI2aP0WELEqNgdfRF2nFIgsY+gbs8HucMA+8Rn15eVIzCpGTHoholLPIyL9Mkqe9WP081Mkh8Rg09E0HAg+j2opoI01XsbB9Ofot1vQXJw2t+3oerwzOTD54TaCD4l5qch7I32WCFIRkV5Ma/d3JRgOWsv51iERERGtHO+CVjQ2BoSvij3nWjE89hFlyfH4IygfefVv8aF/HOPmGcxYbbDJ78qabxINeQnYmvECg/JD9FZ8ri9HTsMApgYbEXtk/vYjsPfcawxOfkRhtPOYftsfDb+D0di017mMp+nVIM43gxYREdGfgDdB61SkFEr2hK6OAwkIOBKmnR8Qht/3ReCP/VHYcnChP/ZK7fuiseN4EvYci8EfAWKdcGw7EoPf1NuR50e7mb92iPPNoEVERPQn4G3Q+nX3KVolRoKW/B4t3zyjRURERL7mXdCKgt/+U/hlZwitML/94opWFIMWERHRn4E3QSvoVBgOBEXAb58IW8G0QsT5FedZnG9DQUvcOvzdb6tHStAiIiKi1SPGX/WYLCiD/W9btsqDf0hEFK2woJBQ/L51LuSq+0RNfmGpkaBFREREq089JguB2TfmrmrRqjt8+ramT9RcD8OrG4iIiGht2xkULw/26gBAK0+EXHH+1X2iJgct8Ye6gYiIiIiWR751yKBFRERE5HviC4cMWkREREQrQA5afEaLiIiIyPfkoCX+UDcQERER0fIwaBERERGtEAYtIiIiohVi6IWlREREROQ9Q7+Ch4iIiIi8x/doERHRojb8shF//d9/aH4dDK0ccb7FeVf3xWLYR6vPSB+53gz/2+YtREREC4gBZcuOXQiLikFUXAKtMHGexfkW513dF4thH60uo33EoEVERIsS/3oPi4xBTEIyElLTaQXFp6TJ51mcb3He1X2xmPl9JLah3i75zlL6yHXrUN1AREQkBpPI2ATEJ0sDeEo6rTBxnsX59nYQZx+tPqN95HozvLqBiIjIOYjHy4MLrQ5xvr0dxNlHX4eRPmLQIiKiRXEQX31GBnH20ddhpI8YtIiIaFFiMImIiUdcUiqtEnG+vR3EfdtHaUhMy0JSqnr+WpHmZt7XYaSPGLSIiGhRzkE8DrFJKWvWmYtVqLxWg/JLxcjOSFvYnpyN7KISFBTkInHe/IScQpwvLkXB2Wxp4NRu82sS59vbQdyXfZR0qQmjdjPe15zWtPlK2rkiZKRq53t09i4+z5jxsT5f27aobBTU3sPtO9eQny5NZ5ag+u593L52AcmaZY0x0kcMWkREtCjXIJ6YsgZlo/D+RzjsNszMzMBqd8Bhm8KX51eQmTy7TEopngzbYW6/gQxlvewqvBiawcxQC8qzU91s9+syMoj7so8SCp9gwD6Dz7fPIc5N+7KlluBRvxW2qV403yxFutJH84krRup5whkRtKbRWX9W25acibTcQhSWFiFdBCFXWw4q303BMdaCkjRpOqMKLRMOTLy+ghT1Ngwy0kdy0NoT6KdpICIiEoNJuDSoxCQmrzHpyH/QDYtjBvlZafLgF5eej0tPu2Fy2DDcVCENptJyKSV4LAet61LQkqbTS3C/2wLbRBuunUl1s92vT5xvbwfx5fRRYtFNPGl6hZY37/C2rR3tnf2YsDpgGRtA/+AQhkfHMDYxiSlTHx4WuTlXyfm4/KgFrY3XkK5ucysNmWX38WbQArvDgZmxj3hQfgYJrvYMlL4chmmgEcXpC9d1XtGaRtejSpRW38Ttp9LnfurF0IQZMzYpYEvbs482oTht/nrZs0GrWQpa0nRG5WzQqkKyZt+MMdJHImMxaBERkVvyIB4dJ787aE05fQPtZgemPtSp2rJQ2jQCu7UfD86nSWFgXtBKPoe6dmngNX/G7fPp2m2uEeJ8ezuIL6eP4oseo3t8DMNDQ+jv60V3dx9GLQ4p6HSgtfUNmpub0djYiMePH6H6fIZm/ZiEHFRJQcY+9ByFybPzktKRmleMizV38fDWJaRo1hEycPrKc3ROzGC89SrSlPkpF/FkyAZTWy3SpemUojrce/4GbZ8HMDI1I4czEagE24wZY4M96GhtwsM799HUNw3L57vIFUHI9TnZqHg7G7RSpen0eUFLs0/GGOkjOWjx1iEREbnjHMRjEZ2QtKakXfsAk2MCLeWZmrbY84/Rb7Oi+36BFLSK5aBl6niE+jcj0gDdj8el2nXWEnG+vR3EfdpHqZfxYkwKWu+vIVXd5lY6Cp4MwGbuwZvm9+gcGIPJaneFIWvfI5xJUq8zT/JpZGSluKaTLrVg1GFGe12uPB1/4RkGLFMY7vuM960fMShuHT4oRaZ4Ds+1nVScufcFFvsYWiqyVJ8hBcE2ExyjL3EhRZpOr5gNWpVIci0jBadEN/vmgZE+kl9YyqBFRETuiMEkTBpUouIT15AknL7fC5u1F3fOJmnbM2vwzuzAaFMZ4pOK0TBkh9ViwYxtFM2VOYhWL7/GiPPt7SDu0z5KLMSDARumO+uRqW6bL7MKjb1jmJqZF6pMI+jueIMnd6/jYkk1ng1YMdF6BcnqdReTdA71ny1wjL9BWfrsPBFqZtuj8+6gSwpan27mzVsvCemVrzBstWH0VSVS1NuMz0F1uxm2oafIT5Km0yrQLIKWtGyiskz6FbyeMOPzXSmUa9ZfnJE+YtAiIqJF+WwQ96kk5NztgdXWh7v57oJWLdosDoy8uOgMWuKK1sdXaB21wvLlEc6lqre3thgZxJfbR+LqTIx4wFs8hJ6cj5td07D2NeB8di6y8vKRe64Q+UUlKCzMQ7yyXsI51Da/wdP7N1BW9RQ9VvGQet5sKEpG1vWPMNlH8Lw0XfN5izn3sAfTDgs+3jzrPgjn3lYFrRTk3GjHuN2OqU93kJvsZh1pP2/1zGD6y21ki2k3QUtc/RywmfC2Oku7vg4jfeT61uHGP/yIiIgWcA7iMYiMT1hTEivfYNIhBshMTVtcSSOGHc5BOTLpgjNotdchp/A+uix2TLyvRWaidptrhTjf4ryr+2IxS+ujPNR9MmHGaoXNZoddfGNz3jNQapbOemRotiFJLZfDi3z1UJpOKH6Cnmk7xlurkaJedjEJmTA5pH5pq0XGYv3iClq58z77Aq4/uIrMJDfLy+3OfZtsrUKSmE5zTk+8qkCCvEwy8h+LW58dqM52s74OI30kBy3xuw7VDURERPIgHiUN4nEJa4s0aDaN2THd27BwfkIeajpMcJg/4VqONJ14Qb51aP5Qi9S4RKSUv8KwzYr+52VIVG9zjRDn29tBfOl9lInzdXdw/eZNXKutQeWVK7hUXoG61jE4TB9QV1SA3LNnkXU6F+lZ2UhOTUaUZhtCHq53TWO66xYypem4/Hq8bmvA+VT1cm7EpyK99Baa+80Ya7uJ0yIwqZdRZN/Ex5kZdNXnadsWkVjWglG7Be21Oc55s8FLDlrSdGz+XXSaHRhrKTf8s2Ckj1y3DtUNREREYjAJlQaViNj4NSgBycX3YLWLKzIShw2W0U94VJGLaGWZhCI8GrJhqq0GKa71MlDcOOh8ZqsiS/51Ktptfz3ifHs7iPu6jzJufpbOywDu5Sdq2haTfqMT09Zu1OcmaNoWykC5eN2C+Nbg9CQGOl/hXnURkhPUy7mTioKGXljcXG1zsmHkRRnipGWjcm+g3STNs/SioTRjbhspl9E0oSxvxfinBlxI97TP7hnpI3Exi0GLiIjccg7i0QiPjVuzopLTkZyVhaQUEQ607ZHyQ9XxC+fHJSBafNtMPX8NEOfb20Hc132UdOUdpuyjeFqSrGlbTGxJA9o/vcXdi+matoXiEZuZi9T0FETFqdu8E52Wi9yiUhRdvIjCkmKcLchHVk621PfiipuyXCKyK66hICNh4fophai8XY9r1WXIzUx2+7PiLSN9xKBFRESLEoPJqchohMXE0ioR59vbQdznfSQHCTfzaQEjfSQHLfGglrqBiIjIp4M4ecXIIM4++jqM9BGf0SIiokU5B/EohEbH0CoR59vbQZx99HUY6SMGLSIiWpQYTIJOhcn/ghcPANPKEudZnG9vB3H20eoz2kcMWkREtKi//u/f8duWrfLAEhIRRSssKCQUv2/1l8+7ui8Wwz5aXUb7iEGLiIgW9cPPv8oDivjXO60Ocb7FeVf3xWLYR6vPSB8xaBERERGtEL7egYiIiGiFzAWtTZuJiIiIyIdcQetXaYKIiIiIfEcOWuIPdQMRERERLQ+vaBERERGtkKCoAPzlcOhOTQMRERERLY/8egcGLSIiIiLfY9AiIiIiWiFy0DoSthvCnkA/mZi5FOKBLzX1Mu6I+5eCu3XEfokgOJ8yT/xXvez8NuWY1J/nLfWxuNu/xRg5JqPH8zWOycjxrOYxqY/D3f4txhfH5OvjEdTH4m7/FjP/mObP9/Z4lGVX45jUy7jjiz5SlvXlMamPxd3+LcbIMa3W8QjqY3G3f+4YOZ7VPCb1cbjbv8X44ph8fTyC+ljc7d9iWBtW55jUx6L4/8Ggd9FQD9cDAAAAAElFTkSuQmCC>