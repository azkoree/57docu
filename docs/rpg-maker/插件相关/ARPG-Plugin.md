# 官方ARPG插件说明

This plug-in provides the ability to convert an RPG Maker MZ system into an ARPG.

本插件能够在RMMZ中使用ARPG系统。

## ■ 功能

> This plug-in provides the functions necessary for action RPGs, such as player and enemy status management, hit detection settings, and attack processing settings.
>

本插件提供了一些ARPG必要的功能，例如玩家与敌人状态管理，攻击方向设置和攻击过程设置。

> All damaging objects (sword slashes, bullets, etc.) are realized by dynamically setting events.
>
> This makes the plug-in highly customizable.
>

所有的伤害物件（例如斩击、子弹等）通过动态的事件来设置，来进行更为自由的自定义。

> Common events can also be used to create processing when a character takes damage.
>
> For example, in the sample game, when a character takes damage, the character is knocked back in the direction of the damage.
>
> This is achieved by executing a plug-in command for blowing up the character from the common event.
>
> This functionality can be used to implement a combo-like system where, for example, a character is only blown away if he is hit by a series of attacks.
>

公共事件也可以用于制作玩家造成伤害的过程。

例如，在范例游戏中，当玩家造成伤害，对方就会根据收到伤害的方向被击退，这是通过从公共事件执行插件命令来实现的。

这一功能可以用来制作连击系统，例如，玩家只有在受到一连串攻击时才会被击退。

> In addition, since this plug-in is built on top of the dot movement plug-in, any character movement can be controlled in dot units, making it possible to create very action-oriented games.
>
> For example, by calculating the angle between the enemy character and the player and sending bullets in that direction, it is possible to create an attack that pursues the player.
>

此外，由于该插件以像素移动插件为基础而开发，所有角色的移动能够进行以像素点为单位的控制，能够开发动作性更强的游戏。

例如，通过计算敌方和玩家之间的角度，并从相应方向射出子弹，能够做出跟踪弹的效果

## ■ 前置需求

> The following plug-ins are required to install this plug-in.、
>

该插件需要以下前置的插件。

**Dot Move System (DotMoveSystem.js)**

> DotMoveSystem.js is used to control characters in dot units.
>

本插件用于控制玩家的像素级移动

**Dot Movement System Function Extension (DotMoveSystem_FunctionEx.js)**

> This plug-in adds various extended functions to the main body of the dot movement system.
>

本插件为像素级移动提供了更多的扩展功能

**Self Variable (SelfVariable.js)**

> This plug-in provides self-variables, extended self-switches, and common event variables/switches.
>
> The ARPG core may automatically set various in-game flags as self-variables to events (e.g., ID of the user who used a skill), so this is used for this purpose.
>

本插件提供了独立变量、扩展的独立开关，以及公共事件变量/开关。

ARPG核心可能会自动为事件设置独立变量，作为各种游戏内标志（例如：技能使用者的iD）

> Please install this plug-in, including these dependent plug-ins, in the following order.
>

请按照以下顺序来安装这些插件。

・DotMoveSystem.js

・DotMoveSystem_FunctionEx.js

・SelfVariable.js

・ARPG_Core.js

## 【功能详情】

### [通用]

#### **■ 启用或停用ARPG模式**

> If set to ON in the "ARPG mode switching" plug-in command, ARPG mode is started.
>
> When set to OFF, ARPG mode is terminated.
>
> Once in ARPG mode, you can fight with enemies in the field.
>
> Whether the current ARPG mode is ON or not can be checked by the switch set in the plug-in parameter "ARPG Mode Switch".
>
> The current ARPG mode can be checked by the switch set in the plugin parameter "ARPG Mode Switch".
>

如果将插件命令中的“ARPG模式开关”设置为ON，就会启用ARPG模式。

如果设置为OFF，就会停用该模式。

在ARPG模式中，可以与敌人在地图上直接进行战斗。

通过插件参数中”ARPG模式开关“来判断的当前ARPG模式是否启用。

> Note 1: If the player moves to another map, ARPG mode will automatically switch to OFF.
>
> Note 2: Changing the ARPG mode switch has no effect.
>
> ARPG mode must be switched by this command.
>
> Note 3: Saving is not possible during ARPG combat.
>

*注意：如果玩家移动到另一地图，ARPG模式会自动设置为OFF。*

*更改ARPG模式开关不会有任何效果，更改模式必须由插件命令来进行。*

*在ARPG战斗中不可使用保存。*

### [复制事件/动态事件]

#### ■ **复制事件**

