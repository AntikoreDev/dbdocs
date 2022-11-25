# Dansebox's Console
At certain point in your mods you may need to log messages to debug more easily. You can log by using the [Console Module](../reference/console.md).

The console generally contains most logs the game does, stuff that generally goes to `latest.log` file will appear here during play as well.

To look at the console in-game, just press `F3` at any time.

## Console Commands
Not only that, Dansebox also includes a few commands you can run during play to ease modding process.

### lua
Runs a lua snippet of code. Note that every mod instance is separated from each other, and this will run outside any of these, so you can't access directly to variables from them.

**Syntax:**
```bash
lua <code snippet...>
```

### playsfx
Plays an audio asset from their ID. This include music as well.

**Syntax:**
```bash
playsfx <id>
```

### reload
Unloads and loads every mod or an specified mod. Take in account this command breaks everything so easily, and for so, using it on playing, replays, and level editor is disabled.

**Syntax:**
```bash
reload [modname]
```

### clear
Clear the whole log, this doesn't affect the `latest.log` file

**Syntax:**
```bash
clear
```

### luastate
Outputs a lua state id by the namespace

**Syntax:**
```bash
luastate <namespace>
```

### luaadd
Runs lua code over a luastate

**Syntax:**
```bash
luaadd <namespace> <code...>
```

### macro
Runs a macro by ID. A mod can check when a macro is run, so you can create your own macros. See [`onMacro`](./events.md#onMacro) for further information

**Syntax:**
```bash
macro <name>
```