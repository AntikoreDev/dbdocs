# Good Practices in Modding
There are a plenty of stuff you can do to improve your code's performance and readability.

## Resource Management
You may need to add sprites, sounds, objects, etc. It's recommened to do all of these resource loading during the `onLoad` function. It's almost mandatory to save ID's received from these functions for later use, for this you can make tables for sprites, sounds, objects, and everything.

After the mod has been disabled, you should free this memory up, by using `resources.free();` on the `onUnload` function.
```lua
sprites = {}
sounds = {}
objects = {}

function onLoad()
	sprites = {
		superblock = resources.load("superblock.png");
	};

	objects = {
		superblock = resources.add("superblock", sprites.superblock, "Super Block", "Awesome Items", "This block is so super that even superman can't withstand its presence");
	};

	sound = {
		supersound = resources.load("supersound.ogg");
	};
end

function onUnload()
	resources.free();
end
```