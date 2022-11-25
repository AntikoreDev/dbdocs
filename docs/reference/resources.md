# Resources Module
Allows handling resources, that means, you can load sprites, sounds, create new objects etc, through this module.

## load
Loads sprites or sounds from a filename, the filename starts at content folder, so you can write `mysprite.png` and that would link to mysprite.png inside the content folder. Depending on the extension, Dansebox will get it as a sprite or as a sound.

**Syntax:**
```lua
resources.load(String fname);
```

**Returns:**
```lua
AssetID
```

**Example:**
```lua
sprites = {
	superblock = resources.load("superblock.png");
};
sounds = {
	gunfire = resources.load("shoot.ogg");
}
```
This code imports the shoot.ogg sound and the superblock.png sprite, and save them into tables for future reference.

## add
This adds a new object to use in levels for example.

**Syntax:**
```lua
resources.add(String objectIDWithNoNamespace, SpriteID sprite, SpriteID mask, String objectName, String objectCategory, Table properties = []);
```

**Returns:**
```lua
ObjectID
```

**Example:**
```lua
No example defined.
```

## free
This is used to free up memory from sprites, sounds, objects etc. This is recommended to use in the `onUnload` event.

**Syntax:**
```lua
resources.free();
```

**Returns:**
```lua
nil
```

**Example:**
```lua
function onUnload()
	resources.free();
end
```

## mask
This is used to customize mask (collision box) for a sprite.

**Syntax:**
```lua
resources.mask(SpriteID sprite, Number left = 0, Number top = 0, Number right = 15, Number bottom = 15);
```

**Returns:**
```lua
SpriteID
```

**Example:**
```lua
sprites = {
	coin = resources.mask(resources.load("coin.png"), 7, 7, 9, 9);
};
```
This adds a coin sprite with a very small mask