# NBPresents - Version 1.3.21.15
Premium Mod for Forge 1.12.2, very easy to use server gift hunt creation with graphical interface and very advanced customization, compatible with Sponge permissions.

*Last Edit Time 31/03/2021*

## General
**NBPresents** allows you to create **collections** of presents, a collection is made with minecraft decorative heads, which you can customize as you wish. Once created, your collection is displayed in a menu for your players to see how many presents they need to complete the collection. You can set display names, icons, commands to be executed after a player completes the collection and permissions. Each present in a collection can be collected by players with the required permission, and each present can also be renamed in the configuration. 

## Configuration
This category explains how to set up and use NBPresents. Please note that you need to have the "Gooeylibs" mod to guarantee security for the inventory menu. If you don't already have it, it will be provided to you.

### Permissions
Users must have OP permission for single player instances, for servers under Forges/Sponge, users will need the ``nbpresents.admin`` permission to configure the mod. No additional permissions are required for configuration.

### Licencing
Regarding the license, all players have access to the command ``/nbplicence`` which displays the information about the current license.

#### Buy a single license / network license
For purchases please go directly to my discord, where the prices are posted. To join, simply go here: https://discord.gg/w3S9ZQf8nR
Please note that single licenses will only work for a single server. For network licenses, the IP addresses of the authorized servers on the network must be sent to the developer to be linked to your license. 

#### Activate my license
*This process is the same for single licenses as for network licenses.*
The information used here is fictituous and will not work, it is used as an example.
For our example we will use this information:<br>
**Server/Network Name**: ``MyAmazingServer``<br>
**Server/Network Key**: ``AmazServQXCegs1X16``<br>

Then use these commands in order <br>
``/nbplicence ServerName MyAmazingServer``<br>
``/nbplicence ServerKey AmazServQXCegs1X16``<br>
``/nbplicence Connect``<br>

A success message should then be displayed. If not, check your information and contact the developer if the license is still not activated. <br>
Once this is complete, use the command "**/nbplicence Ip**" and send the address to the developer to complete the process.

### Commands information
The plugin offers to execute commands as rewards. <br>
There are two types of commands, the ones starting with **"/"** which will be executed by the player, and the commands starting with "**!**" which will be executed by the server.<br>
**For example** <br>
``/presentkey`` will simulate sending the plugin license check command by the player.<br>
``!give {PLAYER} minecraft:stone 1`` will ask the server to give the player one stone.<br>

### Configuration files
The configuration files work in JSON format. In case of error, please read the generated report, the problem is probably due to a wrong format. For more information do not hesitate to consult https://developer.mozilla.org/fr/docs/Learn/JavaScript/Objects/JSON or other sites to understand the format. Do not hesitate to open a ticket on the discord server if you can't fix the problem alone.

#### General.json
This is the default content of the file.<br>
```
{
	"ServerName": "",                   // Your license name will be saved here, please do not edit this line manually.
	"LicenceKey": "",                   // Your license key will be saved here, please do not edit this line manually.
	"ServerId": 0,                      // This is the license server ID, please do not edit it alone, this is a backup option to act quickly in case of server downtime.
	"SecondsAutoBackupInterval": 300,   // The time in seconds between each automatic save of the players' progress.
	"DisplayDeveloperHead": true,	    // Shows or hides the developer's head in the present menu.
	"IgnoreWarning": false,		    // Ignore all warning.
	"ViewFullError": false		    // Display complete error if an error occured during opening config file.
}
```