> The following description in the Note field of an event will copy the specified event from the list of dynamic event copy source maps specified in the plugin parameters.
>
> The specified event is copied from the list of dynamic event copy source maps.
>

在事件的“备注”字段中输入以下描述，即可从插件参数中指定的动态事件复制源映射列表中复制指定的事件。

指定的事件将从动态事件复制源映射列表中复制。

`<cp: 复制源事件名或ID>`

> It is also possible to limit the copy source map by describing as follows
>

也可以像如下这样，限制复制的源地图ID

`<cp: 复制源地图ID, 复制源事件名或ID>.`

> Note: All the IDs of the source map are plugin parameters.
>
> The ID of the map to be copied must be set in the "Copy Event Common Settings/List of Dynamic Event Generator Map IDs.
>

*注意：源地图的所有ID为插件参数。*

*复制的地图的ID必须包含在“复制事件通用设置/生成动态事件的地图列表”*

#### **■ 动态事件生成**

> Events can be generated dynamically by executing the "Dynamic Event Generation" plug-in command.
>
> The event from which the dynamic event is copied must be placed on the map registered in the plugin parameter "List of map IDs from which dynamic events are generated".
>

事件能够通过执行插件命令“动态事件生成”来动态地生成事件。

复制的动态事件必须位于被注册在复制事件通用设置/生成动态事件的地图列表”中

#### ■ **删除动态事件**

> Generated dynamic events can be completely deleted by executing the event command "Temporarily delete event".
>

生成的动态事件可通过事件命令“临时删除事件”来进行删除。



### [角色相关]

#### ■ **关于格挡**

> While pressing the A key during ARPG combat, the player guards.
>
> f a player is attacked from the opposite direction of the player's direction while on guard,
>
> the damage is halved if the player is on guard.
>
> Also, if the attacker guards just before guarding, it is a just guard and completely neutralizes the damage.
>

在ARPG战斗中按下A键，能够让玩家格挡

如果玩家在格挡时受到了来自玩家对面的伤害，那么玩家受到的伤害就会减半。

此外，如果攻击者在防御之前进行防御，则属于完美防御，可以完全抵消伤害。

> See "Angle of Attack for Skill Objects" for the direction of attack used to determine guard success.
>

有关用于确定防御成功的攻击方向，请参阅“技能对象的攻击角度”。

> If you do not use the guard function, set the plug-in parameter
>
> "Key Common Settings/Actor Guard Key"to Set the key name to "Unassigned".
>

如果不打算使用防御功能，在插件参数中，将

“通用按键设置 - 角色防御键”设置为“Unassigned”

> Also, if you use the Guard function but do not use Just Guard,
>
> set 0 to the number of frames for Just Guard.
>

此外，如果使用防御功能但不使用完美防御，将完美防御的帧数设置为0

#### ■ **通过插件指令设置格挡**

> In addition to pressing the A key, it is also possible to guard by executing a plugin command.
>
> If you set the guard mode to ON with the plugin command "Player guard mode setting",
>
> it will be in a guarded state during that time. When set to OFF, the guard is released.
>
> This function is mainly intended for guarding in environments without a keyboard or gamepad.
>

除了A键，也可以通过执行插件命令来进行格挡。

如果将格挡模式设置为ON，就能够在一定时间内进入格挡状态。如果设置为OFF就取消格挡。

这一功能主要用于没有键盘或手柄的环境下（例如触屏）。

#### ■ **角色切换**

> You can switch the player's actor by pressing the "S" key.
>
> This function can be used regardless of ON/OFF of ARPG mode.
>

可以通过按下S键来切换使用的角色。

You can also switch actors by executing the plugin command "Change control actor".



When the switch set in the plugin parameter "Control actor change permission switch ID" turns OFF,

actor switching by key input is disabled.



※Note: Actors cannot be switched while they are attacking or taking damage.

Also, the menu screen reordering function cannot be used while the actor cannot be switched.





### [敌人相关]

#### ■ About Enemy Character Settings

In the event of an enemy character, by executing the "Setup Enemy" plug-in command through parallel processing or automatic execution, the event in which it is executed will be called "Setup Enemy".

By executing the plugin command "Setup Enemy" in an event of an enemy character, the event in which it is executed is treated as an enemy character.

The "Enemy setting" is used as an enemy character.

Please be sure to execute "Setup Enemy" when the ARPG mode is ON.



"Collision Attack Skill ID", "Enemy Kill Common Event ID", and "Enemy Damage Common Event ID"

can be set as arguments when setting enemy characters, but if 0 is specified for these values,

the plug-in parameter "Enemy The value of the parameter with the same name in "Common Settings" is applied.



