# Dansebox Modding API Documentation
This is an official documentation for [Dansebox](https://antikore.itch.io/dansebox)'s modding API created using [MkDocs](https://www.mkdocs.org/). This website is hosted through GitHub pages and you can check it at https://antikoredev.github.io/dbdocs/

## Example mod
This is a very basic example mod you can use to try out the api.
```lua
--[[
A simple mod that restarts a level if the player gets hit!
--]]

function onLoad()
	console.log("One-hit Mod Enabled");
end

function onUnload()
	console.log("One-hit Mod Disabled");
end

function onUpdate()
	if (not game.islevel()) then return end
	if (game.hit()) then game.restart(); end
end
```

## Featured Mods
A list of mods already made that should be featured.

*No mods added yet*

## Contribute
You can contribute Dansebox by donating through [Ko-fi](https://ko-fi.com/antikore) ☕✨
You can contribute to this documentation by modifying and improving the markdown files for the pages.