#### String.json
This is the default content of the file. All texts and formats used and visible by the player are listed here, as well as aliases are available and listed here. 
**Warning: The aliases are specific to each feature, these are all used correctly here, if you add aliases not recognized, they will not be replaced as desired.**<br>
```json
{
	"Message": {
		"PICKED_UP_ALREADY": "&eYou've already picked up this present.",
		"PICKED_UP_SUCCESS": "&2You have just collected the present &6{ID_NAME} &2from the collection &6{NAME}!",
		"PICKED_UP_ERROR": "&cAn error has occurred, you cannot collect this present at this time.",
		"PICKED_UP_REMAINING": "&bYou still need to collect &e{AMOUNT} &bpresent to complete the &e{NAME} &bcollection!",
		"PICKED_UP_NO_PERMISSION": "&eYou do not have permission to collect gifts for the &a{NAME}&e collection!",
		"PRESENT_INVALID_COLLECTION": "&4The present collection is invalid!",
		"PRESENT_INVALID_PRESENT": "&4This present is invalid!",
		"PRESENT_INVALID_LOCATION": "Invalid Location!",
		"PRESENT_CANT_DELETE": "&cThe present could not be deleted.",
		"PRESENT_DELETED": "&bThe present has just been deleted.",
		"PRESENT_CANT_ADD": "&cThe present could not be added.",
		"PRESENT_ADDED": "&aThe present has just been added.",
		"PRESENT_CLAIMED": "&aYou ",
		"PRESENT_ALREADY_EXIST": "&aThe present has just been added.",
		"COLLECTION_FINISHED": "&6&lCongratulations: &6You have just completed the '{NAME}'&6 collection!",
		"CONFIG_ERROR": "&4Problem with the configuration!",
		"CONFIG_LOADED": "&aThe configuration has just been loaded",
		"CONFIG_SAVED": "&aThe configuration has just been saved",
		"ITEM_DESCRIPTION_REMAINING": "&aYou found &6{COUNT}&a/&6{TARGET} &aof the gifts in the collection!",
		"ITEM_DESCRIPTION_COMPLETED": "&2You have completed the collection!",
		"INVENTORY_NAME": "&2&lNBPresents - NicolasBrg",
		"INVENTORY_COLLECTION_NAME": "&6&lCollection &f{NAME}"
	}
}
```

#### PresentCollection.json
This is an example of the Collection used in the default configuration. Please note that for the coordinates, if the values are all set to **"-1"**, it is considered undefined. Therefore you will have to manually delete the initial presents, present only to show the available formats.<br><br>
**Once you understand how it works you can delete these collections from the in-game commands, avoid doing it from the configuration.**
<br>
```
{
	"Present_Collection": {
		"Christmas": {                                                  // Here is the ID Name of your collection (You can't have the same name twice)
			"DisplayName": "&f&lChrist&4&lm&ca&4&ls",                     // Here is the display name, showed in the player present UI
			"Permission": "",                                             // Here is the requiered permission, leave blank to allow everyone to use it.
			"Icon": "CruXXx",                                             // Here is the PlayerOwner Skull who is showed in player present UI to represent this collection, for this case 'CruXXx' is a skull representing a red present. You can use every player name you want to show his head. 
			"PresentList": [                                                  
				{
					"DisplayName": "First",                                   // Here is the display name of this specific present, he will be showed when player collect it, or in your debug menu.
					"Location": {                                             // Here is the present location, if X / Y / Z are defined to "-1" the location will be undefined
						"world": "world",
						"X": -1,
						"Y": -1,
						"Z": -1
					},
					"SpecialCommand": "/say First present for Christmas!"     // Here is a command that will be used when a player has found the current present 
				},
				{
					"DisplayName": "",
					"Location": {
						"world": "world",
						"X": -1,
						"Y": -1,
						"Z": -1
					},
					"SpecialCommand": [		// Here is a list of commands that will be used when a player has found the current present 
						"!say First command",
						"!say Other command"
					]
				}
			],
			"CommandAfterFullCompletion": [                               // Here it's a list of commands that will be executed once the collection is finished by a player.
				"!say GG {PLAYER}",
				"!give {PLAYER} minecraft:poke_ball 1"
			]
		},
		"Easter": {
			"DisplayName": "&aE&ba&cs&dt&ee&fr",
			"Permission": "",
			"Icon": "{display:{Name:\"Easter Egg with Chick\"},SkullOwner:{Id:\"179e8543-16ca-45f0-bebd-d068496b87a2\",Properties:{textures:[{Value:\"eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYjNmYWY4ZDk4NjJjNjgyNzZjZjAyMzFhODE3OWQ2OWE1YTk0NGVlYjJhZjQ1NDM2MGE1N2RlYTc1OGRiYTBmYSJ9fX0=\"}]}}}",                                             // Instead of just the head of a known player, you can load another texture, a tutorial is proposed below.
			"CommandAfterFullCompletion": [
				"!say The say command has been executed because {PLAYER} has completed a collection",
				"/presentkey"
			],
			"PresentList": [
				{
					"DisplayName": "",
					"Location": {
						"world": "world",
						"X": -1,
						"Y": -1,
						"Z": -1
					},
					"SpecialCommand": "!say General Test"
				}
			]
		}
	}
}
```