■ Displaying HP of Enemy Characters

The HP gauge can be set in the "Setup Enemy" plug-in command to display the HP of the enemy character.

When "Normal" is selected, the HP gauge is displayed directly on the enemy character.

When "Boss" is selected, a large HP gauge is displayed at the top of the screen.





### [Skill Related]

#### ■ Creating Skills

If you put` <action: common event name or ID> `in the memo field of a skill, the corresponding common event will be invoked when you execute that skill.

This common event is called an "action common event.

Within an Action Common Event, by executing the "Activate Skill" plug-in command, the skill is activated and MP or TP is consumed.



In this state, skill objects are generated by executing the "Create Skill Object" command.

Skill objects are objects that, when hit by a battler, cause damage, recover HP, etc.

It is an event that can give the battler the effect of a skill.

Consider a skill object as a bullet fired by a player or an enemy character in a shooting game.

The skill object collides with the battler.

When a skill object collides with a battler, the effect set by the skill is applied to the colliding battler.

The default hit detection of a skill object is the size of the event that made it a skill object.

However, you can customize the hit judgment freely by following the procedure in " ■ Setting the Hit Judgment below.



If "Activate Skill" is not executed, MP/TP will not be consumed. Use this to your advantage.

If a skill activation condition is not met (for example, if there is an enemy character nearby) when the common event of a skill action is executed, the skill will not be executed.

If the common event of the skill action is executed and the skill activation condition is not met (e.g., an enemy character is nearby), the skill is not executed.



Note: It is not possible to create a skill object without activating a skill. If you do, an error message will be displayed.



#### ■ Common Event Variables Available in Action Common Events

The common event variable for storing the user event ID will automatically contain the event ID of the character who is the user who executed the action common event.

The event ID is automatically stored in the common event variable when the character is an event.



By combining these two variables, it is possible to specify the character who used the skill in the character specification argument of various plug-in commands.



These variables must be common event variables.



#### ■ Pass common event variable/switch value to action common event

By writing the following in the memo field of the skill, it is possible to set the value

in advancewhen executing the specified action common event.

・When setting common event variables

`<set-var Variable ID, Value>`

(e.g.) Set the value 100 to the variable with ID=10

`<set-var 10, 100>`



・When setting a common event switch

`<set-sw Switch ID, Value>`

(e.g.) Set the switch with ID=10 to ON

`<set-sw 10>`



※ Make sure these variables/switches are common event variables or common event switches.

※ This function was added from ARPG_Core v1.4.0.



#### ■ Self variables available in events generated as skill objects

In events generated by the "Create Skill Object" plug-in command

The self-variables "skill object user type stored self-variable" and "skill object user event ID stored self-variable" can be used.

The self-variable that stores the skill object user type stores the type of the character that is the user who executed the skill object generation.



These variables must be self-event variables.



#### ■ Cancel using skill when receive damage

If the plugin command "Damage Skill Cancel Enable/Disable Toggle" is set to Enable,

the skill will be canceled when damage is taken, forcing the skill common event to end.



Also, if you specify a chanting common event ID in the "Activate Skill" plugin command

The common event will be executed until the skill is activated,

during which time skill cancellation by damage will be enabled.

The same can be achieved with the "Damage Skill Cancel Enable/Disable Toggle" command.

However, it is simpler to use this method when skill chanting is the objective.



※ The maximum HP damage ratio for skill cancellation can be changed by setting the

"Skill Cancel Damage Rate" in the "Battler ARPG Parameter Settings" plugin command.

The maximum HP damage ratio for skill cancellation can be changed by setting the

"Skill Cancel Damage Rate" in the "Battler ARPG Parameter Settings" plugin command.

If not set, the skill will be canceled if it takes even one damage.



#### ■ Revert movement speed when skill is completed or canceled

When the skill is activated, data such as movement speed is retained.

Retained data will be restored upon skill completion or cancellation.

By using this function, you don't have to be conscious of restoring the movement

speed etc. when canceling an attack motion, for example.



The data retained when the skill is activated is as follows.

・Moving Speed

・Character images and indexes

・Orientation fixed



※ This function was added from ARPG_Core v1.4.0.



#### ■ Attack Angle of Skill Objects

By executing the "Specify Attack Angle" plug-in command for a skill object

The attack angle can be set for a skill object by executing the "Specify Attack Angle" plug-in command for the skill object.

The angle of attack set here is used to determine whether the skill object is facing the user when guarding.



The value set here can be obtained by reading the common event variable "Common variable for storing damage angle" in the common event that is executed when damage is received.

This can be combined with the "Blow away character" plugin command to blow away the character in the direction of the damage.



