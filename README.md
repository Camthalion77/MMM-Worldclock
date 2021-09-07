# Module: MMM-Worldclock
This module is derived from default MagicMirror module 'clock' and modified. Thanks to michaelteeuw.<br>
This module displays times from around the world. <br>
Modified fork of worldclock by eouia, renamed and improved.<br>

*** Due to the end of life for required modules, this module may break in future versions of MagicMirror. I am working on a solution. *** 

![](https://github.com/bkeyport/MMM-Worldclock/blob/master/world-clock.png?raw=true)

## Installation

1\. Execute the following commands to install the module:

```bash
cd ~/MagicMirror/modules # navigate to module folder
git clone https://github.com/BKeyport/MMM-Worldclock # clone this repository
```

2\. Then, add the following into the `modules` section of your `config/config.js` file:

````javascript
{
	module: 'MMM-Worldclock',
	position: 'top_left', // This can be any of the regions, best in top_left or top_right regions
	config: {
	// See 'Configuration options' for more information.
		timeFormat: 'hh:mm A', //Global time format, as defined in moment.js format()
		style: 'top', // Which way do you want the flag and description from the clock? choices are 'top', 'left','right','bottom'
		offsetTimezone: null, // Timezone you want to show the difference from. null, "", or omitted from config will be UTC.
		clocks: [
			{
				title: "Home",
			},
			{
				title: "HOLLYWOOD", // Too long of a title could cause bad text align.
				timezone: "America/Los_Angeles", //When omitted, Local time will be displayed. 
				flag: "us", // If you'd like a flag from the standard library 
			},
			{
				timezone: "Asia/Seoul",
			},
			{
				title: "UTC",
				timezone: "UTC",
				timeFormat: "HH:mm MM/DD", // Time format override. 
				altflag: "world.png" // if you'd like a flag from a file on your mirror device. 
			},
		]
	},
},
````
3\. Change the options to your desired method. 

## Configuration options

The following properties can be configured:

| Option            | Description
| ----------------- | -----------
| `timeFormat`      | How to format the time of worldclocks <br><br> **Possible example values:** any formatter available in moment.js (eg. `HH:mm A`, `hmmss`) <br> **Default value:** `LT` (It could be displayed like '12:34 AM')
| `style`           | How to display with defined style. <br><br>**Possible values:** `top`, `bottom`, `left`, `right` <br> If you select top, the time will be displayed over the timezone title or UTC gap comment.<br>You can customize this style by modifying CSS with style selector (style-top, style-bottom, style-left, style-right). See the clock_style.css <br> **Default value:** `top`
| `offsetTimezone` | `null` or `Europe/Berlin`<br/> If you set `null`, timegap from UTC will be shown. <br> If you set `TIMEZONE` like `Europe/Berlin`, it will show timegap from that timezone.  
| `clocks`          | Array of clocks



### clocks configuration options:
| Option            | Description
| ----------------- | -----------
| `title`           | The clock title of each timezone. if it is omitted or null, the `timezone` value will be displayed instead. <br><br> **Example:** `My Home`, `The Golden Gate`, `Hong Kong Office` or `null`  
| `timezone`        | Specify a timezone to show current local time. <br><br> **Possible examples values:** `America/New_York`, `Europe/Berlin`, `Etc/GMT+10` <br>See more informations about configuration value [here](https://momentjs.com/timezone/docs/#/data-formats/packed-format/)<br> **Default value:** `null`<br> If this value is null or omitted, current local timezone value (defined in config.js) will be used. I don't recommend it because the purpose of this module is showing another local time.<br>All available timzone codes are [here](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
|`flag `  |  [ISO 3166-1-alpha-2 code](https://www.iso.org/obp/ui/#search/code/) for country. DO NOT use with altflag below |
|`altflag `  |  name of alternative flag file. MUST Be square image, MUST be self centered. DO NOT use with flag above. Place in module's root directory. |
|`timeFormat`|Override module  timeFormat configuration for this clock. For possible values see timeFormat above.|

If you happen to use `flag` and `altflag` together you'll get both on the same clock, This is clearly not desired. <br> 

Altflag images should have no whitespace around the edge for most advantagous look. It will be slightly smaller than the flag image. I'm not sure why this is, yet.<br>

## Style Customizing
Look and feel of the module is handled by CSS.<br>

Please make all changes in MagicMirror/css/custom.css (If you haven't made any changes to CSS, it may not exist) 

Each clock is in it's own class. The class is defined as 'world-' with the sequence number, starting at zero. 

First clock is 'world-0' ("home") in default code<br>
Second is 'world-1' ("Hollywood") in default code<br>
and so on. <br>

Modifying the overall style is accomplished by adjusting the classname 'style-' and the value of your style config. 

'style-top' 'style-bottom' 'style-left' and 'style-right' respectively. 

## Updates
* 2021-06-07
	* Update schema.json for various bug fixes and MMM-Config, Update README. 

* 2021-06-06
	* Adjusted defaults to match documentation. 
	* Adjusted defaults for MMM-Config use. ** Note: double check your fields carefully, some may revert to default, working on bugfix **
	* Continue rewrite of documentation for clarity. 
	* Altflag now is _about_ the same size as regular flags. 

* 2021-01-18 
	* Added initial altflag operation. Will allow user to add a flag of their choice. Is not working fully yet, I need to learn and build my own css tree for it to make it seamless with other flag system. As of present, icons are slightly larger than wanted, and may interrupt other operation. Suggestions welcome. 
* 2020-08-06 
	* Fixed timeFormat per clock to work properly. 

Updates after 2020-08-01 is BKeyport

* 2019-02-24
	* eouia: `offsetTimezone` is added.
* 2017-08-25
	* eouia: supports `MMM-TelegramBot` (https://github.com/eouia/MMM-TelegramBot)
	* eouia:  command `/worldclock` is added
* 2017-08-10
	* eouia: Country flags are supported.
	* eouia: HTML/CSS Structures are refined.

Thank YOU for your support.

@eouia/@bkeyport