<br>**Customized head**<br>
To find the name of an already known head you can simply go here: https://minecraft-heads.com/player-heads browse the list and retrieve the player's name.
<br>
For more advanced textures, go here: https://minecraft-heads.com/custom-heads, choose a head, copy the command corresponding to the version, here 1.12.2 and retrieve only the information between the brackets. Then escape the quotes and simply paste the line obtained in the Icon section.

For example, if you have the head available here: https://minecraft-heads.com/custom-heads/decoration/43283-easter-egg-with-chick

**1. I select my version, 1.12.2 then, I found the command:**<br>
```/give @p skull 1 3 {display:{Name:"Easter Egg with Chick"},SkullOwner:{Id:"573f5b35-e9ea-4ed1-aa9e-6fc027d75952",Properties:{textures:[{Value:"eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNDAwMTRjZTA3NGVhNmU3MTkyODdlNzRhNzk2MTVkNTkyOWZjNmZmNDJhYzgxYTdlMWU0NWEwMDVmNzY0MjE3OSJ9fX0="}]}}}```<br>
<br>
**2. I'm only keeping the contents of the brackets, then:**<br>
```{display:{Name:"Easter Egg with Chick"},SkullOwner:{Id:"573f5b35-e9ea-4ed1-aa9e-6fc027d75952",Properties:{textures:[{Value:"eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNDAwMTRjZTA3NGVhNmU3MTkyODdlNzRhNzk2MTVkNTkyOWZjNmZmNDJhYzgxYTdlMWU0NWEwMDVmNzY0MjE3OSJ9fX0="}]}}}```
<br><br>
**3. Then I escape the quotation marks:**<br>
```{display:{Name:\"Easter Egg with Chick\"},SkullOwner:{Id:\"573f5b35-e9ea-4ed1-aa9e-6fc027d75952\",Properties:{textures:[{Value:\"eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNDAwMTRjZTA3NGVhNmU3MTkyODdlNzRhNzk2MTVkNTkyOWZjNmZmNDJhYzgxYTdlMWU0NWEwMDVmNzY0MjE3OSJ9fX0=\"}]}}}```
<br><br>
**4. You can now complete icon section.**<br>

#### PlayerData.json
PlayerData is the file that contains the progress of players, I advise you not to edit it, its operation is very similar to "**PresentCollection.json**, if you need additional information do not hesitate to contact me. Here is the default content associated with the default collection.<br>
```json
{
	"Present_Collection": {
		"Christmas": {
			"PresentList": [
				{
					"PlayerFound": [
						
					]
				},
				{
					"PlayerFound": [
						
					]
				}
			],
			"PlayerCompleted": [
				
			]
		},
		"Easter": {
			"PresentList": [
				{
					"PlayerFound": [
						
					]
				}
			],
			"PlayerCompleted": [
				
			]
		}
	}
}
```

### Commands
Here is a list of commands proposed by NBPresents (excluding aliases)

#### Admin

##### nbp <config / collection / json>

