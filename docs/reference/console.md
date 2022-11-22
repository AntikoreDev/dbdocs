# Console Module
Allows the interaction with console and logs.

## log
Output text to the console

**Syntax:**
```lua
console.log(String text);
```

**Returns:**
```lua
nil
```

**Example:**
```lua
function onLoad()
	console.log("Enabled my incredible mod! Thanks :D");
end
```
This will show a log message when the mod is enabled :)

## error
Output text to the console as an error

**Syntax:**
```lua
console.error(String text);
```

**Returns:**
```lua
nil
```

**Example:**
```txt
No example defined.
```
This will show a log message when the mod is enabled :)

## trace
Output text to the console, and also to the latest.log file

**Syntax:**
```lua
console.trace(String text);
```

**Returns:**
```lua
nil
```

**Example:**
```lua
function onLoad()
	console.trace("Enabled my incredible mod! Thanks :D");
end
```
This will show and trace a log message when the mod is enabled :)
