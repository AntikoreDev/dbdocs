# Instance Module
The instance module allows the interaction with game objects, both level editor and ingame ones.

## id
Returns the object id from an instance

**Syntax:**
```lua
instance.id(InstanceID inst);
```

**Returns:**
```lua
ObjectID
```

**Example:**
```lua
function onEditorObjectPlace(inst)
	if (instance.id(inst) == "coolitems:myitem") then
		console.log("Wow, thanks for using my mod!!!!");
	end
end
```
This will check if the object placed is a `coolitems:myitem`, and if it does, thank the player for that.

## namespace
Returns the namespace of an object

**Syntax:**
```lua
instance.namespace(InstanceID inst);
```

**Returns:**
```lua
String
```

**Example:**
```lua
function onEditorObjectPlace(inst)
	if (instance.namespace(inst) != "coolitems") then return end
	-- do stuff
end
```
This will exit the execution of the function if the object's namespace isn't `coolitems`

## x
Returns the x coordinate of an object.

**Syntax:**
```lua
instance.x(InstanceID inst);
```

**Returns:**
```lua
Number
```

**Example:**
```lua
function onEditorObjectPlace(inst)
	console.log(instance.x(inst) .. ", " .. instance.y(inst));
end
```
This will log the position of an object when placed in the editor.

## y
Returns the y coordinate of an object.

**Syntax:**
```lua
instance.y(InstanceID inst);
```

**Returns:**
```lua
Number
```

**Example:**
```lua
function onEditorObjectPlace(inst)
	console.log(instance.x(inst) .. ", " .. instance.y(inst));
end
```
This will log the position of an object when placed in the editor.

## destroy
This destroys an instance

**Syntax:**
```lua
instance.destroy(InstanceID inst);
```

**Returns:**
```lua
nil
```

**Example:**
```lua
function onEditorObjectPlace(inst)
	if (levelNotMine) then
		instance.destroy(inst);
		console.log("This level is not yours!!!!");
	end
end
```
This will disable the player to place blocks in the edtitor if level is not theirs.

## move
This moves an instance relatively

**Syntax:**
```lua
instance.destroy(InstanceID inst, Number x, Number y);
```

**Returns:**
```lua
nil
```

**Example:**
```lua
function onLevelObjectUpdate(inst)
	if (instance.id(inst) == "bullets:bullet") then
		instance.move(0, -8);
	end
end
```
This will move bullets during the level, upwards by 8 pixel per frame.