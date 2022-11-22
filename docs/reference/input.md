# Input Module
Allows to check for buttons during the game.

## press
Check if a key has been pressed. You can use `input.key()` to get key values for special keys, such as `DEL` for the delete button, or `SPACE` for the space button. You can use freely a one-letter long string to check for a letter key directly in this function too.

**Syntax:**
```lua
input.press(String or Integer key);
```

**Returns:**
```lua
boolean
```

**Example:**
```lua
function onUpdate()
	if (input.press("Z")) then
		console.log("You pressed the letter Z!");
	end
	if (input.press(input.key("SPACE"))) then
		console.log("You pressed the spacebar");
	end
end
```
This will show you a message if you press the Z key, or the spacebar.

## down
Check if a key has being held. For everything else works exactly the same than `input.press();`

**Syntax:**
```lua
input.down(String or Integer key);
```

**Returns:**
```lua
boolean
```

**Example:**
```lua
moving = 0;
key_left = input.key("LEFT");
key_right = input.key("RIGHT");

function onUpdate()
	if (not game.inplay()) then return end
	if (input.down(key_left) or input.down(key_right)) then
		moving = moving + 1;
	end
end
```
This will count every frame you were moving

## release
Check if a key has being released. For everything else works exactly the same than `input.press();`

**Syntax:**
```lua
input.release(String or Integer key);
```

**Returns:**
```lua
boolean
```

**Example:**
```txt
No example defined
```

## key
Returns the numerical ID of a key. The first argument should be a letter or a string that refers to a key. 

**Syntax:**
```lua
input.key(String key);
```

**Returns:**
```lua
integer
```

**Example:**
```txt
No example defined
```