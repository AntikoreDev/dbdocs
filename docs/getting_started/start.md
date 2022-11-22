# Creating your first mod project
To start modding Dansebox, you'll need a simple template. You can download a premade one or continue with the following step

## Creating file structure
If you don't have any template, you may create the file structure below, inside `mods` folder on your game's directory. 

```txt
<modname>/
	content/
	main.lua
	mod.conf
	mod.png
```
Make sure you don't put `<modname>` to the root folder.

- `content/` · This is where all sprites and sounds will be stored, keep it as organized as you want. 
- `mod.png` · This is a preview image for the mod, this is optional and you can ignore it.
- `mod.conf` · This is a file that set basic information about your mod. This is an important file we'll explain below
- `main.lua` · This is where the real shit goes on, Dansebox will run this **lua** file in order to run your mod.

## Creating the mod.conf file
This file holds information about your mod, such as mod name, mod description, version, author, etc.
You should create this file for the mod to work. It interprets as an `.ini` file.

The bare minimum you have to include to this file is something like this.
```ini
[Mod]
name="My cool mod"
description="This mod does all the things!"
version="1.0"
author="Me!"
namespace="mycoolmod"
```
You may want to change the name, and description to fit your needs. The most important thing that YOU MUST change is the namespace, which is the identifier for your mod, this should be unique and not repeated. For sake of simplicty, you should try to use the same namespace for the root folder name

## Basic main.lua syntax
This is where the fun part goes, you start your mod by starting your game. (If it doesn't, check if it's enabled through settings menu)
When the mod starts, it runs automatically the [`onLoad`](./functions.md) function inside your mod 

Here's a good example to start from
```lua
function onLoad()
	console.log("Mod enabled");
end

function onUnload()
	console.log("Mod disabled");
	resources.free();
end
```
When the mod is enabled, it will display in the console `Mod enabled`. When it disables, it will display `Mod disabled` and then free any resources added (If you don't import any sprites, sounds or objects, you shouldn't need any `reesources.free();` function).