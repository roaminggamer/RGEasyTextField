RGEasyTextField
============

RGEasyTextField is a library for creating native.newTextField() objects compatible with Windows.  This is a Corona SDK library.

Warning!!
-------------------------
If running in Windows version of simulator, be sure to simulate an Android device to get keyboard input.


Basic Usage
-------------------------

##### Require The Code
```lua
local RGEasyTextField = require( "RGEasyTextField" )
```
##### Create a text field
```lua
local group = display.newGroup()

local function myListener( self, event )
	print( event.phase, event.target.text )
	return true
end

local myField = RGEasyTextField.create( group, display.contentCenterX, 100, 
	display.actualContentWidth-20, 30,
	{ 
		placeholder = "<name>", 
		fill = {1,1,1}, selStroke = { 1, 0 , 1 }, selStrokeWidth = 4,
		fontColor = {1, 0, 1}, fontSize = 10,
		listener = myListener 
	} )
```

##### Get text
```lua
print( myField.text ) 
```

##### Set text
```lua
myField:setText( "Bob" )
```

##### Set Next and Prev Fields
The windows version supports tab, shift + tab, enter, and shift + enter advancement and return to next/prior fields like traditional windows apps.

To enable this set the next and prev fields.
```lua
nameField:setNextField( passwordField )
passwordField:setNextField( emailField )
emailField:setNextField( nameField )

nameField:setPrevField( emailField )
passwordField:setPrevField( nameField )
emailField:setPrevField( passwordField )
```


##### Syntax
```lua
RGEasyTextField.create( parentGroup, x, y, width, height, params )
```
 * parentGroup - Group to insert field into.  Passing 'nil' implies currentStage.
 * x,y - <x,y> center to place field at.
 * width, height - Width and Height of text field.
 * params - Table containing named settings parameters.


Named (Settings) Parameters
-------------------------
 * debugEn - If true, print debug ouptut.
 * placeholder - Text to display when field is empty.
 * fill (LIGHTGREY) - Table containing color code for field background.
 * setStroke (GREEN) - Table containing color code for field selection stroke.
 * selStrokeWidth (2) - Width of selection (indicator) stroke.
 * listener - Text input listener.  Must use 'table listener' variety ONLY.  (See example above.)
 * isSecure - Fill with asterisks after typing.  This is a 'secure' field.
 * text - Initial text.
 * fake - Read-only field indicating this is a faked field.  (Do not write to this value or you will break the field functionality.)
