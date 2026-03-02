# Action Combat Manual

For Version 1.6.2+

# RPG Maker Action Combat

通过notetag、注释、条件分歧和插件命令，来实现想要的功能和效果



## 📝Notetags

### ❤️ 事件的HP系统

`<hp: value>`

为事件设置一个HP值

```
value：可以是一个数字，最大值或最小值，数据库中的敌人名称，角色和角色名称
```
> `<hp: Ghost>` -  这个事件获取数据库中的名称为“Ghost”的敌人的数值、特性等设置

> `<hp: actor, 1>` - 同上，但是从1号角色获取

⚠️ 在1.5.5以上的版本，可以只用在事件名称输入数据库的敌人名称就能够设置HP值

#### 自定义HP条

`<hpy: x>` - 调整事件HP条的y偏移

`<hpColor: #00000>` - Change HP bar color for event调整事件HP条的颜色

`<hpScale: x>` - Scale the size of HP bar up. Default is 1.0缩放HP条的大小，默认为1

`<radius: x>` - 调整玩家接近时，事件HP条的弧度

`<hideHP>`  -为事件隐藏HP条

### ⚔️ 伤害系统

`<dmg: value>`

本事件向其他事件造成的伤害，它只会给事件设置固定伤害值。要使用公式计算伤害，需要使用插件命令**Increase/Decrease Character HP**

```
value：可以是数字，最小最大值，v[变量id]，数据库中的技能名称
```

> `<hp: Fireball>` - 用的fireball技能来处理伤害，使用其公式和特性

> `<hp: v[2]>` - 用id为2的变量值来处理伤害


#### 动作计时

`<cooldown: x>`