#### ■ Synchronize the position of the skill object and the movement of the user

By executing the plugin command "Skill object user position synchronization" for the skill object,

the position of the skill object and the movement of the user can be synchronization.

When using this function, it is possible to attack while dashing, for example.



#### ■ Applying Skill Effects

After activating a skill, execute the plug-in command "Apply Skill Effects".

The effect of the relevant skill can be applied to the user.

Only the damage of the skill will be applied.



In addition, when the plugin command "Test apply skill effect" is executed, the user will not be able to see the effect of the skill before it can be applied.

This function allows you to check in advance whether the skill effect can be applied.

By using this function, it is possible, for example, to disable recovery items when HP is full.

For example, if the HP is full, the recovery item cannot be used.



#### ■ Displaying Skill Names When Skills are Activated

A popup window will appear when a skill is activated by entering the following information in the notes field of the skill.

In this case, the text set in the "Message" field of the skill will be displayed.

`<showSkillNam>e`



#### ■ Setting invincibility time when taking damage

The invincibility time when damaged by a skill can be set by populating the following in the Note field of the skill.

`<noDamageFrame: invincibility time>`



Example: To set the invincibility time to 60 frames

`<noDamageFrame: 60>`



If this setting is omitted, the invincibility time is 30 frames.



#### ■ Setting a time limit after using a skill

You can set a time limit after using a skill by populating the following information in the Note field of the skill.

The following is a list of the time to prohibit attacks after a skill is used.

`<noAttackFrame: Attack delay>`



Example: To set the no-attack time to 120 frames

`<noAttackFrame: 120>`



If this setting is omitted, the no-attack time is set to 60 frames.



#### ■ Specify inertial movement cancellation when skill is activated

Inertial movement can be canceled when the skill is activated

by writing the following in the memo field of the skill.

`<cancelAcceleration: true>`



If you set it as follows, inertial movement will continue even after the skill is activated.

`<cancelAcceleration: false>`



※ If this setting is omitted, inertial movement cancellation is enabled.



#### ■ Specify movement prohibition when skill is activated

You can prohibit movement when the skill is activated

by writing the following in the memo field of the skill.

`<disableMove: true>`



If you set it as follows, inertial movement will continue even after the skill is activated.

`<disableMove: false>`



※ If you omit this setting, no movement is enabled.

※ Only player movement and autonomous movement by key or touch are prohibited.

Movement from event commands is not prohibited.



#### ■ Overwrite skill for damage determination when character collides

By writing the following in the memo field of the skill, you can overwrite it with a skill

that damages the enemy if it collides with the enemy while using the skill.

`<overwriteCollideAttack>`



If you overwrite it, it will automatically return to the original setting when the skill ends.





### [Field Objects]

#### ■ Field Objects

Field object is an object that is neither a player nor an enemy, but can be set to be hit by a player or an enemy. It can be grass that can be destroyed by a sword, a switch that turns ON when hit by an arrow, etc.

The hit detection of field objects can be set to "Custom".



You can set "damage judgment" or "custom judgment" for the hit judgment of the field object.

For details on the collision judgment, please refer to "■ collision detection settings".



#### ■ Field object damage handling

If you set "Damage Judgment" to the field object, the common event set in

"Field Object Damage Common Event ID" will be called when the attack judgment touches.



Field objects do not have HP, so all you do in damage processing is calling a common event.

This processing is mainly intended for use such as destroying grass when a sword attack hits it.



### [related to collision detection]

#### ■ collision detection settings

The "collision detection settings" plug-in command can be used to configure the hit detection settings.

The following types of collision detection are available

Attack detection: If this detection comes in contact with a "damage detection", damage will be inflicted to the user who set the damage detection.

Damage detection: If this detection contacts the "attack detection," the attacker is damaged.

Custom detection: This is a user-definable collision detection. The collision detection set here can be checked with the "collision detection check" plugin command.



Collision detection can be set for the following characters

If collision detection is set for other characters, an error will occur.

Player (all collision detection can be set)

Enemy (all collision detection can be set)

Field object (only damage judgment/custom judgment can be set)

Skill object (only attack detection/custom detection can be set)



Player collision detection can be set using the "Player collision detection setting" plug-in parameter.



#### ■ Collision detection check by plug-in commands

Damage processing according to the attack detection and damage detection is automatically performed by the plug-in.

However, the "collision detection check" plug-in command allows you to check for collision detection at any time.

The "collision detection check" plug-in command allows collision detection to be checked at any desired timing.



#### ■ Collision detection visibility