###### nbp config <load / load_presentcollection / refresh_string / save / save_playerprogress / save_presentcollection / print>
```nbp config load```: Command to load all configurations. Please note that player progress can be lost if it hasn't been saved recently, so make sure that player data has been saved recently. You have a command made especially for loading collections.  <br>
```nbp config load_presentcollection```: Command to load the present collection configuration file. <br>
```nbp config refresh_string```: Command to refresh all string of the plugin. <br>
```nbp config save```: Command to save all configurations <br>
```nbp config save_playerprogress```: Command to save the player progress configuration file. <br>
```nbp config save_presentcollection```: Command to save the present collection configuration file. <br>
```nbp config print```: Command that displays all the collections currently loaded. <br>

###### nbp collection <Create / Edit / Finish / Info / Permission / Remove / Rename / Print> 
Auto-completion is available for all commands. <br>
```nbp collection Create <Name>```:  Create a new collection named "Name". <br>
```nbp collection Edit <Name>```: Edit the "Name" collection. All presents placed will be linked to this collection.<br>
```nbp collection Finish```: Closes the edit mode and saves the collection.. <br>
```nbp collection Info```: Shows you the name of the collection you are currently editing. <br>
```nbp collection Permission <Name> {NewPermission}```: Update the permission to use the "Name" collection with {NewPermission}. <br>
```nbp collection Remove <Name> {Token}```: Delete the collection "Name", a security token will be generated, you will have to confirm the command with this token to validate the deletion. <br>
```nbp collection Rename <Name> {DisplayName}```: Update the DisplayName of "Name" collection with {DisplayName}. <br>
```nbp collection Print <Name>```: Displays the "Name" collection with all the presents with their coordinates in your private chat. <br>

###### nbp json
```nbp json```: Command that displays in console, all json data from the memory. <br>

##### nbplicence <Connect / Ip / ServerKey / ServerName / Status / Info>
```nbplicence ServerName <Name>```: Defines {Name} as the name of your server associated with your license.<br>
```nbplicence ServerKey <Name>```: Defines {Name} as the key of your server associated with your license.<br>
```nbplicence Connect```: Try to authenticate the server to the license server. <br>
```nbplicence Ip```: Sends you the ip to send to the developper to link it to your license. <br>
```nbplicence Status```: Displays in console the RawData of the last server response concerning your licence. <br>
```nbplicence Info```: Displays the status of the license. <br>

##### collection
```/collection``` takes no argument and displays an UI with more than 30 preloaded head. <br> 
Warning: A little lag can be felt at the first run due to the time needed to download the collection. <br>
![PresentDefaultCollection](https://user-images.githubusercontent.com/30299182/112839436-7f4e4300-909e-11eb-892f-c6c1389ddfa3.png)

#### Player
Commands available for players, no permissions required.

##### presents
```/presents``` takes no argument and displays the gift collection display interface.

##### nbplicence
```/nbplicence``` takes no argument and displays the licence status.

##### nicolasbrg
```/nicolasbrg``` takes no argument. This command is disabled if you have already purchased another of my products. It simply displays my contact information.

### Setting up a collection
We want to create a collection named "TestCollection". <br>
```/nbp collection create TestCollection``` Create the collection. <br>
```/collection``` Open example head menu, we choose all the head we want. <br><br>
Place presents in the world. <br>
```/nbp collection finish``` Save the current collection. <br>
```/nbp collection permission TestCollection nbpresents.mysuperpermissionname``` Set the current collection permission to "nbpresents.mysuperpermissionname". <br>
```/nbp collection rename TestCollection &6A&emaz&aing``` The current collection is now renamed ! <br>[Amazing](https://user-images.githubusercontent.com/30299182/112840953-37c8b680-90a0-11eb-91f0-ee3c6e995d17.png) <br>
```/nbp config save``` We save a last time our collections. <br>

Finally, with the ``/presents`` the players see. <br>
![Present](https://user-images.githubusercontent.com/30299182/112841422-bf162a00-90a0-11eb-8460-3ccccd5230a9.jpg)

### Other bonus features
When the developer logs in, a message is displayed in game, when the player clicks on it, a message to say hello is sent.
