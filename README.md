# Documentation

Exec UI Library

## Loading the Library

```lua
local Library = loadstring(game:HttpGet('https://raw.githubusercontent.com/Player788/Exec-UI-Library/main/src.lua'))()
```

### Creating a Window

```lua
local Window = Library:Window{
	Name = <title : string>, 
	Creator = <name : string>,
	Script = <name : string>,
	Hotkey = {
		Key = <keycode : EnumItem>, 
		Enabled = <boolean>
	}
	Saves = {
		FileId = <name : string>,
		Enabled = <boolean>
	}
	Sounds = <boolean>
}
```

***

### Creating a Tab

```lua
local Tab = Window:AddTab{
	Name = <text : string>,
	TextColor3 = <Color3>,
}
```

***

### Creating a Left Section

```lua
local LeftSection = Tab:LeftSection(<name : string>)
```

### Creating a Right Section

```lua
local RightSection = Tab:RightSection(<name : string>)
```

***

### Creating a Notification

```lua
Library:Notification{
	Title = <header : string>,
	Content = <description : string>,
	Time = <duration : number>
}
```

***

### Creating a Button

```lua
LeftSection:AddButton{
	Name = <string>,
	TextColor = <Color3>,
	Callback = <function>,
}
```

* You need to state your element as a variable to get its methods, Example `local Button = Section:AddButton{}`
* You can also chain element methods, Example `LeftSection:AddButton{}:AddButton{}`

#### Methods

```lua
Button:Set(<string>)
Button:Destroy()
```

***

### Creating a Toggle

```lua
LeftSection:AddToggle{
	Name = <string>,
	TextColor = <Color3>,
	Default = <boolean>,
	Callback = <function> <returns : boolean>
}
```

#### Methods

```lua
Toggle:Set(<boolean>)
Toggle:Destroy()
```

***

### Creating a Slider

```lua
LeftSection:AddSlider{
	Name = <string>,
	TextColor = <Color3>,
	Default = <number>,
	Min = <number>,
	Max = <number>,
	Increment = <number>,
	Callback = <function> <returns : number>
}
```

#### Methods

```lua
Slider:Set(<number>)
Slider:Destroy()
```

***

### Creating a Textbox

```lua
LeftSection:AddTextBox{
	Name = <string>,
	TextColor = <Color3>,
	PressEnter = <boolean>,
	ClearOnFocus <boolean>,
	Default = <string>,
	Placeholder = <string>,
	Callback = <function> <returns : string>
}

```

#### Methods

```lua
Input:Set(<string>)
Input:Destroy()
```

***

### Creating a Keybind

```lua
LeftSection:AddBind{
	Name = <string>,
	TextColor = <Color3>,
	Default = <Keycode : EnumItem>
	Hold = <boolean>,
	Callback = <function> <returns : <string> <holding : boolean>
}
```

#### Methods

```lua
Bind:Set(KeyCode : EnumItem)
Bind:Destroy()
```

***

### Creating a Dropdown

<pre class="language-lua"><code class="lang-lua">LeftSection:AddDropDown{
<strong>	Name = &#x3C;string>,
</strong>	Default = &#x3C;any>,
	Options = &#x3C;table>,
	Callback = function(Value)
		print(Value)
	end
}
</code></pre>

#### Methods

```lua
Dropdown:Refresh(<list : table>, <clear : boolean>)
Dropdown:Remove(<index>)
Dropdown:Set(<index>)
```

### Creating a Colorpicker

```lua
LeftSection:AddColor{
	Name = <string>,
	TextColor = <Color3>,
	Callback = <function> <returns : <color3>
}
```

#### Methods

```lua
Colorpicker:Set(<Color3>)
```

## Miscellaneous

### Saves (Filesystem)

* Flags are used as global variables to store (Values, Tables, etc.) Toggles, Sliders, Dropdowns & binds. Adding a flag value will automatically save its configs. Example:

```lua
LeftSection:AddToggle({
    Name = "Toggle",
    Default = true,
    Flag = "toggle"
})
```

#### Methods

```lua
Library:Get(<Flag : string>) <returns value>
Library:Save()
Library:Load() -- Always add at last or in a button
```

***

### Library Methods

```lua
Library:Destroy()
Library:UpdateTheme()
```

### Library Config

```lua
Library.Keys <table : dict>
Library.Theme <table : dict>
Library.Logs <table : array>
Library.Config <table : dict>
```
