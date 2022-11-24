# Events
This is a reference of every event that Dansebox runs on your mod's `main.lua` file.<br>
For sake of simplicity, take in account that Dansebox shouldn't run any event on your mod if its disabled<br>
Note that you don't have to include any of these events for your mod to work, instead, just add those you actually need.

## onLoad
This runs once the mod is enabled by the user, or when the game starts while the mod is enabled.

**Syntax:**
```lua
onLoad()
```

**Example:**
```lua
function onLoad()
	console.log("Enabled my incredible mod! Thanks :D");
end
```
This will show a log message when the mod is enabled :)

## onUnload
This runs once the mod is disabled by the user, or when the game ends while the mod is enabled.
**Syntax:**
```lua
onUnload()
```

**Example:**
```lua
function onLoad()
	resources.free();
end
```
This will free up resources added by the mod (This is a good practice actually!)

## onUpdate
This will run every frame, this is useful when you want to check for buttons to do different actions. Note that this runs anywhere you are, including splash screens, editor, main menus, first load, etc. so you may (or may not) want to check where you are before doing an action.

**Syntax:**
```lua
onUpdate()
```

**Example:**
```lua
function onUpdate()
	if (not game.islevel()) then return end
	if (game.hit()) then game.restart(); end
end
```
This will restart the level, when the player is hit, only if the player is in a level.

## onLevelObjectUpdate
This will run every frame for every object that is currently active in the level, while playing. This works both if you're on a replay or if you're in a level.
The first parameter is an instance id you can use to manipulate the instance through the [instance](../reference/instance.md) module

**Syntax:**
```lua
onLevelObjectUpdate(InstanceID instance)
```

**Example:**
```lua
function onLevelObjectUpdate(instance)
	if (instance.id(instance) == "mymod:superblock") then
		draw.sprite(sprite.superblock, instance.x(instance), instance.y(instance), instance.depth(instance));
	end
end
```
This draws the superblock sprite if the instance id is `mymod:superblock`

## onEditorObjectUpdate
This will run every frame for every object that is currently active in the level editor.
The first parameter is an instance id you can use to manipulate the instance through the [instance](../reference/instance.md) module

**Syntax:**
```lua
onEditorObjectUpdate(InstanceID instance)
```

**Example:**
```lua
function onEditorObjectUpdate(instance)
	if (instance.id(instance) == "mymod:superblock") then
		draw.sprite(sprite.superblock, instance.x(instance), instance.y(instance), instance.depth(instance));
	end
end
```
This draws the superblock sprite if the instance id is `mymod:superblock`

## onPlayerCollide
This will run every frame the player collides with something, for each instance colliding.
The first parameter is an instance id you can use to manipulate the instance through the [instance](../reference/instance.md) module

**Syntax:**
```lua
onPlayerCollide(InstanceID instance)
```

**Example:**
```lua
function onPlayerCollide(instance)
	if (instance.id(instance) == "gunfires:ammo") then
		instance.destroy(instance);
		ammo = ammo + 10;
	end
end
```
This will detect when the player collides with the object with id `gunfires:ammo`, if it does, it destroys it and adds 10 to the `ammo` variable.

## onLevelLoad
This will run when a level is loaded. Works both for replays and levels.

**Syntax:**
```lua
onLevelLoad()
```

**Example:**
```lua
function onLevelLoad()
	attempts = 0;
end
```
This will detect when the level is loaded, and set the variable `attempts` to 0

## onLevelPrepared
This will run once the level is loaded, and after the level is restarted. Works both level and replays as well

**Syntax:**
```lua
onLevelPrepared()
```

**Example:**
```lua
function onLevelPrepared()
	attempts = attempts + 1;
end
```
This will detect when the level is prepared, and add 1 to the vriable `attempts`

## onLevelStarted
This will run once the player has started the level, by pressing `left` or `right` (or any key that starts the level) the first time in a level after being loaded.

**Syntax:**
```lua
onLevelStarted()
```

**Example:**
```lua
function onLevelStarted()
	console.log("Level " .. level.name() .. " started! Here we go!");
end
```
This will send a debug message when you start a level, that includes the level name

## onLevelComplete
This will run once the player has completed a level.

**Syntax:**
```lua
onLevelComplete()
```

**Example:**
```lua
function onLevelComplete()
	draw.hudtext("Congratulations!", view.width() / 2, view.height() - 16, -1000, color.white, font.main);
end
```
This will congrat you by completing a level!

## onNetworkPacketReceive
This will run when a packet is received during a multiplayer play. (This may not be implemented when you're reading this, so this event is probably, inexistent)

**Syntax:**
```lua
onNetworkPacketReceive(Table packetData)
```

**Example:**
```txt
No example defined.
```

## onEditorLoad
This will run when the editor loads a level. Doesn't run if the editor is loaded plain empty. It gives you the filename of the level that has been loaded.

**Syntax:**
```lua
onEditorLoad(String filename)
```

**Example:**
```lua
function onEditorLoad(filename)
	local levelfile = level.fromfile(filename);
	local name = level.name(levelfile);
end
```
This will get the name of a level from it's file when it's loadaded.

## onEditorSave
This will run when the editor saves a level. It gives you the filename of the level that has been saved.

**Syntax:**
```lua
onEditorSave(String filename)
```

**Example:**
```txt
No example defined.
```
This will get the name of a level from it's file when it's loadaded.

## onEditorObjectPlace
This will run everytime an object is created in the level editor. The first parameter corresponds to the instance of the new object

**Syntax:**
```lua
onEditorObjectPlace(InstanceID instance)
```

**Example:**
```lua
function onEditorObjectPlace(instance)
	if (instance.id(instance) == "mymod:singleton") then
		if (instance.number("mymod:singleton") > 1) then
			instance.destroy(instance);
		end
	end
end
```
This will only let the player place 1 object of `mymod:singleton`

## onEditorObjectErase
This will run everytime an object is erased in the level editor. The first parameter corresponds to the instance of the destroyec object

**Syntax:**
```lua
onEditorObjectPlace(InstanceID instance)
```

**Example:**
```txt
No example defined.
```

## onMacro
This will run when the player tried to run a macro through the console. First parameter is the ID passed through the command.

**Syntax:**
```lua
onMacro(String name)
```

**Example:**
```lua
function onMacro(name)
	if (name == "mylives") then
		console.log("You have " + lives + " lives!");
	end
end
```
This outputs a message that tells the player how many lives they have, when the command `macro mylives` is used.