If the switch which you specified for the plugin parameter "HitBoxSetting/switch ID for hit box visibility" is ON, the hit box will be visible.



Also, pressing the key (F6 by default) set in the plugin parameter "Hitbox visualization switching key"

can automatically switch the visualization state of the hitbox.

This function is only valid during test play.

※ If the hitbox is visualized in the switch settings, it can be visualized even if it is not a test play.





### [Combo attack function]

By setting the plug-in parameter "action combo setting", it is possible to easily create a combo attack.

With this setting, if the skill specified by the "derived source skill ID" is executed within the

"minimum combo possible time" to "maximum combo possible time", the skill will be changed to the

skill specified by the "derived skill ID". It is possible to execute after overwriting.

Also, if there is a combo destination setting, the attack prohibition time set by noAttackFrame

will be ignored and the minimum combo possible time will be used to determine whether an attack is possible or not.



※ This function was added from ARPG_Core v1.4.0.





### [Other]

Setting up states to be resolved over time

In ARPGs, there may be many situations where you want to resolve states over time.

We have prepared a function for this purpose.

By populating the following in the state Note field, the state can be resolved at the specified number of frames elapsed.

The state can be resolved when the specified number of frames have elapsed.

`<duration: number of frames>`



For example, to resolve the state after 10 seconds, set as follows (1 second = 60 frames)

`<duration: 60>`



This setting alone will not update the number of frames remaining when states are stacked.

If you want to update the number of remaining frames by stacking states, you need to include the following information in the Note field.

`<overWriteDuration: number of frames>`



#### ■ Skill settings for each weapon

It is possible to switch skills during a normal attack depending on the type of weapon.

The specified skill is executed by making the following entry in the Note field of the weapon.

`<skill: skill name>`



Note

When dual wielding is set, only the setting of the first equipped weapon will be reflected.



#### ■ Firing a transparent object

You can fire a transparent object to check whether the enemy is in front of you or not.

For example, it can be used to check if there is an enemy in front of you.

The collision target of the transparent object is the same as an event whose priority is set to Same as characters.



Note

If there is already a character at the position where the transparent object is created, the transparent object will pass through the character and collide with the character.

the transparent object will pass through the character.



#### ■ Target Selection Function

The "Target Selection" plug-in command allows the player or enemy to be selected by the cursor in the game.

This makes it possible, for example, to fire bullets at a selected enemy character.



If the weight is turned on, time can be stopped while the selection is being made, and if it is turned off, the selection can be made in real time.



When "Cancelable" is turned on, the target selection can be canceled when the cancel button is pressed during the target selection.

In this case, the result stored in the selection result storage switch is turned OFF.



#### ■ CheckInTheScreen event

By executing the "CheckInTheScreen" plug-in parameter

The plugin parameter "CheckInTheScreen" can be used to determine if the specified character is on the screen.



#### ■ Attribute judgment when receiving damage

By executing the plug-in command "Damage attribute check" in the common event that is executed when you

receive damage, you can determine which attribute you received damage from.

Note: Normal attacks cannot be judged as attributes.



#### ■ Increase attribute when attacking

Normally, only one attribute can be given to a skill, but it is possible to increase the attribute by writing

the following in the memo field. This setting can be used multiple times in one memo field.

`<damageElement: Element name>`



Example: When adding attributes of fire and ice

`<damageElement: fire>`

`<damageElement: ice>`



#### ■ Character weight

By executing the "Character Action Weight" plug-in command, you can stop a character's

events for a certain period of time. can be stopped for a certain period of time.

The difference between this command and the "wait" event command is that the wait, when executed from a parallel move,

stops the character's autonomous movement, but the character action wait stops the autonomous movement as well.

However, the difference is that the character action weight stops the autonomous movement as well.

Therefore, this command can be used when weights are needed for rigidity in the event of damage.



#### ■ How to check if the character has moved

Character movement can be checked by using the plug-in command

The character's movement can be checked by using the plugin command "Check if character is moved".

When this command is executed, if the character has moved at least once before being updated in the next frame,

the specified switch will be turned on, The specified switch will be turned ON.

The flag indicating whether or not the character has moved within the frame will be cleared when the

target character is updated in the next frame. The flag indicating whether the character has moved

within the frame is cleared when the target character is updated in the next frame.



### [Appendix]

When you specify a character for plugin parameters/plugin commands, you can input a variable value;



#### ■ Chracter type variable value

Player: 1

Follower: 2

Event: 3

Vehicle: 4



#### ■ Follower index variable value

First: 1

Second: 2

Etc.



#### ■ Vehicle variable value

Boat: 1

Ship: 2

Airship: 3