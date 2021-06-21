# SimMenuPlugin
SimHub plugin that adds an in-game menu to control SimHub, game and other options

## API

To add your own game options and settings options to the SimMenu, you can use the API provided to interface with the SimMenu plugin.
 
- Add a reference to the SimMenu plugin (SimMenu.Plugin.dll located in SimHub root folder)
- Import the SimMenu plugin
```C#
using SimMenu.Plugin;
```
- Fetch SimMenu plugin and bind events (typically done in "Init" method)
```C#
SimMenuPlugin simMenu = pluginManager.GetPlugin<SimMenuPlugin>();
simMenu.Initialised += SimMenu_Initialised;
```
- Add your plugin's options to the settings menu
```C#
private void SimMenu_Initialised()
{
	simMenu.AddSettingsOption(new SettingsOption
	{
		Title = "YOUR PLUGIN NAME",
		Description = "Configure the 'YOUR PLUGIN NAME' plugin settings",
		SubOptions = new ObservableCollection<SettingsOption>
		{
			new SettingsOption
			{ 
				Title = "Setting 1", 
				Description = "Description of Setting 1", 
				IncrementAction="YOUR PLUGIN NAME.Setting1Increment", 
				DecrementAction="YOUR PLUGIN NAME.Setting1Decrement", 
				ValueProperty="YOUR PLUGIN NAME.Setting1" }
			}
		});
}
```