在经过x帧后，持续的伤害效果仍然有效。仅用于条件分歧：checkCollide(source, target, cooldown (write as is)")

> `<cooldown: 15>` ：碰撞检测事件将每 15 帧返回一次 true，而不是仅返回一次。

#### 碰撞箱设置

`<hitbox: width, height, offset x, offset y>`

本事件的碰撞箱。每个事件的默认碰撞箱为**1, 1, 0, 0**，其中宽度和高度单位为1个图块，偏移为像素

`<hitbox: 2, 2>` or `<hitbox: 3, 5, 15, 30>`


#### 公式设置攻击者

`<attacker: x>`

可选的标签，用于手动设置攻击者的技能公式，如果此处为空，插件就会自动检测攻击者。大部分情况下不会使用这个

```
X: 角色id，数据库的敌人名称
```

> `<attacker: actor 2>` - 假如技能公式为a.atk - b.def，a.atk为2号角色的攻击

```

### 🎨 视觉自定义

#### 色调效果

`<hue: -180 to 180>`

事件的色调，最小-180，最大180，可以在Aseprite中预览色调

#### 位置调整

`<sprite offset: x, y>`

事件精灵的偏移。仅影响精灵！

### 🎯 移动和交互

`<ignore>`

Only usable for movement route **moveToClosest**, which to not move to events with this notetag

<pass>

Player can step on any event with this notetag regardless of where they're being placed

<platform: size>

Transform the event into a platform. Characters stepping on platform will move along with it. Size is in pixel unit. If size isn't assigned (you only write <platform>) then size will be 48 pixel by default.

💬

## Comments

### 🔄 Event Behavior

#### Passive Events

 

<passive: x, y, z, etc>

The common event ids/names that this event will call in parallel. It's like calling a common event in a parallel event but on another layer that isn't being affected by any commands inside that event.

<passive: 1, 2, 3, 4, 5> or <passive: Player Attack, Player Defend>

#### Animation Control

 

<stepping speed: x>

Adjust the walking animation speed of the event. The lower the number, the faster the animation plays.

<stepping speed: 8>

#### Event Sliding

 

<no sliding>

Stop the event from moving instead of sliding, when it moves toward an obstacle or screen boundary.

### 🏗️ Collision System

#### Collision Area

 

<collisionRect: width, height, offset X, offset Y>

Expand your event collision area (not hitbox). All in tile unit (still support decimal). Offset doesn't move the rect but move your player/event location. Rect when expand will expand with anchor top-left, which also is where the player/event is standing

<collisionRect: 3, 3, 0, 0> Expand by 3 tiles horizontally and vertically
<collisionRect: 3, 3, 1, 1> Same but also make event sprite to be at the center

#### Hitbox Collision Control

 

<skip collision>

The event will be ignored from conditional branch **checkCollide** on any page with this comment

### 👨‍👧‍👦 Parent-Child System

#### Child Events

 

<child of: x>

Make the event to be a child of another event/player. Child events are just regular events with attributes to move along with the player.

X:player, event id, event name, <event notetag>

#### Child Positioning

 

<child offset: x, y>

Adjust position of the child from the parent

<child offset: 50, 0> - Will move along with its parent but with offset x = 50

### 🖱️ Mouse Interaction

#### Clickable Events

 

<clickable: range>

Event with this comment can be activated via mouse click and only when the player is within range

<clickable> - Display outline and can be triggered if player is within 1 tiles
<clickable: 3> - Display outline and can be triggered if player is within 3 tiles

🔀

## Conditional Branch

### ❤️ HP Monitoring

HP(eventId/'player')

Check the current HP of an event or player

**HP(1) > 0** or **HP(this._eventId) <= 0** or **HP('player') > 0**

hpDecreased(eventId)

Check if the event just got its HP decreased

hpDecreased(this._eventId)

gotHit(eventId)

Check if the event just got collided by another event (result of condition checkCollide)

gotHit(this._eventId)

### 💥 Collision Checking

checkCollide(source, target, cooldown?)

Check collision between source and target ONCE (unless cooldown is assigned). The hitbox size/position is determined by notetag <hitbox: width, height, offset x, offset y> from both source of target (still work even if you don't assign that).

Source:event Id, 'player', this._eventId

Target:'player', 'event name', '<event notetag>', ['<event notetag>', '<event notetag 2>', 'event name'], 'impassable X', 'region X'

Cooldown: Can be a number or 'cooldown'
The checkCollide only return true once when collision just happened, but if a cooldown is assigned, it'll return true multiple time, and the cooldown is the wait frame before another collision to happen again

'cooldown' - If your event has notetag <cooldown: 5>, it means cooldown = 5

'impassable X' - X can be A3 A4 B C D E, the tileset. Example: impassable A3 A4 B C

'region X' - X is a region Id

**checkCollide(this._eventId, 'Bullet')** - Return true if this event collided an event named Bullet

**checkCollide('player', 'Bullet')** - Return true if player collided an event named Bullet

**checkCollide('player', 'Bullet', 60)** - Return true if player collided an event named Bullet and will return true again after 60 frames have passed

**checkCollide('player', 'impassable B C D E')** - Return true if player collided an impassable tile belong to tileset BCDE

**checkCollide('player', ['Bullet', 'Sword')** - Return true if player collided an event named Bullet or Sword

### 📡 Range Checking

checkRange(source, range, target, eye view?, block region ID, '<exception notetag>')

Check range from source to target, like a detection system. By default, it's a circle detection.

Source: event Id, this._eventId, 'player'

Target:'player', '<event notetag>', 'region X'

Range: A number in tile unit

Eye View: A degree number. If assigned, convert circle detection to cone detection (like flashlight view) and make the size of cone to be this degree number. 360 degree = full circle

Block Region ID: If detection is eye view mode and Block Region ID is assigned, the cone will be blocked by this region id. Meaning the source event won't be able to detect target if target is taking cover behind this region id

Exception Notetag:If assigned, target has this notetag will make this condition to return false regardless

**checkRange(this._eventId, 7, 'player')** - Return true if this event is within 7 tiles from player

**checkRange('player', 7, '<enemy>')** - Return true if player is within 7 tiles from an event with notetag <enemy>

**checkRange(this._eventId, 7, '<enemy>', 90, 1)** - Return true if this event is within 7 tiles + eye view of 90 degree from an event with notetag <enemy>. Return false if <enemy> is covered by region id 1

#### Sound Detection

 

checkSound(source, max volume, range)

Check if there's any sound playing from other events around source event within x range.

**checkSound(this._eventId, 50, 6)** - Any sound above 50 volume playing from other events within 6 tiles

### 📊 Local Variables

localVariable(eventId, var name)

Check local variable of an event

Var Name:If assigned, check local variable with this name. Otherwise, use default local variable name. This is similar to naming your variable to a custom name. If you don't name it then it'd still work. It'd be like localVariable(eventId, 'default')

**localVariable(this._eventId) >= 5** - Return true if local var 'default' of this event is >= 5

**localVariable(this._eventId, 'fire') >= 5** - Same but instead of 'default', it's 'fire'

#### Other Event Local Variables

Check local variable of another event that is nearby the source event

eventLocalVariable(source, var name, direction)

Source: event ID , 'player' , this._eventId

Direction: front , behind
The direction of the source that will use to look for nearby event. Either check for the front or the back. If not assigned, it'll check for the event underneath the source

**eventLocalVariable(this._eventId) >= 5** - Return true if local var of event underneath this event is >+ 5

**eventLocalVariable('player', 'fire', 'behind') == "haha"** - Return true if local var named 'fire' of event behind player is haha

#### Percentage Checks

 

localPercentage(eventId, percentage)

Check local percentage of an event. It's similar to when you set a variable from range 1 ~ 50 and the result will be given randomly from 1 - 50.

**localPercentage(this._eventId, 50)** - 50% chance this condition will return true

### ⚔️ Equipment & Inventory Checks

#### Weapon Checks

 

equippedWeapon(weapon id/'weapon name', slot)

Check if the player is equipping a weapon using its id or name. If slot isn't assigned then it'll check for the first weapon slot

**equippedWeapon('Long Sword')** - Check if player is equipping weapon Long Sword in slot 1

**equippedWeapon(1, 2)** - Check if player is equipping weapon id 1 in slot 2

#### Weapon Type Checks

 

equippedWeaponType(weapon id/'weapon name', slot)

Return true if player is equipping a weapon with a certain type

#### Weapon Notetag Checks

 

equippedWeaponNotetag('<notetag>', slot)

Return the value from the notetag box of equipped weapon

**equippedWeaponNotetag('capacity') >= 7** - Return true if notetag box of equipped weapon in slot 1 contains notetag <capacity: number> and number is >= 7

**equippedWeaponNotetag('element', 2) == 'fire'** - Return true if notetag box of equipped weapon in slot 2 has notetag <element: fire>

#### Armor Checks

 

equippedArmor(armor id or 'armor name')

Return true if player is equipping an armor

#### Skill Checks

 

learnedSkill(actor Id/'actor name', skill iD/'skill name')

Return true if an actor has learned a certain skill

**learnedSkill('player', 'Fireball')** - Return true if player has learned Fireball
**learnedSkill('David', 'Blizzard')** - Return true if actor named "David" has learned Blizzard

#### Inventory Quantity Checks

 

amount('type', id or 'name')

Return the amount of item/weapon/armor that the player possesses.

**amount('item', 1) > 7** - Return true if player has more than 7 of item id 1
**amount('armor', 'Heavy Armor') == 1** - Return true if player has 1 'Heavy Armor' in inventory
**amount('weapon', 5) >= 4** - Return true if player has 5 weapon id 5 in inventory

### 🎮 Gamepad & Control Checks

checkGamepad()

Return true if a gamepad is connected

isRightStickPushed()

Return true if right stick of gamepad is being pushed

isLeftStickDegree(value)

Return true if left stick is being pushed to this degree (0 - 360)

Input.isTriggered('key')

Return true if key is pressed and released once (Requires Hendrix Keyboard Gamepad plugin)

**Input.isTriggered('n')** - Return true if button N just pressed
**Input.isTriggered('leftclick')** - Return true if just Left Clicked
**Input.isTriggered('rightclick')** - Return true if just Right Clicked

Input.isPressed('key')

Return true if key is being pressed and hold (Requires Hendrix Keyboard Gamepad plugin)

### 🎯 Direction & Target Lock Checks

checkDirection(target, number)

Number: A number from trackpad
Number: 4 -> left, 6 -> right. Support 8 directions

**checkDirection(this._eventId, 8)** or **checkDirection('player', 9)**

#### Target Locking

 

isLockingATarget(source)

See if the source is target locking something. Support 'player' , this._eventId or an event Id 

isBeingTargetLocked(target)

See if the target is being locked by something. Support 'player' , this._eventId or an event Id 

### 🦸🏻 Game States Checks

checkLevelUp()

Return true when party leader has just leveled up

partyLeader(actor id or 'actor name')

Return true if party leader is id x or has a certain name

### 🔧 Advanced Conditions

#### Performance & Optimization

 

inViewport(eventId, extra buffer)

A useful conditional that is mostly used for performance optimization. It'll return true if events are on screen and will return false if it's offscreen.

**inViewport(this._eventId)** - Check with extra 5 pixels offscreen
**inViewport(this._eventId, 48)** - Check with extra 48 pixels offscreen

#### Impassable In Front Check

 

inFrontIsImpassable(target)

Return true if in front of target is an impassable tile or impassable events. Target supports an event id or 'player' 

#### Notetag & Name Checks

 

notetag(eventId, '<notetag>') or notetag('<notetag>')

A versatile conditional branch that will either check if an event has a certain notetag or an event with a certain notetag exists on map.

**notetag('<enemy>')** - True if there's an event with notetag <enemy> on map

**notetag(this._eventId, '<enemy>')** - True if the current event has notetag <enemy>

**notetag('<crop>', this._eventId)** - True if an event with notetag <crop> is at the same position of current event

checkName(eventId)

Check if eventId's name is something

checkName(this._eventId) == "Santa"

checkNameOnMap(name)

Check if there's an event with this name on current map

checkNameOnMap('Santa')

### 🕺 Platform & Jumping

#### Platform Checks

 

onPlatform(target)

Return true if target is standing on a platform event (event with notetag <platform>). Target supports an event Id or 'player'

#### Jumping Checks

 

checkJump(target, 'state')

Return true if target is either started jumping, is jumping or landed

Target: event Id , 'player'

Number: startedJump , jumping , landed

⚠️

This check is for plugin command "Jumping"

📜

## Script Call

### ⚔️ Weapon Functions

#### Weapon Damage

 

equippedWeaponDmg(slot)

Return the attack value of the weapon party leader is equipping in a certain slot

**equippedWeaponDmg()** or **equippedWeaponDmg(2)**

#### Weapon Parameters

 

equippedWeaponParam(param, slot)

Return a value from a param of the weapon party leader is equipping in a certain slot

**equippedWeaponParam('atk')** - Get Attack value of equipped weapon from slot 1

**equippedWeaponParam('def', 2)** - Get Defense value of equipped weapon from slot 2

#### Gun System *(check database notes section)* 

$gameSystem.gunAmmo(slot)

Return the current ammo loaded to equipped weapon from a certain slot

$gameSystem.gunCapacity(slot)

Return the capacity of equipped weapon from a certain slot

$gameSystem.gunAmmoInInventory(slot)

Return the amount of ammo item in inventory that belong to a weapon equipped from a certain slot

To use in Conditional Branches, you can write them in short:
gunAmmo(slot) gunCapacity(slot) gunAmmoInInventory(slot)

### 💥 Collision Damage

$gameMap.event(CollisionManager.lastSourceEventId).getDamageFromNoteTag()

Return the damage from notetag <dmg: x-y> of the event just collided

⚠️

Best to use with Control Variable. You'll almost never use this function, so ignore it

### 🦸🏻 Characters & Sprites

⚠️

The benefit of using these functions via a Script Call is they won't be affected by player movement, which is an issue of command **Movement Route**. But, unless you're making a complex mechanic, most of the time you won't use these.

#### Change Sprites

 

**$gameMap.event(eventId).setImage('filename', character index)** or **$gamePlayer.setImage('filename', character index)**

**$gameMap.event(this._eventId).setImage('$haha', 0)**
Change this event image to $haha.png. This is a single file so character index should always be 0

**$gameMap.event(3).setImage('group', 1)**
Change this event image to group.png and select index 1

#### Play Frames

 

**$gameMap.event(eventId).playFrames(first frame, last frame, speed)** or **$gamePlayer.playFrames(first frame, last frame, speed)**

Make event or player play frames from their spritesheet. Requires Hendrix Animation Solution plugin

**$gamePlayer.playFrames(1, 6, 3)
**Make player play from frame 1 to 6 by the speed of "wait 3" (just like Wait command) each frame

#### Set Frames

 

**$gameMap.event(eventId).toFrame(frame index)** or **$gamePlayer.toFrame(frame index)**

Make event or player set to a frame from their spritesheet. Requires Hendrix Animation Solution plugin

**$gameMap.event(this._eventId).toFrame(3)**
Change current event image to frame 3 of its spritesheet

### 🔧 Utility Functions

#### Vortex Effects

 

sucking(source, 'notetag', range, speedboost)

Suck events to the source. Source supports event id or 'player' 

**sucking****(this._eventId, '<enemy>', 8)** - Suck all events with notetag <enemy> within 8 tiles to current event

**sucking(this._eventId, '<enemy>', 8, 7)** - Suck all events with notetag <enemy> within 8 tiles to current event whilst increasing the walking speed of those events to 7

#### Variable Access

 

localVar(event id, 'var name')

Return the value of the local variable of an event.

**localVar(this._eventId)** or **localVar(this._eventId, 'fire')**

#### Direction Info

 

getDirection(target)

Get target's current direction. Target supports event id or 'player' 

#### Count Event on Map

 

mapCount(target)

Return the amount of event currently on map. Target supports event name or <notetag>  

**mapCount("ball")** or **mapCount('<ball>')**

🏃

## Movement Route

Call these script in a Set Movement Route command

### 🚶 Basic Movement

#### Self Switch Control

 

selfSwitch(letter, true/false)

Same as Control Self Switch but you can call this in Movement Route.

selfSwitch('A', true) or selfSwitch('B', false)

#### Movement

 

dash(distance)

Move the player to the direction he's moving. Why use this instead of Move Forward? Because this supports 360 degrees and in pixel so it's compatible with Joystick.

dash(3)

setMoveSpeed(number)

By default, RPG Maker only supports max speed of 6. With this, you can break that limit.

setMoveSpeed(8)

### 🎯 Target Lock

lockTarget(target, range (10), autoSwitch (true), faceWhenIdle (true), runFreely (true), targetImage, indicatorPosition ('above'), indicatorAnimation ('pulse')

Make the character lock to a target. He/she will always look at this target. You'll find this feature common in action games

**lockTarget('player')** - Make the character locks to player

**lockTarget('<enemy>')** - Make the character locks to a nearby event with notetag <enemy> within 10 tiles. Will auto switch to nearest target

**lockTarget('<enemy>', 7, false)** - Make the character locks to a nearby event with notetag <enemy> within 7 tiles and will only lock to that event, ignoring nearer options

You can add more param to have more cases:

faceWhenIdle (true/false) - Character looks at locked target when not moving

runFreely (true/false) - Character looks at locked target when running/dashing (if character is player)

targetImage ('filename') - Display this image (indicator) on locked target (filename in picture folder without .png)

indicatorPosition ('above'/'middle'/'foot') - Position of indicator image on the locked target

indicatorAnimation ('pulse'/'static'/'updown') - Animation of indicator image

### 🧭 Directional Movement

#### Turn Toward Target

 

turnToward(target, force direction, max distance)

Turn the character direction to the target.

Target: event Id , '<event notetag>' , 'player' , 'mouse or gamepad' , 'playerLockedTarget' , 'eventLockedTarget' 

Force Direction: true/false
If assigned, lock or unlock the character to the current direction, similar to Directional Fix ON

Max Distance: a number
If assigned, character will only turn toward the target within this range (tile unit)

mouse or gamepad - Turn torward mouse/joystick position
playerLockedTarget - Turn character to the target that player is locking
eventLockedTarget - Turn character to the target that current event is locking

**turnToward('<enemy>')** - Turn toward a nearby event with notetag <enemy>

**turnToward('<enemy>', false, 7)** - Same as above, but won't turn to events that are out of reach by 7 tiles

**turnToward('mouse or gamepad', true)** - Turn to mouse/joystick direction and turn on Directional Fix

#### 360-Degree Rotation 

rotateTo(destination, search range)

Rotate the character (support 360 degrees) to a destinatino. Best for projectiles.

Destination: map cordination , event id , '<event notetag>' , 'mouse or gamepad' , 'player moving direction' , 'playerLockedTarget' , 'eventLockedTarget' 

Search range: a number
If assigned, limit the search for destination up to this range (tile unit)

map cordination - Written as x, y. Rotate character to this cordinate
mouse or gamepad - Rotate character to the position of mouse/joystick
player moving direction - Rotate character to the same direction player is moving
playerLockedTarget - Rotate character to the target that player is locking
eventLockedTarget - Rotate character to the target that current event is locking

**rotateTo(15, 30)** - Rotate the character to map coordination x15 y30

**rotateTo('<enemy>')** - Rotate the character to nearby event with notetag <enemy>

**rotateTo('<enemy>', 7)** - Rotate the character to any event with notetag <enemy> within 7 tiles distance

#### Direction Sharing

 

shareDirection(target)

Make the character to have the same direction as the target

Target:event id , '<event notetag>' , 'player' , 'playerLockedTarget' , 'eventLockedTarget'

playerLockedTarget - Share the same direction of the target that player is locking
eventLockedTarget - Share the same direction of the target that current event is locking

### 🦘 Jump & Teleport

#### Random Jumping

 

jumpToNearby(max distance, jump on another event)

Jump the character to nearby positions from its current position. I use it for loots dropping from monsters or from a chest.

**jumpToNearby(3)** - Jump to nearby tiles within 3 tiles distance, not on events
**jumpToNearby(3, true)** - Same but will jump on other events if they're in the way

#### Targeted Jumping

 

jumpTo(destination, range limit/jump by x tiles)

A versatile command that will jump the character to a target. In some cases, the param will act differently, please read examples carefully to further understand the feature.

Destination: map cordination , event id , 'player' , 'forward' , 'backward' , 'away' , 'cursor' , 'right stick' , '<enemy notetag>' , 'playerLockedTarget' , 'eventLockedTarget'

 Range Limit/Jump by X Tiles: a number
If assigned, jump up to this range or jump this many range, depending on what you used from X, Y (tile unit)

forward - Jump forward from character's direction
backward - Jump backward from character's direction
away - Jump away from player
cursor - Jump to mouse location
right stick - Jump to gamepad's right stick degree
playerLockedTarget - Jump to the target that player is locking
eventLockedTarget - Jump to the target that current character is locking

**jumpTo(15, 30)** - Jump the character to map coordination x15, y30

**jumpTo('player')** - Jump the character to game player

**jumpTo('player', 5)** - Jump the character to game player but limit up to 5 tiles

**jumpTo('away', 3)** - Jump the character away from the game player by 3 tiles

**jumpTo('right stick', 3)** - Jump to to right stick degree by 3 tiles

#### Teleportation

 

teleportTo(destination, min distance, max distance/exception)

A versatile command that will teleport the character to a target. In some cases, the param will act differently, please read examples carefully to further understand the feature.

Destination: map cordination, 'player', '<event notetag>', 'forward', 'playerLockedTarget', 'eventLockedTarget'

Min distance: a number
If assigned, teleport to destination with minimum distance by X range (tile unit). This param becomes 

Max search range/Exception: a number
If assigned, teleport to destination but only if this destination is within X range (tile unit). This param becomes ***Exception*** when used with forward 

forward - Teleport character forward
playerLockedTarget - Teleport character to the target that player is locking
eventLockedTarget - Teleport character to the target that this character is locking

**teleportTo('player')** - Teleport the character to the player position

**teleportTo('<enemy>')** - Teleport to nearby event with notetag <enemy>

**teleportTo('<enemy>', 3)** - Teleport to nearby event with notetag <enemy> outside minimum distance of 3 tiles

**teleportTo('<enemy>', 3, 7)** - Teleport to a random location around a nearby event with notetag <enemy>, between 3 and 7 tiles away from that event

**teleportTo('forward', 5)** - Teleport forward by 5 tiles. Won't teleport to impassable tiles

**teleportTo('forward', 5, 'A3 A4 B')** - Teleport forward by 5 tiles. Will teleport anywhere passable except impassable tiles from tileset A3, A4 and B.

### 👟 Advanced Movement

#### Pixel Movement (Requires DotMoveSystem)

 

moveToPosition(destination, y/rotate along path?)

A versatile command that will move the character to a target in pixel. In some cases, the params will act differently, please read examples carefully to further understand the feature.

Destination:map cordination, 'mouse or gamepad', 'forward', 'player', '<event notetag>', 'comment: x', 'playerLockedTarget', 'eventLockedTarget'

map cordination - Written in format x, y
mouse or gamepad - Move to mouse position or gamepad's joystick degree
comment: x - Move to an event with comment "x"(green text) in its active page
playerLockedTarget - Move to the target that player is locking
eventLockedTarget - Move to the target that current character is locking
forward - Move forward by 1 pixel. If y is assigned with **"tile"** then it'll move by 1 tile

**moveToPosition(15, 7)** - Move to this map cordination

**moveToPosition('mouse or gamepad')** - Move to cursor or right stick if gamepad is connected

**moveToPosition('forward')** - Move the character to wherever it's rotated to (support 360 degrees) by 1 pixel per call. Event needs to be rotated in order to use **forward.** Best for projectiles

**moveToPosition('forward', 'tile')** - Same but will move by 1 tile per call

**moveToPosition('player')** - Move the character to game player position by 1 pixel unit per call

**moveToPosition('player', 'player')** - Move the character to game player position till reached by one call

**moveToPosition('player - 0.5', 'player + 6')** - Move to game player position with additional x - 0.5 tile and y + 6 tiles

**moveToPosition('comment: crop')** - Move the character to an event that its page has comment "crop"

**moveToPosition('cursor', true)** - Move to mouse location and also rotate the character along the path. Best for projectiles

**moveToPosition('<enemy>')** - Move to nearby event with notetag <enemy>

#### Grid-Based Pathfinding

 

moveToClosest(destination, perfect pathfinding?, wait till finish?, exception)

Move the character to a target grid-based, support pathfinding.

Destination: 'player', '<event notetag>', 'playerLockedTarget', 'eventLockedTarget'

Perfect Pathfinding: true/false
Add path finding if true

Wait till finish: true/false
If true, one call of this movement route script will wait till character reached destination before processing the next command

Exception: moveToClosest('<enemy>', true)
Same as case 2 but with perfect pathfinding, automatically avoids obstacles. Best for ground characters.

playerLockedTarget - Move to the target that player is locking
eventLockedTarget - Move to the target that current event is locking

**moveToClosest('<enemy>')** - Move to event with notetag <enemy>

**moveToClosest('<enemy>', true)** - Move to event with notetag <enemy> with path finding

**moveToClosest('<enemy>', true, true)** - Same, but will wait till character reached <enemy> before processing the next command

**moveToClosest('<enemy>', true, true, '<friendly>')** - Same, but if the event <enemy> also has notetag <friendly> then character won't move toward it

### 🦸🏻 Character Sprites

Make your character play animation with a spritesheet, unlimited frame. A very important feature to upper the quality of your game as characters animations are the soul of every game.

⚠️

These commands require Hendrix Animation Solution plugin

playFrames(first frame, last frame, speed)

Make character play its spritesheet from first frame to last frame with a certain speed

playFrames(1, 6, 3) - Play current spritesheet from frame 1 to 6, with the speed of 3 (like Wait 3 frames)

toFrame(frame index)

Make character set its current frame to a another frame from its spritesheet

toFrame(3) - Switch current frame to frame 3

📅

## Database Notes

### ⚔️ Weapons

#### Setup a Gun

<capacity: x> - Make this gun max capacity is X

<starting ammo: x> - Make this gun when picked up to have X ammo

<ammo item: x> - Make this gun requires ammo item X to shoot. X can be item Id or item name

⚠️

X supports expression

### ☠️ States

#### Inflict a State

 

<state common event: x, y, z...>

Call this common event on the event that got hit. Can be multiple common events. Can use either common event name or their Ids

🔌

## Plugin Commands

### 🌟 Event Spawning & Management

#### Spawn Event

Spawn an Event from the Template Map to the Current Map.

Event Id/Name: The ID or name of the event you want to spawn. It must match the ID or name of the event from the template map. Support expressions

X, Y Position: The location you want to spawn the event. If you put just one word then it'll be used for both X and Y

this/player - Spawn on position of current event/player

region X - Spawn on all region X tiles

cursor - Spawn at mouse cursor position

random(a:b) - Generate random number, a is min, b is max

<notetag> near: this/player/eventId - Spawn at nearest event with notetag to a target

Initial Rotation Degree: When spawned, this event will be rotating to this degree

a number - Point to this degree (0-360)

mouse or gamepad - Rotate to mouse or gamepad if available

mouse or gamepad + 60 - Rotate to mouse/gamepad plus 60 degrees to the right

<notetag> - Point to an event with said notetag

this / player - Rotate to this event/player

Not Spawn On: Disallow event to be spawned on this destination

impassable A3 B C - Not spawn on impassable tiles belong to A3 B C

impassable events - Not spawn on events that block movement

Spawn in front: Spawn in front of the target if true. Only usable if X Y Position is this or player

Grid-Based: Spawn in grid-based instead of pixel-based

Permanent Event: Save this event across game maps (make it act like a regular event)

⚠️

Spawn in pixel requires Dot Move System plugin

#### Destroy Event

Destroy the events you spawned from Template Map or a regular RPG Maker event

Event Target: The target to destroy

this - Destroy current event

event Id - Destroy event on map with this id

event name - Destroy any events with this name

<notetag> - Destroy any events with this notetag

Destroy Nearby Events: If assigned, destroy events that is near **Event Target** instead

event name - Destroy any events with this name near Event Target

<notetag> - Destroy any events with this notetag near Event Target

Destroy Permanently: If false, after destroying the event, if player returns to the map, the event will re-spawn. If true, the event destroyed from the game permanently.

#### Create Dynamic Event

Create an event that contains some properties that will only last an amount of time before it destroys itself. Best used to create hitboxes.

When your character swings a sword, create a hitbox at the sword.

Notetag: The notetags this event will have

Comment: The comments this event will have

Destroy after: If assigned, destroy this event after X frame

X, Y Position: This supports all cases similar to **Spawn Event** command

Rotation Degree: When spawned, this event will be rotating to this degree. Support expressions

a number - Point to this degree (0-360)

mouse or gamepad - Rotate to mouse or gamepad if available

this/player - Rotate to match this event/player

mouse or gamepad + 60 - Rotate to mouse/gamepad plus 60 degrees to the right

Attach To: Make this dynamic event attach to a target

<notetag> - Attach to an event with this notetag

this/player - Attach to the current event or player

#### Destroy Dynamic Event

Destroy all events created dynamically

Notetag to match: Destroy all events with a certain notetag

<notetag> - Destroy all events with this notetag

<notetag> near: this/player/eventId - Destroy a dynamic event with this notetag that is near either this event/player/or an eventId

### ❤️ HP & Health Management

#### Increase / Decrease Character HP

Update HP characters. Will automatically detect whether it's an event enemy or an actor event

Target: The target to update HP

player

this - current event

all - any events with hp

event id - an event with this id

HP Change:+ or - an amount of HP. Support expressions

a number
damage - Use value from notetag <dmg: x> of event that just collided with Target event
player weapon - Use player's ATK + equipped weapon's ATK
player 2nd weapon - Use player's ATK + equipped weapon in shield slot's ATK

Exceed Max Health: Allow HP to exceed the initial maximum HP when gaining HP

#### HP Bar Visibility

Show/hide HP bar of an event (just visually)

#### Remove Event HP Bar

Remove an event's hp bar completely

### 🎨 Visual Effects & Display

#### Pop Text Value

Display a text onto an event, can be used to show damage dealt

Event Id Support this for current event, event id, player 

Value: The number/text that will display onto the event

damage - Display value x from notetag <dmg: x> from event that just collided with Event Id
exp / gold - Display exp or gold from defeated enemy
player weapon - Display player's ATK + equipped weapon's ATK
player 2nd weapon - Display player's ATK + equipped weapon in shield slot's ATK
number , text , other expressions 

Animation Type: The animation for the text

Stick to map: Stick the text to map position, make it not moving along with camera

#### Break Character

Immediately break the event calling this command into pieces

#### Character Effects

Play certain sprites effect on character like spin, rotate, bounce, etc

#### Swing Weapon

Using a picture file as a weapon and swing it

#### Camera Update

Stop/Resume camera focusing on player

#### Freeze Time

Freeze all events and player for an amount of time

#### Pause Events

Pause all events (except the event calling this command) from moving or processing commands

### 🎮 Event Control & Behavior

#### Collision Status

When false, conditional branch checkCollide won't return true even if it collided with the event calling this command

#### Whatever you're doing, stop!

Immediately stop movement routes of the event calling this command

#### Child and Parent

Make an event to be a child of another event/player. The child will move along with its parent whilst still being able to do its own things

#### Change Event Hitbox

Change the hitbox of an event dynamically

#### Assign New Passive

Add or remove a common event from comment <passive: x, x, x> if it exists in the current event

#### Dynamic passable

Make an event to be passable (able to walk on it) even if it's an obstacle

#### knockback

Push a target away from another target

Who to knockback (target): this , player , event id , <event notetag> 

Knockback From: Target will be pushed away from this character. Support event id , player , <event notetag> 

#### add state

Inflict a state to a target

#### remove state

Remove a state from the target that has been inflicted by a state. Will remove state from event/player calling this command

### 🔄 Switches & Variables

#### Control Self Switch

Similar to RPG Maker default control self-switch but slightly more advanced. It can automatically find the right page to self-switch into. Support extra self switch set via naming Switches as "self switch [name]."

When your enemy dies, it'll self-switch into a page with comment <death>. You can leave that page A B C D whatever, it'll auto-find the right letter.

#### Control Local Variable

Create variables that belong to the event calling this command

#### Reset All Local Variables

Reset all local variables of events to 0

#### Quick Reset Switches & Variables

Reset all switches with a specific keyword in their name to false, Reset all variables with a specific keyword in their name to 0

Any switches and variables that have [reset] in their name will be reset to false and 0

### 🎮 Player Controls & Actions

#### Player Movement

Block player from moving

#### Change Player Hitbox

Change player hitbox dynamically

#### FAST WEAPON EQUIP

Immediately equip the next weapon available in inventory

#### JUMPING

Make a target jump!

#### Target Lock

Make player locks onto an event. Player will always look at this event. This is a common gameplay mechanic that you'll often see in action games

What do you want?: Enable, disable the locking feature or lock the next avaiable target

Look at Notetag: Lock to a nearby event with this notetag

Range: Only lock events inside this range (tile unit)

Auto Switch Target: Automatically switch to the most nearest target

Player Run Freely: When player dashing/running, player won't look at locked target

Indicator Image: Show this image on the locked target

#### Gun - armor & capacity control

Modify ammo/magazine capacity of equipped weapon that has note <capacity: x> and <ammo: item name>. A great command to create a ranged weapon like bow and gun

#### Gun - reload

Reload the weapon by decrease item name (<ammo: item name>)

⭐

## Additional Features

### 🔄 Extended Self Switches

self switch X

If an event with a page has a switch named **self switch X**, that switch becomes a self-switch of that page. This feature is to break the limitation of having only 4 self switches A B C D

💡

**Tip:** This allows you to have unlimited self switches beyond the default A, B, C, D limitation. Simply name any switch "self switch [name]" and it will function as a self switch for that event. To switch page to custom created self switch [name], use plugin command Control Self Switch and switch via a comment

```