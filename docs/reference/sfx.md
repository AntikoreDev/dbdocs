# SFX Module
This module handles audio playing.

## play
You can play sounds through this method. You can use custom sounds by passing the output of `resource.load();` of a sound file to the SoundID.

**Syntax:**
```lua
sfx.play(SoundID sound, Number volume = 1, Number pitch = 1, Boolean loops = false, Integer priority = 10, Number offset = 0);
```

**Returns:**
```lua
nil
```

**Example:**
```lua
function onPlayerCollide(instance)
	sfx.play(sound.shout);
end
```
This will play a shouting sound when colliding with other object.